# Overview of Custom Sample Injection

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

??? alert "A Word of Caution"
    The ROMs of *Ocarina of Time* and *Majora's Mask* have a limited file space of 64 MiB decompressed, and it becomes 32 MiB when compressed. To retain compatibility with both Nintendo 64 hardware and Wii Virtual Console hardware, a ROM should never go above 64 MiB *compressed*. The Nintendo 64 can theoretically handle 64 MiB ROMs; however, Wii Virtual Console can only be expanded to allow 48 MiB due to the nature of the fact the Wii itself needs memory to run the operating system and emulator at the same time. Using custom samples can eat up this data very quickly if the sample file is large enough; it is recommended to keep samples themselves to around a max of 10 KiB when possible. Emulators on PC can go well above the 64 MiB and 48 MiB limit; however, hardware compatibility is important.

    Please be mindful when releasing creations publicly that there will be more than one person using them, so it is best to show some refrain. If a song file ends up anywhere near 500 KiB, then it is likely too large. A good target to aim for would be no larger than 100 to 200 KiB.

This page details the basics of custom sample injection for *Ocarina of Time* and *Majora's Mask* for use with the *Ocarina of Time* and *Majora's Mask* randomizers. This page *does not* detail injecting a sample directly into the ROM without the use of the randomizer program.

!!! warning
    Custom sample injection is for creating non-vanilla sampled instruments, drums, or sound effects and assumes a creator already has a decent understanding of music creation and using custom audiobanks. This is not a beginner's guide to music creation.

## Overview
In the latest versions of the *Ocarina of Time* and *Majora's Mask* randomizers, it is possible to create brand-new instruments using non-vanilla samples by injecting them into a ROM using the randomizer. Pages related to this feature will do their best to help creators learn the process of custom sample injection. However, not everything is easy or straightforward; some information is very complex and requires a somewhat thorough explanation.

??? info "OOTMM Unsupported Files"
    At the time of writing this note, custom sample files (`.zsound` files) are unsupported by the OOTMM randomizer and will be skipped during seed generation. There will be a log of what files were skipped. This is normal.

For the sake of clarity and brevity, instruments, drums, and sound effects that use custom sample injection will all be referred to as "sampled" instruments, drums, and sound effects; vanilla instruments, drums, and sound effects will be referred to as "non-sampled" or "vanilla" instruments, drums, and sound effects. As an aside, this also applies to `.ootrs` and `.mmrs` files using sampled instruments as well; sampled songs that use sampled instruments are referred to as being "sampled" (this makes it easier for the end-user to recognize whether a song uses sampled instruments, drums, and sound effects and helps when trying to solve issues that arise with the files as well) and non-sampled songs that only use vanilla instruments, drums, and sound effects are referred to as being "non-sampled" (this is generally because a majority of songs will not be using sampled instruments, drums, and sound effects). Any mention of "samples" refers to the `.wav` and `.bin` (or `.zsound`) files being used to create a sampled instrument, drum, or sound effect.

The majority of the work for the sampled instruments, drums, and sound effects samples is making them compatible with *Ocarina of Time* and *Majora's Mask*. Once the samples are compatible with the games, the rest of the process is creating the audiobank data the sampled instrument, drum, or sound effect will use for import into a sequence's full audiobank. Making sampled instruments, drums, and sound effects can be very time-consuming, and many problems may arise when working with sampled instruments, drums, and sound effects, so do not get discouraged when failing.

??? tip "Recomendation"
    It is recommended to read through the custom sample injection wiki pages fully once while following along with the process, then going over it again as many times as needed until fully understanding the process. Should any further help be required, it is best to inquire within the [:fontawesome-brands-discord: Majora's Mask Randomizer](https://discord.gg/8qbreUM){ target="__blank" }<small>:material-open-in-new: </small> or [:fontawesome-brands-discord: Darunia's Joy](https://discord.gg/EVpd499gkS){ target="__blank" }<small>:material-open-in-new: </small> discord servers.

## Sample Injection Tools
Before getting started, below is a list of tools that are used for custom sample injection. Not every tool may be required, but it is recommended to download all the tools you need right now to save on needing to go back and forth between downloading and visiting the relevant wiki pages.

## Summary of Creating New Instruments, Drums, and Sound Effects
Before beginning, it may be beneficial to understand the general workflow for custom sample injection, as well as garner basic information on what sample files actually are. Please understand that the workflow presented here is not set in stone, it is a guideline to help creators create their own workflow that works for them; the wiki follows the presented workflow in how information and pages are structured and presented.

### Custom Sample Injection Workflow
<div class="annotate" markdown>

1. Obtain a `.wav` file to use for a sampled instrument, drum, or sound effect
    - Resample the `.wav` file to 32000 Hz (1)
    - Add or remove loop points in the `.wav` file using Polyphone or z64Audio as needed
2. Find the `.wav` file's tuning float value
    - Find the `.wav` file's root key (2)
3. Convert the `.wav` file to a `.bin` (or `.zsound`) file using the Sample Creation Tools or obtain a sample from a different Nintendo 64 game using N64 Soundlist Tool
    - Convert the sample's codebook ADPCM predictor data from `.bin` to `.xml`
    - Convert the sample's loopbook ADPCM predictor data from `.bin` to `.xml` (3)
4. Create the sampled instruments, drums, or sound effects audiobank (4)
    - Edit the splits, release rate, tuning float, and ADSR values inside the audiobank
    - Copy and paste the codebook ADPCM predictor data into `<books>`
    - Copy and paste the loopbook ADPCM predictor data into `<loops>` (5)
5. Set up the sampled instruments, drums, or sound effects unique sample address marker
    - For *Ocarina of Time* randomizer rename `*.wav.vadpcm.bin` to `*.zsound` and add `ZSOUND:*.zsound:########` to the song's `.meta` file
    - For *Majora's Mask* randomizer rename `*.wav.vadpcm.bin` to `*_########.zsound`
    - ~~Rename `*.wav.vadpcm.bin` to `*.zsound` and add `- "*.zsound": "########"` to the `samples:` section of the song's `metadata.yml` file~~ (6)
6. Test the sampled instrument, drum, or sound effect in-game to make sure it works
    - Create an `.ootrs` or `.mmrs` and test the sample using the audiobank and a test sequence in the randomizer (7)

</div>

1. Resampling is an optional step in this process, but it removes the need for any extra work in tuning a sampled instrument, drum, or sound effect.
2. Finding the root key of a sample is only required if unsure of or to reconfirm the root key for the sample.
3. If the `.wav` file does not have any loop data specified, then the Sample Creation Tools will not output a `.bin` file containing loopbook ADPCM predictor data.
4. If not using an audiobank template, then either create an audiobank from scratch or edit an existing audiobank from *Ocarina of Time* or *Majora's Mask using* SEQ64.
5. This is only required if the Sample Creation Tools output a `.bin` file containing your sample's loopbook ADPCM predictor data.
6. `metadata.yml` has not been presented to or adopted by the developers of any randomizer; however, it is a simple but effective system that will hopefully be adopted and added in the future.
7. Optionally, the sample could be injected into a decompressed ROM; however, it is much more tedious and does not ensure that the sample will not collide with other data added by the randomizer.

-----

There are a few ways to obtain samples to inject. The first way is ripping and injecting other Nintendo 64 games' sample files, and codebook & loopbook ADPCM predictor data using N64 Soundlist Tool. The second way is obtaining a soundfont (`.sf2`) that has already ripped sample files as `.wav` files and using those `.wav` files to create a sampled instrument, drum, or sound effect. The third way is to create samples using a DAW or sampling software to create a `.wav` file, then use those `.wav` files to create a sampled instrument, drum, or sound effect.

The easiest way of creating sampled instruments, drums, and sound effects is using other Nintendo 64 games' sample files, codebook & loopbook ADPCM predictor data, and other relevant data using N64 Soundlist Tool; in compairson converting a `.wav` file is much more involved and tedious.

## Summary of `.zsound` Files
The binary (`.bin`) files the randomizer recognizes as `.zsound` files are `.aiff` files that have been compressed into `.aifc` files and encoded using a switchable ADPCM algorithm created by Nintendo to allow audio files to play on the Nintendo 64 hardware.

The reason for the name `.zsound` and not `.bin` is because the binary file extension does not allow for much differentiation between different RAW files. SEQ64 also refers to sequence files (`.seq`, `.aseq`, and `.zseq`) as RAW files. If packed into an `.ootrs` or `.mmrs` file, the lack of differentiation could cause issues, so they were coined `.zsound` files by Isghj5 for use with MMR; later, when OOTR added custom sample injection, it also adopted the `.zsound` file extension as the system is based on the system MMR used at the time custom sample injection was being added. The `.zsound` files themselves are placed in the root directory of `.ootrs` and `.mmrs` files.

## Summary of ADPCM Predictors
What are known as "books" and "loops" are ADPCM codebook and loopbook prediction coefficient tables. Because the Nintendo 64 uses a switchable ADPCM compression based algorithm, it is required for the predictors to be placed inside audiobanks, which is somewhat redundant, since the predictor data is embedded in the sample files. The codebooks and loopbooks are used by `vadpcm_enc`, a Nintendo 64 audio encoding tool created by Nintendo and supplied with the Nintendo 64 SDK, when creating the compressed binary file `*.wav.vadpcm.bin` and are embedded directly into the file. Codebooks and loopbooks tell the audio engine how a sample is supposed to play.

As for ADPCM, it is a lossy audio compression format, so when being compressed some audio data is overwritten or lost completely. ADPCM compression works by separating a sample's data into different blocks, and predicting the variation of that sample's data within each block. The size of the blocks are measured in "samples"; the smallest block size is `32` samples, and the highest is `512` samples. Larger blocks allow for better compression, but at the expense of sound quality and resolution for aligning audio loop points.

Because ADPCM uses sample blocks that are aligned one after another, a `.wav` file compressed using ADPCM compression may have an unfinished, or partial, block at its end. In this case, the ADPCM decoder generates silence (1) for the remainder of this partial block.{ .annotate }

1. The silence will appear in codebooks and loopbooks as a zeroed out value, this is normal and is not a cause to be alarmed or worried that a sample has an issue.

-----