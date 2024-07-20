# Building a Custom Audiobank

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details building an audiobank completely from scratch in C, XML, and as a Binary file.

## Data Ordering

For C and Binary, items do not need to be in any particular order except for the header data; so long as all the addresses match the order of data should not matter(?). For XML, the order is very strict due to SEQ6 hardcoding the data format; addresses can be left as zeroed values, SEQ64 will automatically assign addresses when overwriting an audiobank, however, indexes must be correct.

??? info "Important XML Info"
    For XML audiobanks, all structures must be contained within a bank that contains some metadata information tag:
    ```xml linenums="0"
    <?xml version="1.0" encoding="UTF-8"?>
    <!-- Above is the XML declaration, do not remove it -->

    <bank NUM_INST="0" NUM_DRUM="0" NUM_SFX="0" ATnum="0">
      <!-- All the audiobank information is contained within the tags-->
    </bank>
    ```

    Audiobanks must also be structured in a very specific way, otherwise SEQ64 will not be able to read the audiobank and will throw errors:
    ```xml
    <?xml version="1.0" encoding="UTF-8"?>

    <bank NUM_INST="0" NUM_DRUM="0" NUM_SFX="0" ATnum="0">
      <!-- Audiobank Index Entry -->
      <abindexentry>
        <!-- Insert structure here -->
      </abindexentry>
      <!-- Audiobank Header -->
      <abheader>
        <!-- Insert structure here -->
      </abheader>
      <!-- ABBank -->
      <abbank>
        <!-- Insert structure here -->
      </abbank>
      <!-- Audiobank Drum List -->
      <abdrumlist>
        <!-- Insert drum list here -->
      </abdrumlist>
      <!-- Audiobank SFX List -->
      <absfxlist>
        <!-- Insert sfx list here -->
      </absfxlist>
      <!-- Audiobank Instruments -->
      <instruments>
        <!-- Insert item(s) here -->
      </instruments>
      <!-- Audiobank Drums -->
      <drums>
        <!-- Insert item(s) here -->
      </drums>
      <!-- For OOT and MM leave this as-is -->
      <sfx/>
      <!-- Audiobank Envelope -->
      <envelopes>
        <!-- Insert item(s) here -->
      </envelopes>
      <!-- Audiobank Samples -->
      <samples>
        <!-- Insert item(s) here -->
      </samples>
      <!-- Audiobank Codebooks -->
      <aladpcmbooks>
        <!-- Insert item(s) here -->
      </aladpcmbooks>
      <!-- Audiobank Loopbooks -->
      <aladpcmloops>
        <!-- Insert item(s) here -->
      </aladpcmloops>
    </bank>
    ```

-----

!!! warning
    Audiobanks as they are used in-game are slightly different than the structure of `soundfont.h` used by decomp. Tools may also use different naming and formatting and allow for more or less flexibility, this page must be edited again to accomodate for any new `C` based tools that may and will eventually arise from decomp.

!!! alert ":material-code-braces: C Code Warning"
    `C` code for audiobanks may need to be confirmed and edited depending on the tools being worked with.

## Audiobank Metadata

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    AudiobankIndexEntry Metadata = {
      addr = 0,
      len = 0,
      sample_medium = 0,
      seq_player = 2,
      table_num = 0,
      soundfont_id = 255,
      num_inst = 0,
      num_drum = 0,
      num_sfx = 0,
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml linenums="0"
    <!-- Audiobank Index Entry -->
    <abindexentry>
      <!-- ABIndexEntry Struct -->
      <struct name="ABIndexEntry">
        <!-- Audiobank Address in the Audiobank Index -->
        <field name="addr" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Bank (in Audiobank)"
               ptrto="ABHeader" value="0"/>
        <!-- Size of the Audiobank in Bytes -->
        <field name="len" datatype="uint32" ispointer="0" isarray="0" meaning="Bank Length"
               value="0"/>
        <!-- Sample Mediums: 0 = RAM, 1 = UNK, 2 = ROM, 3 = Disk Drive, 5 = RAM (Unloaded) -->
        <field name="sample_medium" datatype="uint8" ispointer="0" isarray="0" meaning="none"
               defaultval="2" value="2"/>
        <!-- Sequence Players: 0 = SFX, 1 = Fanfares, 2 = BGM, 3 = Cutscene SFX -->
        <field name="seq_player" datatype="uint8" ispointer="0" isarray="0" meaning="none"
               defaultval="2" value="2"/>
        <!-- Audio Tables: 0 = @000000, 1 = @000000, 2 = @538CC0 -->
        <field name="table_num" datatype="uint8" ispointer="0" isarray="0" meaning="Sample Table number"
               value="1"/>
        <!-- All vanilla audiobanks have 0xFF as their fontId -->
        <field name="soundfont_id" datatype="uint8" ispointer="0" isarray="0" meaning="None"
               defaultval="255" value="255"/>
        <!-- Defines amount of instruments inside the Audiobank -->
        <field name="NUM_INST" datatype="uint8" ispointer="0" isarray="0" meaning="NUM_INST"
               value="1"/>
        <!-- Defines amount of drums inside the Audiobank -->
        <field name="NUM_DRUM" datatype="uint8" ispointer="0" isarray="0" meaning="NUM_DRUM"
               value="0"/>
        <!-- Defines amount of sound effects inside the Audiobank -->
        <field name="NUM_SFX" datatype="uint16" ispointer="0" isarray="0" meaning="NUM_SFX"
               value="0"/>
      </struct>
    </abindexentry>
    ```

=== ":material-hexadecimal: &nbsp;Binary"
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    00 00 00 00 | tt uu vv ww xx yy zz zz
    ```

    - `tt` = Sample medium (`sample_medium`) for the samples the audiobank uses
    - `uu` = Sequence player (`seq_player`) the audiobank uses
    - `vv` = Audiotable (`table_num`) the audiobank is in
    - `ww` = "Soundfont ID" (`soundfont_id`) of the audiobank
    - `xx` = Number of instrument (`NUM_INST`) in the audiobank
    - `yy` = Number of drums (`NUM_DRUM`) in the audiobank
    - `zz zz` = Number of sound effects (`NUM_SFX`) in the audiobank

## Audiobank Header

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
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
    ```xml linenums="0"
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
        <field name="drum_ptr" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr Drum List"
               ptrto="ABDrumList" value="0"/>
        <!-- Pointer to ABSFXList -->
        <field name="sfx_ptr" datatype="uint32" ispointer="1" isarray="0" meaning="Ptr SFX List"
               ptrto="ABSFXList" value="0"/>
        <!-- Audiobank Instrument List -->
        <field name="inst_list" datatype="uint32" ispointer="1" isarray="1" meaning="List of Ptrs to Insts"
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    00 00 00 00 | xx xx xx xx yy yy yy yy zz zz zz zz -- -- -- --
    ```

    - `xx xx xx xx` = Drum List pointer address
    - `yy yy yy yy` = SFX List pointer address
    - `zz zz zz zz` = Instrument address pointer (`uint32`), there are as many address pointers as there are instruments defined by `NUM_INST`
    - `--` = Padding to byte 16 for alignment

    !!! info "Instrument List"
        The "Instrument List" is built directly into the audiobank header, so instrument address pointers begin immediately after the SFX List.

    !!! info "NULL Address Pointer"
        Addresses that have no information pointed to will be zeroed out, in this case it is important to pay attention to `NUM_INST`, `NUM_DRUM`, and `NUM_SFX` as they define how many addresses there will be in each pointer list; this is important to know because padding is also represented by zero values.

## Audiobank Drum List

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    /* Address: 0x00 */
    Drum* DrumList[64] __attribute__((aligned(16))) = {
      &DrumName, // Pointer to Drum
      NULL,      // Insert "NULL" when there is no drum
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml linenums="0"
    <!--Audiobank Drum List -->
    <abdrumlist address="80">
      <!--ABDrumList Struct -->
      <struct name="ABDrumList">
        <field name="drum_list" datatype="uint32" ispointer="1" isarray="1" meaning="List of Ptrs to Drums"
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | xx xx xx xx -- -- -- -- -- -- -- -- -- -- -- --
    ```

    - `xx xx xx xx` = Drum address pointer, there are as many address pointers as there are drums defined by `NUM_DRUM`
    - `--` = Padding to byte 16 for alignment

    !!! info "NULL Address Pointer"
        Addresses that have no information pointed to will be zeroed out, in this case it is important to pay attention to `NUM_INST`, `NUM_DRUM`, and `NUM_SFX` as they define how many addresses there will be in each pointer list; this is important to know because padding is also represented by zero values.

## Audiobank Instruments

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    /* Address: 0x10 */
    Instrument InstName = {
      reloc_offset = 0,        // Offset to pointers
      key_min = 0,             // Max key for low sample and min key for mid sample
      key_max = 127,           // Max key for mid sample and min key for high sample
      rel_rate = 0,            // Determines amount of decay when note is released
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
    ```xml linenums="0"
    <!-- Audiobank Instruments -->
    <instruments>
      <!-- Instrument Item -->
      <item address="0" name="Instrument Name" map="program" program="0">
        <!-- ABInstrument Struct -->
        <struct name="ABInstrument">
          <!-- Relocation Offset -->
          <field name="reloc_offset" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                value="0"/>
          <!-- Low Sample max key, Mid Sample min key -->
          <field name="Low-Mid Split" datatype="uint8" ispointer="0" isarray="0"
                meaning="Split Point 1" value="0"/>
          <!-- Mid Sample max key, High Sample min key -->
          <field name="Mid-High Split" datatype="uint8" ispointer="0" isarray="0"
                meaning="Split Point 2" value="127"/>
          <!-- Release Rate -->
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | pp qq rr ss tt tt tt tt uu uu uu uu vv vv vv vv
    ## ## ## ## | ww ww ww ww xx xx xx xx yy yy yy yy zz zz zz zz
    ```

    - `pp` = Relocation offset
    - `qq` = Low sample max key and mid sample min key
    - `rr` = Mid sample max key and high sample min key
    - `ss` = Release rate
    - `tt tt tt tt` = Envelope pointer address
    - `uu uu uu uu` = Low sample pointer address
    - `vv vv vv vv` = Low sample tuning float value
    - `ww ww ww ww` = Mid sample pointer address
    - `xx xx xx xx` = Mid sample tuning float value
    - `yy yy yy yy` = High sample pointer address
    - `zz zz zz zz` = High sample tuning float value

## Audiobank Drums

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    /* Address: 0x00 */
    Drum DrumName = {
      rel_rate = 0,             // Determines amount of decay when note is released
      pan = 0,                  // Used when 0xDC is 0
      reloc_offset = 0,         // Offset to pointers
      envelope = EnvelopeName,  // Pointer to Envelope
      sound = {
        sample = &SoundSample,  // Pointer to sample
        tuning = 1.0f,          // Tuning float value
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml linenums="0"
    <!-- Audiobank Drums -->
    <drums>
    <!-- Drum Item -->
      <item address="0" name="Drum Name">
        <!-- ABDrum Struct -->
        <struct name="ABDrum">
          <!-- Release Rate -->
          <field name="Release Rate" datatype="uint8" ispointer="0" isarray="0"
                 meaning="Release Rate" value="255"/>
          <!-- Drum Pan (used when 0xDC is 0)-->
          <field name="Pan" datatype="uint8" ispointer="0" isarray="0" meaning="Pan"
                 value="0"/>
          <field name="reloc_offset" datatype="uint16" ispointer="0" isarray="0" meaning="None"
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | uu vv ww ww xx xx xx xx yy yy yy yy zz zz zz zz
    ```

    - `uu` = Release Rate
    - `vv` = Drum pan
    - `ww ww` = Relocation Offset
    - `xx xx xx xx` = Sample pointer address
    - `yy yy yy yy` = Sample tuning float value
    - `zz zz zz zz` = Envelope pointer address

## Audiobank Envelopes

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
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
    ```xml linenums="0"
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | ss ss tt tt uu uu vv vv ww ww xx xx yy yy zz zz
    ```

    - `ss ss` = Envelope delay value 1
    - `tt tt` = Envelope argument value 1
    - `uu uu` = Envelope delay value 2
    - `vv vv` = Envelope argument value 2
    - `ww ww` = Envelope delay value 3
    - `xx xx` = Envelope argument value 3
    - `yy yy` = Envelope delay value 4
    - `zz zz` = Envelope argument value 4

    !!! warning
        Envelopes inside of an audiobank can only be four values long!

## Audiobank Samples

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    /* Address: */
    Sample SoundSample = {
      codec = 0,                  // Does not exist in the binary
      medium = 0,                 // Does not exist in the binary
      unk_bit26 = 0,              // if (sample->unk_bit26 && (sample->medium != MEDIUM_RAM))
      relocOffset = 0,            // Offset to pointers
      size = 0,                   // Size of the sample in bytes
      sampleAddr = (u8*)0,        // Address of the sample
      loopbook = &SampleLoopbook, // Pointer to loopbook
      codebook = &SampleCodebook, // Pointer to codebook
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml linenums="0"
    <!-- Audiobank Samples -->
    <samples>
      <!-- Sample Item -->
      <item address="128" name="SAMPLE NAME">
        <!--ABSample Struct -->
        <struct name="ABSample">
          <field name="unk_bit26" datatype="uint8" ispointer="0" isarray="0" meaning="None"
                 value="0"/>
          <field name="reloc_offset" datatype="uint8" ispointer="0" isarray="0" meaning="None"
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | uu vv ww ww xx xx xx xx yy yy yy yy zz zz zz zz
    ```

    - `uu` = unk_bit26
    - `vv` = reloc_offset
    - `ww ww` = Sample size in bytes
    - `xx xx xx xx` = Sample address pointer
    - `yy yy yy yy` = Loopbook address pointer
    - `zz zz zz zz` = Cdebook address pointer

## Audiobank Codebooks

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    /* Address :*/
    AdpcmBook SampleCodebook = {
      order = 0,                // I forget what this does...
      num_predictors = 0,       // Number of predictor arrays
      codebook = {
        0, 0, 0, 0, 0, 0, 0, 0, // First predictor array (16 values)
        0, 0, 0, 0, 0, 0, 0, 0,
        0, 0, 0, 0, 0, 0, 0, 0, // Second predictor array (16 values)
        0, 0, 0, 0, 0, 0, 0, 0,
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml linenums="0"
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
          <field name="num_predictors" datatype="int32" ispointer="0" isarray="0"
                meaning="NUM_PRED" value="4"/>
          <!-- Codebook Predictor Arrays -->
          <field name="book" datatype="ALADPCMPredictor" ispointer="0" isarray="1"
                meaning="Array of Predictors" arraylenvar="NUM_PRED">
            <!-- Codebook Predictor Array 1 -->
            <element datatype="ALADPCMPredictor" ispointer="0" value="0">
              <struct name="ALADPCMPredictor">
                <field name="data" datatype="int16" ispointer="0" isarray="1" meaning="None"
                      arraylenfixed="16">
                  <!-- COPY & PASTE FIRST PREDICTOR ARRAY HERE!! -->
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
                  <!-- COPY & PASTE SECOND PREDICTOR ARRAY HERE!! -->
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
                  <!-- COPY & PASTE THIRD PREDICTOR ARRAY HERE!! -->
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
                  <!-- COPY & PASTE FOURTH PREDICTOR ARRAY HERE!! -->
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | ww ww ww ww xx xx xx xx y0 y0 y1 y1 y2 y2 y3 y3
    ## ## ## ## | y4 y4 y5 y5 y6 y6 y7 y7 y8 y8 y9 y9 yA yA yB yB
    ## ## ## ## | yC yC yD yD yE yE yF yF z0 z0 z1 z1 z2 z2 z3 z3
    ## ## ## ## | z4 z4 z5 z5 z6 z6 z7 z7 z8 z8 z9 z9 zA zA zB zB
    ## ## ## ## | zC zC zD zD zE zE zF zF -- -- -- -- -- -- -- --
    ```

    - `ww ww ww ww` = Order value
    - `xx xx xx xx` = Number of predictors value
    - `y# y#` = Codebook array value
    - `z# z#` = Codebook array value
    - `--` = Padding to byte 16 for alignment

    !!! info "Codebook Array"
        Codebook arrays are an array of 16 `int16` values with the number of arrays being used by vanilla samples at two arrays and the number of arrays being used by custom samples at four arrays.
    

## Audiobank Loopbooks

=== ":material-code-braces: &nbsp;C"
    ```c linenums="0"
    AdpcmLoop SampleLoopbook = {
      loop_start = 0,            // Loop start marker of the sample; if loop count = 0 then leave as 0
      loop_end = 0,              // Loop end marker of the sample; if loop count = 0 then this becomes num_samples
      loop_count = 0,            // Total number of times to loop the sample; -1 is indefinite
      num_samples = 0,           // Total number of samples; if loop count = 0 then leave as 0
      /* loopbook only exists if loopCount != 0 */
      loopbook = {
        0, 0, 0, 0, 0, 0, 0, 0, // Predictor array
        0, 0, 0, 0, 0, 0, 0, 0,
      },
    };
    ```

=== ":material-xml: &nbsp;XML"
    ```xml linenums="0"
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
          <field name="Loopbook" datatype="ALADPCMTail" ispointer="0" isarray="1"
                 meaning="Tail Data (if Loop Start != 0)" arraylenvar="HAS_TAIL">
            <!-- If Loop Count != 0 insert the array, otherwise remove the array -->
            <!-- Loopbook Predictor Array -->
            <element datatype="ALADPCMTail" ispointer="0" value="0">
              <struct name="ALADPCMTail">
                <field name="data" datatype="int16" ispointer="0" isarray="1"
                       meaning="None" arraylenfixed="16">
                  <!-- COPY & PASTE LOOP PREDICTOR ARRAY HERE!! -->
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
    ```bin linenums="0"
    Offset (h)  | 00 01 02 03 04 05 06 07 08 09 0A 0B 0C 0D 0E 0F
    —————————————————————————————————————————————————————————————
    ## ## ## ## | vv vv vv vv ww ww ww ww xx xx xx xx yy yy yy yy
    ## ## ## ## | z0 z0 z1 z1 z2 z2 z3 z3 z4 z4 z5 z5 z6 z6 z7 z7
    ## ## ## ## | z8 z8 z9 z9 zA zA zB zB zC zC zD zD zE zE zF zF
    ```

    - `vv vv vv vv` = Loop start value
    - `ww ww ww ww` = Loop end value
    - `xx xx xx xx` = Loop count value
    - `yy yy yy yy` = Number of samples value
    - `z# z#` = Loopbook array value

    !!! info "Loopbook Array"
        Loopbook arrays are an array of 16 `int16` values with the array only being present if "Loop Count" is not equal to zero.