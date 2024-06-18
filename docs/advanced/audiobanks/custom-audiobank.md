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

## Audiobank Instrument List

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

## Audiobank Drum List

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: 0x00 */
    Drum* DrumList[64] __attribute__((aligned(16))) = {
      &DrumName, // Pointer to Drum
      NULL,      // Insert "NULL" when there is no drum
    };
    ```

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
      sampleAddr = (u8*)0,        // Address of the sample in the audio table
      loopbook = &SampleLoopbook, // Pointer to loopbook
      codebook = &SampleCodebook, // Pointer to codebook
    };
    ```

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