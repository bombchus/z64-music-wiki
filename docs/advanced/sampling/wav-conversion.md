# Creating Sample Data by Converting WAV Files

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

??? alert "A Word of Caution"
    The ROMs of *Ocarina of Time* and *Majora's Mask* have a limited file space of 64 MiB decompressed, and it becomes 32 MiB when compressed. To retain compatibility with both Nintendo 64 hardware and Wii Virtual Console hardware, a ROM should never go above 64 MiB *compressed*. The Nintendo 64 can theoretically handle 64 MiB ROMs; however, Wii Virtual Console can only be expanded to allow 48 MiB due to the nature of the fact the Wii itself needs memory to run the operating system and emulator at the same time. Using custom samples can eat up this data very quickly if the sample file is large enough; it is recommended to keep samples themselves to around a max of 10 KiB when possible. Emulators on PC can go well above the 64 MiB and 48 MiB limit; however, hardware compatibility is important.

    Please be mindful when releasing creations publicly that there will be more than one person using them, so it is best to show some refrain. If a song file ends up anywhere near 500 KiB, then it is likely too large. A good target to aim for would be no larger than 100 to 200 KiB.

This page details the process of converting `.wav` files into sample files compatible with *Ocarina of Time* and *Majora's Mask*.

## placeholder
One way of creating custom samples is by converting `.wav` files into `.bin` (or `.zsound`) files using the *vadpcm_enc* and *tabledesign* programs from the Nintendo 64 SDK. However, those tools must be recompiled to work on x86 architecture as they were originally built for IRIX computers using the MIPS processor. Currently, there is no active development of those tools. However, there is a tool that can be used with modern computers and processors called *z64audio*.

Unlike with N64 Soundlist Tool, to obtain all the data for the audiobank the sample(s) will be put in require(s) different tools. The process of converting a `.wav` file is much more involved and can be quite tedious compared to N64 Soundlist Tool; however, it is possible to use samples from anywhere, not just other Nintendo 64 games.

### Workflow
placeholder

## Resampling a WAV File <small>move to own page?</small> { #resampling-a-wav-file data-toc-label="Resampling a WAV File" }
placeholder

Resampling is an optional step in the process of converting a `.wav` file into a sample file. Resampling can reduce the file size of a sample file by lowering the sample rate, reducing the amount of data contained within the file. Resampling can also ensure that a sample's sample rate will match the master sample rate of *Ocarina of Time* and *Majora's Mask* and eliminate the need for sample rate correction when tuning the sample.

### Resampling using Audacity
placeholder

- Open the `.wav` file in Audacity and make sure it is currently selected.
- Click "Tracks" at the top of the Audacity window, then "Resample..." and select the desired sample rate.
- Click "Audio Setup", then "Audio Settings..." and change the "Project Sample Rate" field to 32000 Hz in the "Quality" section of the "Audio Settings" menu.
- Export the sample as a `.wav` file by clicking "File", then "Export", then "Export as WAV".
***

### Resampling using Polyphone
placeholder

## Creating a Looping Sample
placeholder

### Looping using z64Audio
placeholder

### Looping using Polyphone
placeholder

- Open Polyphone, then click "New Soundfont"
- Drag the `.wav` file into the Polyphone window.
- Left-Click anywhere on the waveform visualization to set the "Loop Start" marker, Right-Click anywhere after a "Loop Start" marker to create a "Loop End" marker.
- Once the loop markers have been set up, click the toolbox icon at the top of the Polyphone window, then click "Auto Loop" (this will adjust the loop automatically).
- Listen to the loop and adjust it as needed, undoing any changes with ++ctrl+z++ or ++cmd+z++
- Once content with how the loop sounds, export the sample as a `.wav` file by clicking the toolbox icon at the top of the Polyphone window, then click "Wav Export...".

## Pitch Shifting a Sample <small>move to own page?</small> { #pitch-shifting-a-sample data-toc-label="Pitch Shifting a Sample" }
Due to the hardware limitations of the Nintendo 64's Reality Signal Processor (RSP) being unable to pitch shift audio samples above 24 semitones and below 48 semitones from a sample's root key, a sequence or MIDI file may require a pitch higher than what can be achieved in-game. To get around this limitation, a sample can be pitch-shifted out-of-game instead to change the sample's root key.

!!! info "Audio Quality Degradation"
    When pitch-shifting a sample, there will be degradation in the quality of the audio the farther from the sample's original root key the shift is. Because of this, it is recommended to only ever increase or decrease the pitch by 12 semitones at most in either direction.

!!! info "Pitch Caps and Floors"
    The Nintendo 64 Programming Manual makes mention of the pitch cap and floor; however, it is described as having a max of 12 semitones above the sample's root key, and 24 semitones below the sample's root key. In *Ocarina of Time* and *Majora's Mask* it is the former instead of the latter described by the Nintendo 64 Programming Manual; the reason for this discrepancy is uncertain.

### Pitch Shifting using Audacity
placeholder

### Pitch Shifting using Polyphone
placeholder

- Open Polyphone, then click "New Soundfont".
- Drag the `.wav` file into the Polyphone window.
- Click the toolbox icon at the top of the Polyphone window, then click "Transpose..."
- Enter the amount of semitones to shift the sample up or down. Positive numbers increase the pitch, with negative numbers decreasing the pitch.
- Click "Okay" and Polyphone will shift the pitch of the sample; this will also adjust the sample's loop automatically as well.

## Tuning a Sample <small>move to own page?</small> { #tuning-a-sample data-toc-label="Tuning a Sample" }
placholder

### Finding the Sample's Root Key
placeholder

### Finding the Sample's Tuning Value
placeholder

## Using z64audio to Convert a WAV File
placeholder