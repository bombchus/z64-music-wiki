# Creating a Custom Audiobank from Scratch

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

placeholder

!!! alert ":material-code-braces: C Code Warning"
    I am unsure if dots are needed before values, and if the envelope value needs to be different...
    It might be easier just to build a bank using Sauraen's "AudiobankToC" instead of building it from scratch, assuming you're even working with `C` editing tools in the first place.

## Audiobank Header

=== ":material-code-braces: &nbsp;C"
    ```c
    #include "custom_audiobank.h" // include extern

    /* Address: 0x00 */
    Audiobank CustomBank = {
      // addr = 0,         // not used for bank creation?
      // len = 0,          // not used for bank creation?
      // sampleMedium = 0, // not used for bank creation?
      // seqPlayer = 2,    // not used for bank creation?
      // tablenum = 0,     // not used for bank creation?
      // fontID = 255,     // not used for bank creation?
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
      relocOffset = 0,
      low_mid_split = 0,
      mid_high_split = 127,
      decayIndex = 0,
      lowNotesSound = {
        sample = &SoundSample,
        tuning = 2.0f,
      },
      midNotesSound = {
        sample = &SoundSample,
        tuning = 1.0f,
      },
      highNotesSound = {
        sample = &SoundSample,
        tuning = 0.5f,
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
      decayIndex = 0,          // Also known as Release Rate
      pan = 0,                 // Used when 0xDC is 0
      loaded = 0,              // I forget what this was...
      envelope = EnvelopeName, // Pointer to Envelope
      sound = {
        sample = &SoundSample,  // Pointer to Sample
        tuning = 1.0f,         // Tuning float value
      },
    };
    ```

## Audiobank Envelopes

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: 0x00 */
    EnvelopePoint EnvelopeName[4] = {
      { 2, 32700 },     // Attack Phase
      { 1, 32700 },     // Decay or Hold Phase
      { 32700, 29430 }, // Decay or Sustain Phase 
      { ADSR_HANG, 0 }, // Sustain Phase
    };
    ```

## Audiobank Samples

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address: */
    Sample SoundSample = {
      codec = 0,
      medium = 0,
      unk_bit26 = 0,
      relocOffset = 0,
      size = 0,
      sampleAddr = (u8*)0,
      loopbook = &SampleLoopbook,
      codebook = &SampleCodebook,
    };
    ```

## Audiobank Codebooks

=== ":material-code-braces: &nbsp;C"
    ```c
    /* Address :*/
    AdpcmBook SampleCodebook = {
      order = 0,
      numPredictors = 0,
      codebook = {
        0, 0, 0, 0, 0, 0, 0, 0,
        0, 0, 0, 0, 0, 0, 0, 0,
        0, 0, 0, 0, 0, 0, 0, 0,
        0, 0, 0, 0, 0, 0, 0, 0,
      },
    };
    ```

## Audiobank Loopbooks

=== ":material-code-braces: &nbsp;C"
    ```c
    AdpcmLoop SampleLoopbook = {
      loopStart = 0,
      loopEnd = 0,
      loopCount = 0,
      numSamples = 0,
      // Only exists if loopCount != 0
      predictorState = {
        0, 0, 0, 0, 0, 0, 0, 0,
        0, 0, 0, 0, 0, 0, 0, 0,
      },
    };
    ```