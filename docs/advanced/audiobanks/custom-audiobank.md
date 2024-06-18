# Creating a Custom Audiobank from Scratch

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

placeholder

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
    placeholder

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
    placeholder
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
    placeholder
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
    placeholder
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
    placeholder
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
        Envelopes inside of an audiobank can only be an array of four values!

=== ":material-xml: &nbsp;XML"
    ```xml
    placeholder
    ```

    !!! warning
        Envelopes inside of an audiobank can only be an array of four values!

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
        Envelopes inside of an audiobank can only be an array of four values!

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
    placeholder
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
    placeholder
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
    placeholder
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