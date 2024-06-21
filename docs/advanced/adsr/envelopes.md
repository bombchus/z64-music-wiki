---
hide:
#icon: material/code-braces
---

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

# Custom Envelopes

=== ":material-code-braces: &nbsp;C"

    ```c
    EnvelopePoint gDefaultEnvelope[] = {
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

Below is a graphical representation of the envelope of the Piano instrument, the ADSR values for Ocarina of Time and Majora's Mask are linear values with the time being in microseconds. A value of `1` for your envelope data is equal to ~4000 µs (0.004 s).

In the example below we will assume the sample's waveform is 2 s in total length, so over 8000 µs (0.008 s) the sample goes from zero amplitude to ~99% amplitude, then once it reaches ~99% amplitude it returns to zero amplitude over the course of 960000 µs (0.96 s) and remains at zero amplitude for 4000 µs (0.004 s) and then it will remain at zero amplitude indefinitely due to the value of `-1` being the special command `ADSR_HANG`.

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

![](../../assets/images/adsr/adsr-light.png#only-light){ .on-glb }
![](../../assets/images/adsr/adsr-dark.png#only-dark){ .on-glb }

=== "Attack"

    ![](../../assets/images/adsr/adsr-attack-light.png#only-light)
    ![](../../assets/images/adsr/adsr-attack-dark.png#only-dark)

    **Attack** refers to the time it takes from when a key is first pressed the sound of a sample to go from zero amplitude to the max attack amplitude. The longer your attack is the longer it will take for the sound to fade in to the max attack amplitude from zero amplitude.

=== "Decay"

    ![](../../assets/images/adsr/adsr-decay-light.png#only-light)
    ![](../../assets/images/adsr/adsr-decay-dark.png#only-dark)

    **Decay** refers to the time it takes the sound of a sample to go from the max attack amplitude to the sustain amplitude. The longer your decay is the longer it will take for the sound to decrease in amplitude from the max attack amplitude to the sustain amplitude.

=== "Sustain"

    ![](../../assets/images/adsr/adsr-sustain-light.png#only-light)
    ![](../../assets/images/adsr/adsr-sustain-dark.png#only-dark)

    **Sustain** refers to the amplitude level the sound of a sample will remain at so long as the note is being held. The higher your sustain is the less of a decrease your amplitude will have from the max attack amplitude.

=== "Release"

    ![](../../assets/images/adsr/adsr-release-light.png#only-light)
    ![](../../assets/images/adsr/adsr-release-dark.png#only-dark)

    **Release** refers to the time it takes from when a key is released to the sound of a sample going from sustain amplitude to return to zero amplitude. The longer your release is the longer it will take for the sound to fade out from your sustain amplitude to zero amplitude.

=== "Hold"

    ![](../../assets/images/adsr/adsr-hold-light.png#only-light)
    ![](../../assets/images/adsr/adsr-hold-dark.png#only-dark)

    **Hold** refers to the time a note will be held at max attack amplitude before beginning to decay to the sustain amplitude. The longer your hold is the longer your sound will remain at max attack amplitude before beginning to decay to sustain amplitude.

-----

*Ocarina of Time* and *Majora's Mask* use a multi-point envelope structure, however instruments and drums are limited to four data points inside of an audiobank (sound effects cannot use envelopes from the audiobank), but the number of data points allowed with a sequence embedded envelope should be higher although it is unknown how much higher it can be but looking through the ADSR code from decomp it can be assumed to be as long as you want, given you have enough data to make the sequence fit into the audio buffer.

### Creating New Sounds With Envelopes
Using only envelopes it is possible to create new sounds without needing to use sample injection. After studying multiple soundfonts, such as the General MIDI soundfont, I <small>figure out way to remove first person speech</small> realized there were samples shared between different instruments, or drums but used to create new instruments and drums. One such example is hi-hats such as the closed hi-hat, pedaled hi-hat, and open hi-hat; *Majora's Mask* has a semi-open hi-hat sample that is perfect for this.

A lot of people in the community use the ride cymbal for hi-hats because the semi-opened hi-hat in *Majora's Mask* just doesn't fit, but you can use the hi-hat to create the other two hi-hats instead of using the ride cymbal by using a custom envelope.

!!! info
    If you don't play on using a custom audiobank, and you have channels to spare in your sequence, you can separate the hi-hat sample into its own channel and use a sequence embedded envelope to create the two missing hi-hat sounds.

#### Closed Hi-Hat Envelope
Below is the envelope to create a closed hi-hat out of the semi-open hi-hat in *Majora's Mask*. It cuts the sample almost immediately resulting in just a short hi-hat hit sound from the initial few seconds of the sample.

??? warning "Note Length Warning"
    Due to the way samples are handled in *Ocarina of Time* and *Majora's Mask*, a short enough note will cut the sample even shorter. This isn't usually a problem for the closed hi-hat, but if the sound is too short then you can try lengthening your closed hi-hat notes in your `.mid` file to give more time for the envelope to finish playing.

=== ":material-code-braces: &nbsp;C"
    ```c
    EnvelopePoint CHH[4] = {
      { 2, 32700 },
      { 12, 0 },
      { -1, 0 },
      { 0, 0 },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <item address="0" name="CHH">
      <struct name="ABEnvelope">
        <field name="Delay 1" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="2"/>
        <field name="Arg 1" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="32700"/>
        <field name="Delay 2" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="12"/>
        <field name="Arg 2" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
        <field name="Delay 3" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="-1"/>
        <field name="Arg 3" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
        <field name="Delay 4" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
        <field name="Arg 4" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
      </struct>
    </item>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```
    00 02 7F BC 00 0C 00 00 FF FF 00 00 00 00 00 00
    ```

#### Pedal Hi-Hat
placeholder

=== ":material-code-braces: &nbsp;C"
    ```c
    EnvelopePoint CHH[4] = {
      { 2, 32700 },
      { 24, 0 },
      { -1, 0 },
      { 0, 0 },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <item address="0" name="PHH">
      <struct name="ABEnvelope">
        <field name="Delay 1" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="2"/>
        <field name="Arg 1" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="32700"/>
        <field name="Delay 2" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="24"/>
        <field name="Arg 2" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
        <field name="Delay 3" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="-1"/>
        <field name="Arg 3" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
        <field name="Delay 4" datatype="int16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
        <field name="Arg 4" datatype="uint16" ispointer="0" isarray="0"
               meaning="none" value="0"/>
      </struct>
    </item>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```
    00 02 7F BC 00 18 00 00 FF FF 00 00 00 00 00 00
    ```

-----