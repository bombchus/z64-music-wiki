---
icon: material/code-braces
---

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

# Custom Envelopes

=== ":material-code-braces: &nbsp;C"

    ```c
    EnvelopePoint gDefaultEnvelope[4] = {
        { 1, 32000 },
        { 1000, 32000 },
        { ADSR_HANG, 0 },
        { ADSR_DISABLE, 0 },
    };
    ```

=== ":material-xml: &nbsp;XML"

    ```xml
    <item name="gDefaultEnvelope">
      <struct name="ABEnvelope">
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="1"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="32000"/>
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="1000"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="32000"/>
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="-1"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="0"/>
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="0"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="0"/>
      </struct>
    </item>
    ```

Below is a graphical representation of the envelope of the Piano instrument, the ADSR values for Ocarina of Time and Majora's Mask are linear values with the time being in microseconds. A value of `1` for your envelope data is equal to ~`4000µs (0.004s)`.

In the example below we will assume the sample's waveform is `2s` in total length, so over `8000µs (0.008s)` the sample goes from zero amplitude to ~`99%` amplitude, then once it reaches ~`99%` amplitude it returns to zero amplitude over the course of `960000µs (0.96s)` and remains at zero amplitude for `4000µs (0.004s)` and then it will remain at zero amplitude indefinitely due to the value of `-1` being the special command `#!c ADSR_HANG`.

```c hl_lines="2"
#define ADSR_DISABLE 0
#define ADSR_HANG -1
#define ADSR_GOTO -2
#define ADSR_RESTART -3
```

=== ":material-code-braces: &nbsp;ADSR_DISABLE"

    ```c
    case ADSR_STATUS_DISBLED:
        return 0.0f;
    ```

=== ":material-code-braces: &nbsp;ADSR_HANG"

    ```c
    case ADSR_HANG:
        break;
    ```

=== ":material-code-braces: &nbsp;ADSR_GOTO"

    ```c
    case ADSR_GOTO:
        adsr->envelopeIndex = adsr->envelope[adsr->envelopeIndex].arg;
        goto retry;
    ```

=== ":material-code-braces: &nbsp;ADSR_RESTART"

    ```c
    case ADSR_RESTART:
        adsr->action.s.status = ADSR_STATUS_INITIAL;
        break;
    ```

-----
=== ":material-code-braces: &nbsp;C"

    ```c
    EnvelopePoint pianoEnv[4] = {
      { 2, 32700 },
      { 229, 0 },
      { 1, 0 },
      { -1, 0 },
    };
    ```

=== ":material-xml: &nbsp;XML"

    ```xml
    <item name="Piano Envelope">
      <struct name="ABEnvelope">
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="2"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="32000"/>
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="229"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="0"/>
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="1"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="0"/>
        <field name="Delay" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="-1"/>
        <field name="Argument" datatype="int16" ispointer="0"
               isarray="0" meaning="none" value="0"/>
      </struct>
    </item>
    ```

Ocarina of Time and Majora's Mask use 4-Point envelope structure, however 

![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-light.png#only-light)
![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-dark.png#only-dark)

=== "Attack"

    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-attack-light.png#only-light)
    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-attack-dark.png#only-dark)

    Attack refers to the time it takes from when a key is first pressed the sound of a sample to go from zero amplitude to the max attack amplitude. The longer your attack is the longer it will take for the sound to fade in to the max attack amplitude from zero amplitude.

=== "Decay"

    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-decay-light.png#only-light)
    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-decay-dark.png#only-dark)

    Decay refers to the time it takes the sound of a sample to go from the max attack amplitude to the sustain amplitude. The longer your decay is the longer it will take for the sound to decrease in amplitude from the max attack amplitude to the sustain amplitude.

=== "Sustain"

    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-sustain-light.png#only-light)
    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-sustain-dark.png#only-dark)

    Sustain refers to the amplitude level the sound of a sample will remain at so long as the note is being held. The higher your sustain is the less of a decrease your amplitude will have from the max attack amplitude.

=== "Release"

    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-release-light.png#only-light)
    ![](https://bombchus.github.io/z64-music-wiki/assets/images/adsr-release-dark.png#only-dark)

    Release refers to the time it takes from when a key is released to the sound of a sample going from sustain amplitude to return to zero amplitude. The longer your release is the longer it will take for the sound to fade out from your sustain amplitude to zero amplitude.

=== "Hold"
    Hold refers to the time a note will be held at max attack amplitude before beginning to decay to the sustain amplitude. The longer your hold is the longer your sound will remain at max attack amplitude before beginning to decay to sustain amplitude.

-----