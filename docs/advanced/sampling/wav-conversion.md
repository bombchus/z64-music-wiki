# Creating Sample Data by Converting WAV Files

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

??? alert "A Word of Caution"
    The ROMs of *Ocarina of Time* and *Majora's Mask* have a limited file space of 64 MiB decompressed, and it becomes 32 MiB when compressed. To retain compatibility with both Nintendo 64 hardware and Wii Virtual Console hardware your ROM should never go above 64 MiB *compressed*. The Nintendo 64 can theoretically handle 64 MiB ROMs, however Wii Virtual Console can only be expanded to allow 48 MiB due to the nature of the fact the Wii itself needs memory to run the operating system and emulator at the same time. Using custom samples can eat up this data very quickly if you sample file is large enough; it is recommended to keep samples themselves to around a max of 10 KiB when possible. Emulators on PC can go well above the 64 MiB and 48 MiB limit, however hardware compatibility is important.

    Please be mindful that if you are releasing your creations publicly that you will not be the only person using them, so it is best to show some refrain. If you song file ends up anywhere near 500 KiB then it is likely too large, a good target to aim for would be no larger than 100 to 200 KiB.

This page details the process of converting `.wav` files into sample files compatible with *Ocarina of Time* and *Majora's Mask*.

## placeholder
One way of creating custom samples is by converting `.wav` files into `.bin` (or `.zsound`) files using the *vadpcm_enc* and *tabledesign* programs from the Nintendo 64 SDK, however those tools must be recompiled to work on x86 architecture as they were originally build for IRIX computers using the MIPS processor. Currently there is no active development for those tools, however there is a tool you can use with modern computers and processors called *z64audio*.

Unlike with N64 Soundlist Tool, obtaining all the data for the audiobank you will put the sample(s) in require different tools. The process of converting a `.wav` file is much more involved and can be quite tedious compared to N64 Soundlist Tool; however you can use samples from anywhere, not just other Nintendo 64 games.

### Workflow
placeholder

## Resampling a WAV File
placeholder

## Creating a Looping Sample
placeholder

### Looping using Polyphone
placeholder

### Looping using z64audio

## Tuning a Sample
placholder

### Finding the Sample's Root Key
placeholder

### Finding the Sample's Tuning Value
placeholder

## Using z64audio to Convert a WAV File
placeholder