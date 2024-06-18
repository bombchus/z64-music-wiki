# Building a Custom Audiobank from Scratch

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

placeholder

addresses don't need to be in any particular order except for the header data(?)
for xml, the order is very strict due to SEQ6 hardcoding the data format

!!! warning
    Audiobanks as they are used in-game are slightly different than the structure of `soundfont.h` used by decomp. Tools may also use different naming and formatting and allow for more or less flexibility, this page must be edited again to accomodate for any new `C` based tools that may and will eventually arise from decomp.

!!! alert ":material-code-braces: C Code Warning"
    `C` code for audiobanks may need to be confirmed and edited depending on the tools being worked with.

## Audiobank Metadata

=== ":material-code-braces: &nbsp;C"
    ```c
    AudiobankIndexEntry Metadata = {
      addr = 0,         // not used for bank creation?
      len = 0,          // not used for bank creation?
      sampleMedium = 0, // not used for bank creation?
      seqPlayer = 2,    // not used for bank creation?
      tablenum = 0,     // not used for bank creation?
      fontID = 255,     // not used for bank creation?
      numInst = 0,      // not used for bank creation?
      numDrum = 0,      // not used for bank creation?
      numSfx = 0,       // not used for bank creation?
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- ABIndexEntry Struct -->
    <abindexentry>
      <struct name="ABIndexEntry">
        <!-- Audiobank Address in the Audiobank Index -->
        <field name="addr" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Bank (in Audiobank)"
               ptrto="ABHeader" value="0"/>
        <!-- Size of the Audiobank in Bytes -->
        <field name="len" datatype="uint32" ispointer="0" isarray="0" meaning="Bank Length"
               value="0"/>
        <!-- Sample Mediums: 0 = RAM, 1 = UNK, 2 = ROM, 3 = Disk Drive, 5 = RAM (Unloaded) -->
        <field name="sampleMedium" datatype="uint8" ispointer="0" isarray="0" meaning="none"
               defaultval="2" value="2"/>
        <!-- Sequence Players: 0 = SFX, 1 = Fanfares, 2 = BGM, 3 = Cutscene SFX -->
        <field name="seqPlayer" datatype="uint8" ispointer="0" isarray="0" meaning="none"
               defaultval="2" value="2"/>
        <!-- Audio Tables: 0 = @000000, 1 = @000000, 2 = @538CC0 -->
        <field name="tablenum" datatype="uint8" ispointer="0" isarray="0" meaning="Sample Table number"
               value="1"/>
        <!-- All vanilla audiobanks have 0xFF as their fontId -->
        <field name="fontId" datatype="uint8" ispointer="0" isarray="0" meaning="None"
               defaultval="255" value="255"/>
        <!-- Defines amount of instruments inside the Audiobank -->
        <field name="NUM_INST" datatype="uint8" ispointer="0" isarray="0" meaning="NUM_INST"
               value="1"/>
        <!-- Defines amount of drums inside the Audiobank -->
        <field name="NUM_DRUM" datatype="uint8" ispointer="0" isarray="0" meaning="NUM_DRUM"
               value="0"/>
        <!--
            0x00 has a value of 1 for this, and is the only audiobank containing a value other than
            zero for it; Sauraen's audiobank.h file does not include this value in the index structure.
            Decomp does not include this value in the index structure.
            OoT 0x00 has a value of 0 for this... ???
        -->
        <field name="unknownG" datatype="uint8" ispointer="0" isarray="0" meaning="None"
               defaultval="0" value="0"/>
        <!-- Defines amount of sound effects inside the Audiobank -->
        <field name="NUM_SFX" datatype="uint8" ispointer="0" isarray="0" meaning="NUM_SFX"
               value="0"/>
      </struct>
    </abindexentry>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    00 00 00 00 | ss tt uu vv ww xx yy zz
    ```

    - `ss`: Sample medium (`sampleMedium`) for the samples the audiobank uses
    - `tt`: Sequence player (`seqPlayer`) the audiobank uses
    - `uu`: Audiotable (`tablenum`) the audiobank is in
    - `vv`: "Soundfont ID" (`fontID`) of the audiobank
    - `ww`: Number of instrument (`NUM_INST`) in the audiobank
    - `xx`: Number of drums (`NUM_DRUM`) in the audiobank
    - `yy`: Unknown value
    - `zz`: Number of sound effects (`NUM_SFX`) in the audiobank

    !!! info "Unknown Value"
        It is unknown what `yy` is however *Majora's Mask's* audiobank 0x00 has a value of `1` for `yy` with every other audiobank having a value of `0` for `yy`, and for *Ocarina of Time* has a value of `0` for `yy` for every audiobank.

## Audiobank Header

=== ":material-code-braces: &nbsp;C"
    ```c
    #include "custom_audiobank.h" // include extern

    /* Address: 0x00 */
    Audiobank CustomBank = {
      drums = DrumList,    // Pointer to Drum List
      sfx = NULL,          // Pointer to SFX List
      instruments = {      // Instrument List is built into the header
        &InstName,         // Pointer to inst
        NULL,              // Insert "NULL" when there is no inst
      }
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- ABHeader -->
    <abheader>
      <!-- ABHeader Struct -->
      <struct name="ABheader">
    </abheader>
    <!--ABBank -->
    <abbank>
      <!--ABBank Struct -->
      <struct name="ABBank">
        <!-- Pointer to ABDrumlist-->
        <field name="drumptr" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Drum List"
               ptrto="ABDrumList" value="0"/>
        <!-- Pointer to ABSFXList -->
        <field name="sfxptr" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr SFX List"
               ptrto="ABSFXList" value="0"/>
        <!-- Audiobank Instrument List -->
        <field name="instlist" datatype="uint32" ispointer="1" isarray="1" meaning="List of Ptrs to Insts"
               ptrto="ABInstrument" arraylenvar="NUM_INST">
          <!-- Instrument Pointer -->
          <element datatype="uint32" ispointer="1" ptrto="ABInstrument" value="0"
                  index="0"/>
          <!-- Add more instrument pointers here -->
        </field>
      </struct>
    </abbank>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    00 00 00 00 | xx xx xx xx yy yy yy yy zz zz zz zz -- -- -- --
    ```

    - `xx xx xx xx`: Drum List pointer address
    - `yy yy yy yy`: SFX List pointer address
    - `zz zz zz zz`: Instrument address pointer (`uint32`), there are as many address pointers as there are instruments defined by `NUM_INST`
    - `--`: Padding to byte 16 for alignment

    !!! info "Instrument List"
        The "Instrument List" is built directly into the audiobank header, so instrument address pointers begin immediately after the SFX List.

    !!! info "NULL Address Pointer"
        Addresses that have no information pointed to will be zeroed out, in this case it's important to pay attention to `NUM_INST`, `NUM_DRUM`, and `NUM_SFX` as they define how many addresses there will be in each pointer list; this is important to know because padding is also represented by zero values.

## Audiobank Drum List

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: 0x00 */
    Drum* DrumList[64] __attribute__((aligned(16))) = {
      &DrumName, // Pointer to Drum
      NULL,      // Insert "NULL" when there is no drum
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!--Audiobank Drum List -->
    <abdrumlist address="80">
      <!--ABDrumList Struct -->
      <struct name="ABDrumList">
        <field name="drumlist" datatype="uint32" ispointer="1" isarray="1" meaning="List of Ptrs to Drums"
               ptrto="ABDrum" arraylenvar="NUM_DRUM">
          <!-- INDEX 00 (MIDI Drum Note 21:A1) -->
          <element datatype="uint32" ispointer="1" ptrto="ABDrum" value="00" index="0"/>
          <!-- INDEX 01 (MIDI Drum Note 22:A#1) -->
          <element datatype="uint32" ispointer="1" ptrto="ABDrum" value="0" index="-1"/>
          <!-- Add more drum pointer elements here -->
        </field>
      </struct>
    </abdrumlist>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | xx xx xx xx -- -- -- -- -- -- -- -- -- -- -- --
    ```

    - `xx xx xx xx`: Drum address pointer, there are as many address pointers as there are drums defined by `NUM_DRUM`
    - `--`: Padding to byte 16 for alignment

    !!! info "NULL Address Pointer"
        Addresses that have no information pointed to will be zeroed out, in this case it's important to pay attention to `NUM_INST`, `NUM_DRUM`, and `NUM_SFX` as they define how many addresses there will be in each pointer list; this is important to know because padding is also represented by zero values.

## Audiobank Instruments

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: 0x10 */
    Instrument InstName = {
      relocOffset = 0,         // I forget what this does...
      low_mid_split = 0,       // Max key for low sample and min key for mid sample
      mid_high_split = 127,    // Max key for mid sample and min key for high sample
      decayIndex = 0,          // Also known as release rate
      lowNotesSound = {
        sample = &SoundSample, // Pointer to sample
        tuning = 2.0f,         // Tuning float value
      },
      midNotesSound = {
        sample = &SoundSample, // Pointer to sample
        tuning = 1.0f,         // Tuning float value
      },
      highNotesSound = {
        sample = &SoundSample, // Pointer to sample
        tuning = 0.5f,         // Tuning float value
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- Audiobank Instruments -->
    <instruments>
      <!-- Instrument Item -->
      <item address="0" name="Instrument Name" map="program" program="0">
        <!-- ABInstrument Struct -->
        <struct name="ABInstrument">
          <!-- Relocation Offset -->
          <field name="relocOffset" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                value="0"/>
          <!-- Low Sample max key, Mid Sample min key -->
          <field name="Low/Mid Split" datatype="uint8" ispointer="0" isarray="0"
                meaning="Split Point 1" value="0"/>
          <!-- Mid Sample max key, High Sample min key -->
          <field name="Mid/High Split" datatype="uint8" ispointer="0" isarray="0"
                meaning="Split Point 2" value="127"/>
          <!-- Decay Index (Release Rate) -->
          <field name="Release Rate" datatype="uint8" ispointer="0" isarray="0"
                meaning="Release Rate" value="255"/>
          <!-- Envelope Pointer -->
          <field name="Envelope Pointer" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Envelope"
                 ptrto="ABEnvelope" value="0" index="0"/>
          <!-- Sample Pointer Array -->
          <field name="Sample Pointer Array" datatype="ABSound" ispointer="0" isarray="1" meaning="List of 3 Sounds for Splits"
                arraylenfixed="3">
            <element datatype="ABSound" ispointer="0" value="0">
              <struct name="ABSound">
                <!-- Low Sample Pointer -->
                <field name="Sample Pointer (Low)" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Sample"
                      ptrto="ABSample" value="0" index="-1"/>
                <!-- Low Sample Tuning Float Value -->
                <field name="Tuning" datatype="float32" ispointer="0" isarray="0" meaning="Tuning Float"
                      value="0"/>
              </struct>
            </element>
            <element datatype="ABSound" ispointer="0" value="0">
              <struct name="ABSound">
                <!-- Mid Sample Pointer -->
                <field name="Sample Pointer (Mid)" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Sample"
                      ptrto="ABSample" value="0" index="0"/>
                <!-- Mid Sample Tuning Float Value-->
                <field name="Tuning" datatype="float32" ispointer="0" isarray="0" meaning="Tuning Float"
                      value="1"/>
              </struct>
            </element>
            <element datatype="ABSound" ispointer="0" value="0">
              <struct name="ABSound">
                <!-- High Sample Pointer -->
                <field name="Sample Pointer (High)" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Sample"
                      ptrto="ABSample" value="0" index="-1"/>
                <!-- High Sample Tuning Float Value -->
                <field name="Tuning" datatype="float32" ispointer="0" isarray="0" meaning="Tuning Float"
                      value="0"/>
              </struct>
            </element>
          </field>
        </struct>
      </item>
      <!-- Insert more instrument items here -->
    </instruments>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | pp qq rr ss tt tt tt tt uu uu uu uu vv vv vv vv
    ## ## ## ## | ww ww ww ww xx xx xx xx yy yy yy yy zz zz zz zz
    ```

    - `pp`: Relocation offset
    - `qq`: Low sample max key and mid sample min key
    - `rr`: Mid sample max key and high sample min key
    - `ss`: Decay index
    - `tt tt tt tt`: Envelope pointer address
    - `uu uu uu uu`: Low sample pointer address
    - `vv vv vv vv`: Low sample tuning float value
    - `ww ww ww ww`: Mid sample pointer address
    - `xx xx xx xx`: Mid sample tuning float value
    - `yy yy yy yy`: High sample pointer address
    - `zz zz zz zz`: High sample tuning float value

## Audiobank Drums

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: 0x00 */
    Drum DrumName = {
      decayIndex = 0,           // Also known as Release Rate
      pan = 0,                  // Used when 0xDC is 0
      relocOffset = 0,          // I forget what this does...
      envelope = EnvelopeName,  // Pointer to Envelope
      sound = {
        sample = &SoundSample,  // Pointer to sample
        tuning = 1.0f,          // Tuning float value
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- Audiobank Drums -->
    <drums>
    <!-- Drum Item -->
      <item address="0" name="Drum Name">
        <!-- ABDrum Struct -->
        <struct name="ABDrum">
          <!-- Decay Index (Release Rate) -->
          <field name="Release Rate" datatype="uint8" ispointer="0" isarray="0"
                 meaning="Release Rate" value="255"/>
          <!-- Drum Pan (used when 0xDC is 0)-->
          <field name="Pan" datatype="uint8" ispointer="0" isarray="0" meaning="Pan"
                 value="0"/>
          <!-- Unknown (one of the two values is relocOffset) -->
          <field name="unknown3" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                 defaultval="0" value="0"/>
          <field name="unknown4" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                 defaultval="0" value="0"/>
          <field name="Drum Sound" datatype="ABSound" ispointer="0" isarray="0"
                 meaning="Drum Sound" value="0">
            <struct name="ABSound">
              <!-- Drum Sample Pointer -->
              <field name="Sample Pointer" datatype="uint32" ispointer="1" isarray="0"
                     meaning="Ptr Sample" ptrto="ABSample" value="128" index="0"/>
              <!-- Sample Tuning Float Value -->
              <field name="Tuning" datatype="float32" ispointer="0" isarray="0" meaning="Tuning Float"
                     value="1"/>
            </struct>
          </field>
          <!-- Envelope Pointer -->
          <field name="Envelope Pointer" datatype="uint32" ispointer="1" isarray="0"
                 meaning="Ptr Envelope" ptrto="ABEnvelope" value="112" index="0"/>
        </struct>
      </item>
      <!-- Add more drum items here -->
    </drums>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | tt uu vv ww xx xx xx xx yy yy yy yy zz zz zz zz
    ```

    - `tt`: Decay index
    - `uu`: Drum pan
    - `vv`: Unknown value
    - `ww`: Unknown value
    - `xx xx xx xx`: Sample pointer address
    - `yy yy yy yy`: Sample tuning float value
    - `zz zz zz zz`: Envelope pointer address

    !!! info "Unknown Value"
        One of these unknown values is the relocation offset, however the other value is completely unknown.

## Audiobank Envelopes

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: 0x00 */
    // can delay and arg be left out and just have values like gDefaultEnvelope?
    EnvelopePoint EnvelopeName[4] = {
      { 2, 32700 },     // Attack Phase
      { 1, 32700 },     // Decay or Hold Phase
      { 32700, 29430 }, // Decay or Sustain Phase 
      { -1, 0     },    // Sustain Phase
    };
    ```

    !!! warning
        Envelopes inside of an audiobank can only be four values long!

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- Audiobank Envelopes -->
    <envelopes>
      <!-- Envelope Item -->
      <item address="0" name="Envelope Name">
        <!-- ABEnvelope Struct -->
        <struct name="ABEnvelope">
          <!-- Delay Value 1 (Time) -->
          <field name="delay1" datatype="int16" ispointer="0" isarray="0"
                 meaning="none" value="2"/>
          <!-- Argument Value 1 (Amplitude) -->
          <field name="arg1" datatype="uint16" ispointer="0" isarray="0"
                 meaning="none" value="32700"/>
          <!-- Delay Value 2 (Time) -->
          <field name="delay2" datatype="int16" ispointer="0" isarray="0"
                 meaning="none" value="298"/>
          <!-- Argument Value 2 (Amplitude) -->
          <field name="arg2" datatype="uint16" ispointer="0" isarray="0"
                 meaning="none" value="0"/>
          <!-- Delay Value 2 (Time) -->
          <field name="delay3" datatype="int16" ispointer="0" isarray="0"
                 meaning="none" value="1"/>
          <!-- Argument Value 3 (Amplitude) -->
          <field name="arg3" datatype="uint16" ispointer="0" isarray="0"
                 meaning="none" value="0"/>
          <!-- Delay Value 4 (Time) -->
          <field name="delay4" datatype="int16" ispointer="0" isarray="0" meaning="none"
                 value="-1"/>
          <!-- Argument Value 4 (Amplitude) -->
          <field name="arg4" datatype="uint16" ispointer="0" isarray="0" meaning="none"
                 value="0"/>
        </struct>
      </item>
      <!-- Add more envelope items here -->
    </envelopes>
    ```

    !!! warning
        Envelopes inside of an audiobank can only be four values long!

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | ss ss tt tt uu uu vv vv ww ww xx xx yy yy zz zz
    ```

    - `ss ss`: Envelope delay value 1
    - `tt tt`: Envelope argument value 1
    - `uu uu`: Envelope delay value 2
    - `vv vv`: Envelope argument value 2
    - `ww ww`: Envelope delay value 3
    - `xx xx`: Envelope argument value 3
    - `yy yy`: Envelope delay value 4
    - `zz zz`: Envelope argument value 4

    !!! warning
        Envelopes inside of an audiobank can only be four values long!

## Audiobank Samples

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: */
    Sample SoundSample = {
      codec = 0,                  // I forget what this does...
      medium = 0,                 // Location of the sample data
      unk_bit26 = 0,              // Unknown
      relocOffset = 0,            // I forget what this does...
      size = 0,                   // Size of the sample in bytes
      sampleAddr = (u8*)0,        // Address of the sample
      loopbook = &SampleLoopbook, // Pointer to loopbook
      codebook = &SampleCodebook, // Pointer to codebook
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- Audiobank Samples -->
    <samples>
      <!-- Sample Item -->
      <item address="128" name="SAMPLE NAME">
        <!--ABSample Struct -->
        <struct name="ABSample">
          <!--
              One unknown value should contain data for a sample medium, and another for the codec;
              there should also be a value for a relocation offset and unk_bit26 (defines used samples?).
              Not every field needs to be present?
              Sauraen's audiobank.h structure includes the codec, medium, relocation offset, and unk_bit26.
              Decomp's structure includes the codec, medium, relocation offset, and unk_bit26.
          -->
          <field name="unknown1" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                 value="0"/>
          <field name="unknown2" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                 value="0"/>
          <!-- Sample Size in Bytes -->
          <field name="Sample Size (ROM Insert Size)" datatype="uint16" ispointer="0" isarray="0"
                 meaning="Sample Length" value="0"/>
          <!-- Sample Address Pointer -->
          <field name="Sample Address" datatype="uint32" ispointer="0" isarray="0"
                 meaning="Sample Address (in Sample Table)" ptrto="ATSample" value="0"/>
          <!-- Sample Loopbook Pointer -->
          <field name="Loopbook" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr ALADPCMLoop"
                 ptrto="ALADPCMLoop" value="0" index="0"/>
          <!-- Sample Codebook Pointer -->
          <field name="Codebook" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr ALADPCMBook"
                 ptrto="ALADPCMBook" value="0" index="0"/>
        </struct>
      </item>
      <!-- Add more sample items here -->
    </samples>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | uu vv ww ww xx xx xx xx yy yy yy yy zz zz zz zz
    ```

    - `uu`: Unknown value
    - `vv`: Unknown value
    - `ww ww`: Sample size in bytes
    - `xx xx xx xx`: Sample address pointer
    - `yy yy yy yy`: Loopbook address pointer
    - `zz zz zz zz`: Cdebook address pointer

    !!! info "Unknown Value"
        It is currently unknown what these values are, they could be `codec`, `medium`, `unk_bit26`, or `relocOffset`.

## Audiobank Codebooks

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address :*/
    AdpcmBook SampleCodebook = {
      order = 0,                // I forget what this does...
      numPredictors = 0,        // Number of predictor arrays
      codebook = {
        0, 0, 0, 0, 0, 0, 0, 0, // First predictor array (16 values)
        0, 0, 0, 0, 0, 0, 0, 0,
        0, 0, 0, 0, 0, 0, 0, 0, // Second predictor array (16 values)
        0, 0, 0, 0, 0, 0, 0, 0,
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- Audiobank Codebooks -->
    <aladpcmbooks>
      <!-- Codebook Item -->
      <item address="0" name="Codebook Name">
        <!-- ALADPCMBook Struct -->
        <struct name="ALADPCMBook" NUM_PRED="4">
          <!-- Codebook Order -->
          <field name="order" datatype="int32" ispointer="0" isarray="0" meaning="None"
                value="4"/>
          <!-- Number of Predictors -->
          <field name="npredictors" datatype="int32" ispointer="0" isarray="0"
                meaning="NUM_PRED" value="4"/>
          <!-- Codebook Predictor Arrays -->
          <field name="book" datatype="ALADPCMPredictor" ispointer="0" isarray="1"
                meaning="Array of Predictors" arraylenvar="NUM_PRED">
            <!-- Codebook Predictor Array 1 -->
            <element datatype="ALADPCMPredictor" ispointer="0" value="0">
              <struct name="ALADPCMPredictor">
                <field name="data" datatype="int16" ispointer="0" isarray="1" meaning="None"
                      arraylenfixed="16">
                  <!-- COPY & PASTE YOUR PREDICTOR FIRST ARRAY HERE!! -->
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                </field>
              </struct>
            </element>
            <!-- Codebook Predictor Array 2 -->
            <element datatype="ALADPCMPredictor" ispointer="0" value="0">
              <struct name="ALADPCMPredictor">
                <field name="data" datatype="int16" ispointer="0" isarray="1" meaning="None"
                      arraylenfixed="16">
                  <!-- COPY & PASTE YOUR PREDICTOR SECOND ARRAY HERE!! -->
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                </field>
              </struct>
            </element>
            <!-- Codebook Predictor Array 3 -->
            <element datatype="ALADPCMPredictor" ispointer="0" value="0">
              <struct name="ALADPCMPredictor">
                <field name="data" datatype="int16" ispointer="0" isarray="1" meaning="None"
                      arraylenfixed="16">
                  <!-- COPY & PASTE YOUR PREDICTOR THIRD ARRAY HERE!! -->
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                </field>
              </struct>
            </element>
            <!-- Codebook Predictor Array 4 -->
            <element datatype="ALADPCMPredictor" ispointer="0" value="0">
              <struct name="ALADPCMPredictor">
                <field name="data" datatype="int16" ispointer="0" isarray="1" meaning="None"
                      arraylenfixed="16">
                  <!-- COPY & PASTE YOUR PREDICTOR FOURTH ARRAY HERE!! -->
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                </field>
              </struct>
            </element>
          </field>
        </struct>
      </item>
      <!-- Add more codebook items here -->
    </aladpcmbooks>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | ww ww ww ww xx xx xx xx y0 y0 y1 y1 y2 y2 y3 y3
    ## ## ## ## | y4 y4 y5 y5 y6 y6 y7 y7 y8 y8 y9 y9 yA yA yB yB
    ## ## ## ## | yC yC yD yD yE yE yF yF z0 z0 z1 z1 z2 z2 z3 z3
    ## ## ## ## | z4 z4 z5 z5 z6 z6 z7 z7 z8 z8 z9 z9 zA zA zB zB
    ## ## ## ## | zC zC zD zD zE zE zF zF -- -- -- -- -- -- -- --
    ```

    - `ww ww ww ww`: Order value
    - `xx xx xx xx`: Number of predictors value
    - `y# y#`: Codebook array value
    - `z# z#`: Codebook array value
    - `--`: Padding to byte 16 for alignment

    !!! info "Codebook Array"
        Codebook arrays are an array of 16 `int16` values with the number of arrays being used by vanilla samples at two arrays and the number of arrays being used by custom samples at four arrays.
    

## Audiobank Loopbooks

=== ":material-code-braces: &nbsp;C"
    ```c
    AdpcmLoop SampleLoopbook = {
      loopStart = 0,            // Loop start marker of the sample; if loop count = 0 then leave as 0
      loopEnd = 0,              // Loop end marker of the sample; if loop count = 0 then this becomes numSamples
      loopCount = 0,            // Total number of times to loop the sample; -1 is indefinite
      numSamples = 0,           // Total number of samples; if loop count = 0 then leave as 0
      /* predictorState only exists if loopCount != 0 */
      predictorState = {
        0, 0, 0, 0, 0, 0, 0, 0, // Predictor array
        0, 0, 0, 0, 0, 0, 0, 0,
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml
    <!-- Audiobank Loopbooks -->
    <aladpcmloops>
    <!-- Loopbook Item -->
      <item address="0" name="Loopbook Name">
        <!-- ALADPCMLoop Struct -->
        <struct name="ALADPCMLoop" HAS_TAIL="0">
          <!-- Loop Start -->
          <field name="Loop Start" datatype="uint32" ispointer="0" isarray="0" meaning="Loop Start"
                 value="0"/>
          <!-- Loop End (If Loop Count = 0 then it becomes Number of Samples)-->
          <field name="Loop End (Sample Length)" datatype="uint32" ispointer="0" isarray="0" meaning="Loop End"
                 value="0"/>
          <!-- Loop Count -->
          <field name="Loop Count" datatype="uint32" ispointer="0" isarray="0" meaning="Loop Count"
                 defaultval="-1" value="-1"/>
          <!-- Number of Samples -->
          <field name="Number of Samples" datatype="uint32" ispointer="0" isarray="0"
                 meaning="None" defaultval="0" value="0"/>
          <!-- Predictor State -->
          <field name="Tail Data" datatype="ALADPCMTail" ispointer="0" isarray="1"
                 meaning="Tail Data (if Loop Start != 0)" arraylenvar="HAS_TAIL">
            <!-- If Loop Count != 0 insert the array, otherwise remove the array -->
            <!-- Loopbook Predictor Array -->
            <element datatype="ALADPCMTail" ispointer="0" value="0">
              <struct name="ALADPCMTail">
                <field name="some_adpcm_data" datatype="int16" ispointer="0" isarray="1"
                       meaning="None" arraylenfixed="16">
                  <!-- COPY & PASTE YOUR LOOP PREDICTOR ARRAY HERE!! -->
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                  <element datatype="int16" ispointer="0" value="0"/>
                </field>
              </struct>
            </element> <!-- End of Loopbook Predictor Array -->
          </field> <!-- Closing tag for Predictor State -->
        </struct>
      </item>
      <!-- Add more loopbook items here -->
    </aladpcmloops>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | vv vv vv vv ww ww ww ww xx xx xx xx yy yy yy yy
    ## ## ## ## | z0 z0 z1 z1 z2 z2 z3 z3 z4 z4 z5 z5 z6 z6 z7 z7
    ## ## ## ## | z8 z8 z9 z9 zA zA zB zB zC zC zD zD zE zE zF zF
    ```

    - `vv vv vv vv`: Loop start value
    - `ww ww ww ww`: Loop end value
    - `xx xx xx xx`: Loop count value
    - `yy yy yy yy`: Number of samples value
    - `z# Z#`: Loopbook array value

    !!! info "Loopbook Array"
        Loopbook arrays are an array of 16 `int16` values with the array only being present if "Loop Count" is not equal to zero.