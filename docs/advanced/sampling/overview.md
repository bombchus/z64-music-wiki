# Overview of Custom Sample Injection

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

??? alert "A Word of Caution"
    The ROMs of *Ocarina of Time* and *Majora's Mask* have a limited file space of 64 MiB decompressed, and it becomes 32 MiB when compressed. To retain compatibility with both Nintendo 64 hardware and Wii Virtual Console hardware your ROM should never go above 64 MiB *compressed*. The Nintendo 64 can theoretically handle 64 MiB ROMs, however Wii Virtual Console can only be expanded to allow 48 MiB due to the nature of the fact the Wii itself needs memory to run the operating system and emulator at the same time. Using custom samples can eat up this data very quickly if you sample file is large enough; it is recommended to keep samples themselves to around a max of 10 KiB when possible. Emulators on PC can go well above the 64 MiB and 48 MiB limit, however hardware compatibility is important.

    Please be mindful that if you are releasing your creations publicly that you will not be the only person using them, so it is best to show some refrain. If you song file ends up anywhere near 500 KiB then it is likely too large, a good target to aim for would be no larger than 100 to 200 KiB.

This page details the basics of custom sample injection for *Ocarina of Time* and *Majora's Mask* for use with the *Ocarina of Time* and *Majora's Mask* randomizers. This page *does not* detail injecting a sample directly into the ROM without the use of the randomizer program.

!!! warning
    Custom sample injection is for creating non-vanilla sampled instruments, drums, or sound effects and assumes you already have a decent understanding of music creation and custom audiobanks, this is not a beginner's guide to music creation.

    Please only continue with this guide if you are comfortable using custom audiobanks and dealing with a great deal of trial and error.

## Overview
In the latest version of the *Ocarina of Time* and *Majora's Mask* randomizers it's possible to create brand new instruments using non-vanilla samples by injecting it into the ROM using the randomizer. Pages related to this feature will do their best to help you through the process of custom sample injection, however, not everything is easy or straightforward; some information is very complex and requires a somewhat thorough explanation.

??? info "OOTMM Unsupported Files"
    At the time of writing this note custom sample files (`.zsound` files) are unsupported by the OOTMM randomizer and will be skipped during seed generation. There will be a log of what files were skipped, this is normal.

For the sake of clarity and brevity instruments, drums, and sound effects that use custom sample injection will all be referred to as "sampled" instruments, drums, and sound effects; vanilla instruments, drums, and sound effects will be reffered to as "non-sampled" or "vanilla" instruments, drums, and sound effects. As an aside, this also applies to `.ootrs` and `.mmrs` files using sampled instruments as well; sampled songs that use sampled instruments are referred to as being "sampled" (this makes it easier for the end-user to recognize whether or not a song uses sampled instruments, drums, and sound effects and helps when trying to solve issues that arise with the files as well) and non-sampled songs that only use vanilla instruments, drums, and sound effects are reffered to as being "non-sampled" (this is generally because a majority of songs will not be using sampled instruments, drums, and sound effects). Any mention of "samples" refers to the `.wav` and `.bin` (or `.zsound`) files you are using to create your sampled instrument, drum, or sound effect with.

The majority of the work for sampled instrument's, drum's, and sound effect's samples is making them compatible with *Ocarina of Time* and *Majora's Mask*, once the samples are compatible with the games the rest of the process is creating the audiobank data your sampled instrument, drum, or sound effect will use for import into your sequence's full audiobank. Making sampled instruments, drums, and sound effects can be very time consuming, and you will run into problems when working with sampled instruments, drums, and sound effects so do not get discouraged if you fail.

??? tip "Recomendation"
    It is recommended that you read through the custom sample injection wiki pages fully once while following along with the process, then going over it again as many times as needed until you fully understand the process. Should you require any further help it's best to inquire within the [:fontawesome-brands-discord: MMR](https://discord.gg/8qbreUM) or [:fontawesome-brands-discord: Darunia's Joy](https://discord.gg/EVpd499gkS) discord servers.

## Sample Injection Tools
Before getting started, below is a list of tools that are used for custom sample injection, not every tool may be required, but it is recommended to download all the rools you need right now to save on needing to go back and forth between downloading and visiting the relevant wiki pages.

### Link to Tools
- **[Sample Creation Tools](#){ target="_blank" }** <small> :material-open-in-new: </small>
- **[N64 Soundlist Tool](https://github.com/jombo23/N64-Tools){ target="_blank" }** <small> :material-open-in-new: </small>
- **[Polyphone](https://www.polyphone-soundfonts.com/download){ target="_blank" }** <small> :material-open-in-new: </small> <small>recommended</small>
- **[Audacity](https://www.audacityteam.org/download/){ target="_blank" }** <small> :material-open-in-new: </small>
- **[Z64 Tuning Calculator](#){ target="_blank" }** <small> :material-open-in-new: </small> <small>v2024.07.07</small>
- **[Z64 ADSR Converter](#){ target="_blank" }** <small> :material-open-in-new: </small> <small>v2024.07.07</small>
- **[Audiobank Templates](#){ target="_blank" }** <small> :material-open-in-new: </small> <small>recommended</small>

#### Brief Summary of Tools
=== "Sample Creation Tools"
    The **Sample Creation Tools** created by Isghj5, and edited by others, are required for converting `.wav` files to `.bin` (or `.zsound`) sample files and obtaining codebook and loopbook ADPCM predictor data.

=== "N64 Soundlist Tool"
    **N64 Soundlist Tool** is required for ripping `.bin` (or `.zsound`) sample files and obtaining codebook and loopbook ADPCM predictor data (as well as other instrument, drum, and sound effect data) from Nintendo 64 games.

=== "Polyphone"
    **Polyphone** is *optional*, but required for exporting `.wav` files from `.sf2` (soundfont) files; this is used in conjunction with the "Sample Creation Tools" to convert `.wav` files to `.bin` (or `.zsound`) sample files and to obtain codebook and loopbook ADPCM predictor data. You can also use Polyphone for other sample editing, before converting, as well.

=== "Audacity"
    **Audacity** is *optional*, but extremely useful for resampling `.wav` files as well as sample editing, before converting, as well.

=== "Tuning Calculator"
    The **Tuning Calculator** is *optional*, but extremely useful for tuning your sampled instrument, drum, or sound effect.

=== "ADSR Converter"
    The **ADSR Converter** is *optional*, but can be useful for helping convert `.sf2` envelopes into envelope data compatible with Ocarina of Time and Majora's Mask.

=== "Audiobank Templates"
    The **Audiobank Templates** are *optional*, but are made specifically for the creation of sampled instruments, drums, and sound effects and can be edited in SEQ64 or a text editor capable of editing `.xml` files. The Audiobank Templates contain placeholder data to be edited specifically for either instruments, drums, or sound effects.

    ??? tip "Recommendation"
        It is recommended to avoid using SEQ64 to edit audiobanks and instead use a text editor capable of editing `.xml` files. There's a learning curve, however it will bypass any bugs that SEQ64 introduces.

-----

## Summary of Creating New Instruments, Drums, and Sound Effects
Before beginning, it may be beneficial to understand the general workflow for custom sample injection, as well as garner basic information on what sample files actually are. Please understand that the workflow presented here is not set in stone, it is a guideline to help you create your own workflow that works for you; the wiki follows the presented workflow in how information and pages are structured and presented.

### Custom Sample Injection Workflow
<div class="annotate" markdown>

1. Obtain a `.wav` file your will use for your sampled instrument, drum, or sound effect
    - Resample your `.wav` file to 32000 Hz (1)
    - Add or remove loop points to the `.wav` file using Polyphone or z64Audio as needed
2. Find your `.wav` file's tuning float value
    - Find your `.wav` file's root key (2)
3. Convert your `.wav` file to a `.bin` (or `.zsound`) file using the Sample Creation Tools or obtain a sample from a different Nintendo 64 game using N64 Soundlist Tool
    - Convert your codebook ADPCM predictor data from `.bin` to `.xml`
    - Convert your loopbook ADPCM predictor data from `.bin` to `.xml` (3)
4. Create your sampled instrument's, drum's, or sound effect's audiobank (4)
    - Edit the splits, release rate, tuning float, and ADSR values in the audiobank
    - Copy and paste your codebook ADPCM predictor data into `<books>`
    - Copy and paste your loopbook ADPCM predictor data into `<loops>` (5)
5. Set up your sampled instrument's, drum's, or sound effect's unique sample address marker
    - For *Ocarina of Time* randomizer rename `*.wav.vadpcm.bin` to `*.zsound` and add `ZSOUND:*.zsound:########` to your `.meta` file
    - For *Majora's Mask* randomizer rename `*.wav.vadpcm.bin` to `*_########.zsound`
    - ~~Rename `*.wav.vadpcm.bin` to `*.zsound` and add `- "*.zsound": "########"` to the `samples:` section of your `metadata.yml` file~~ (6)
6. Test your sampled instrument, drum, or sound effect in-game to make sure it works
    - Create an `.ootrs` or `.mmrs` and test your sample using the audiobank and a test sequence in the randomizer (7)

</div>

1. Resampling is an optional step in this process, but it removes the need for any extra work in tuning your sampled instrument, drum, or sound effect.
2. Finding the root key of your sample is only required if you are unsure of or want to reconfirm the root key for you sample.
3. If your `.wav` file does not have any loop data specified then the Sample Creation Tools will not output a `.bin` file containing loopbook ADPCM predictor data.
4. If you are not using an audiobank template, then you will need to either create an audiobank from scratch or edit an existing audiobank from *Ocarina of Time* or *Majora's Mask using* SEQ64.
5. This is only required if the Sample Creation Tools output a `.bin` file containing your sample's loopbook ADPCM predictor data.
6. `metadata.yml` has not been presented to or adopted by the developers of any randomizer, however it is a simple but effective system that will hopefully be adopted and added in the future.
7. Optionally, you could inject the sample onto a decompressed ROM, however it is much more tedious and doesn't ensure that the sample will not collide with other data added by the randomizer.

-----

There are a few ways to obtain samples to inject, the first way is ripping and injecting other Nintendo 64 games' sample files, and codebook & loopbook ADPCM predictor data using N64 Soundlist Tool. The second way is obtaining a soundfont (`.sf2`) that has already ripped sample files as `.wav` files and using those `.wav` files to create your sampled instrument, drum, or sound effect. The third way is to create your own samples using a DAW or sampling software to create a `.wav` file then using those `.wav` files to create your sampled instrument, drum, or sound effect.

The easiest way of creating sampled instruments, drums, and sound effects is using other Nintendo 64 games' sample files, codebook & loopbook ADPCM predictor data, and other relevant data using N64 Soundlist Tool; converting a `.wav` file is much more involved and tedious in comparison.

## Summary of `.zsound` Files
The binary (`.bin`) files the radnomzier recognizes as `.zsound` files are `.aiff` files that have been compressed into `.aifc` files and encoded using a switchable ADPCM algorithm created by Nintendo to allow audio files to play on the Nintendo 64 hardware.

The reason for the name `.zsound` and not `.bin` is because the binary file extension doesn't allow for much differentiation between different RAW files. SEQ64 also refers to sequence files (`.seq`, `.aseq`, and `.zseq`) as RAW files. If packed into an `.ootrs` or `.mmrs` file the lack of differentiation could cause issues so they were coined `.zsound` files by Isghj5 for use with MMR; later when OOTR added custom sample injection they also adopted the `.zsound` file extension as the system was based on the system MMR used at the time they were adding custom sample injection. The files themselves are placed in the root directory of `.ootrs` and `.mmrs` files.

## Summary of ADPCM Predictors
What are known as "books" and "loops" are ADPCM codebook and loopbook prediction coefficient tables. Since the Nintendo 64 uses a switchable ADPCM compression based algorithm they are required by audiobanks which is somewhat redundant since they are embedded in the sample files themselves. The codebooks and loopbooks are used by `vadpcm_enc`, a Nintendo 64 audio encoding tool created by Nintendo and supplied with the Nintendo 64 SDK, when creating the compressed binary file `*.wav.vadpcm.bin` and are embedded directly into the file. Codebooks and loopbooks in the most basic sense tell the audio engine how the sample is supposed to play.

As for ADPCM itself, it is a lossy audio compression format, so when being compressed some audio data is overwritten or lost completely. ADPCM compression works by separating the sample's data into different blocks, and predicting the variation of the sample's data within each block. The size of the blocks are measured in "samples"; the smallest bloock size is `32` samples, and the highest is `512` samples. Larger blocks allow for better compression, but it is at the expense of sound quality and resolution for aligning audio loop points.

Because ADPCM uses sample blocks that are aligned one after another, a `.wav` file compressed using ADPCM compression may have an unfinished, or partial, block at its end. In this case, the ADPCM decoder generates silence (1) for the remainder of this partial block.
{ .annotate }

1. The silence will appear in codebooks and loopbooks as a zeroed out value, this is normal and is not a cause to be alarmed or worried that your sample has an issue.

-----