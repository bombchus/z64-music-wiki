# Custom Music Creation Tools and Resources

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

<style>
  .md-typeset h5 {
    font-size: .7rem;
    color: var(--md-typeset-color);
    margin: 0;
    text-transform: none;
  }
</style>

This page is where you will find links to the various tools and resources used in custom music creation for *Ocarina of Time* and *Majora's Mask*.

!!! alert "Warning"
    This page, as well as the wiki itself, can not and will not supply you with any ROM files or links to any ROM files for *Ocarina of Time* and *Majora's Mask* as it is illegal to do so. This wiki is not meant for piracy of copyrighted materials, it is meant to help those interested in creating custom music for *Ocarina of Time* and *Majora's Mask* learn the process and other details related to music creation for the games.

## Custom Music Creation Tools
Below is a list of tools that are used for creating music for *Ocarina of Time* and *Majora's Mask*. It is recommended to download all the tools you need right now to save on needing to go back and forth between downloading and visiting the relevant wiki pages.

### Links to Basic Tools
- ##### **SEQ64**
    - **[v1.0.0](https://github.com/sauraen/seq64/releases/tag/V1.0){ target="_blank" }**<small> :material-open-in-new: </small><small>required for audiobank editing</small>
    - **[v1.5.0](https://github.com/sauraen/seq64/releases/tag/V1.5){ target="_blank" }**<small> :material-open-in-new: </small><small>required for audiobank editing</small>
    - **[v2.3.2](https://github.com/sauraen/seq64/releases/tag/2.3.2){ target="_blank" }**<small> :material-open-in-new: </small><small>recommended for sequence converting</small>
- ##### **ROM Description**
    - *Ocarina of Time* `ntsc-u` `v1.0`
        - **[ROM Description](#)**<small> :material-open-in-new: </small><small>v2024.02.25</small>
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`gm sample naming` <small>v20YY.MM.DD</small>
    - *Majora's Mask* `ntsc-u` `v1.0`
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`stable` <small>v2024.02.25</small>
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`experimental` <small>v2024.04.10</small>
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`experimental` `gm sample naming` <small>v20YY.MM.DD</small>
- ##### **SEQ64 ABI File**
    - **[Zelda ABI](#)**<small> :material-open-in-new: </small><small>±2 semitone pitch bend scale</small>
    - **[Zelda ABI](#)**<small> :material-open-in-new: </small><small>±12 semitone pitch bend scale</small>
- ##### **MIDI Capable Digital Audio Workstation**
    - **[Fruity Loops Studio](https://www.image-line.com/fl-studio-download/){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[Sekaiju](https://openmidiproject.opal.ne.jp/Sekaiju_en.html){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[REAPER](https://www.reaper.fm/download.php){ target="_blank" }**<small> :material-open-in-new: </small>
- ##### **Soundfont Files**
    - **[Ocarina of Time Soundfont](#)**<small> :material-open-in-new: </small><small>v2023.11.09</small>
    - **[Majora's Mask Soundfont](#)**<small> :material-open-in-new: </small><small>v2024.02.20</small>
- ##### **Nintendo 64 Emulator**
    - **[Simple64](https://github.com/simple64/simple64/releases){ target="_blank" }**<small> :material-open-in-new: </small><small>recommended</small>
    - **[Rosalie's Mupen GUI](https://github.com/Rosalie241/RMG/releases){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[ares](https://github.com/ares-emulator/ares/releases){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[Project64](https://www.pj64-emu.com/public-releases){ target="_blank" }**<small> :material-open-in-new: </small>
- ##### **ROM Decompression Tool**
    - **[nDEC](../assets/tools/nDEC.zip){ target="__blank" }**

#### Brief Summary of Tools
=== "SEQ64"
    **SEQ64** is a tool created for making music sequences for first-party Nintendo 64 games (games made by Nntendo EAD/SRD). It has the capability of converting `.mid`, `.com`, and `.mus` files into sequences and vice versa; for versions 1.0 and 1.5 it has the ability to edit audiobank files as well, though this feature was removed for versions 2.0 and above due to ongoing decompilation of various Nintendo 64 games.

    !!! info "SEQ64 v1.0 versus v1.5"
        For all intents and purposes there are no differences in the main functionality of SEQ64 version 1.0 and version 1.5, they are functionally identical, however SEQ64 version 1.0 has a light theme, and SEQ64 version 1.5 has a dark theme.

=== "ROM Description"
    The **ROM Description** is a data file containing music sequence format definition, audiobank binary format definition, addresses of key files and tables, and general program settings. This data file has been succeeded by the ABI data file for SEQ64 version 2.0 and above which only contains the music sequence format definition. The ROM descriptions provided with SEQ64 are very old, however the ROM descriptions linked to above have been updated to contain more information as well as more accurate information.

=== "Digital Audio Workstation"
    **Digital Audio Workstations**, or **DAW** for short, are where you create or edit conventional music files. For the purposes of creating music for *Ocarina of Time* and *Majora's Mask* you need a DAW that is capable of creating and editing `.mid` files. The DAWs linked above are the most common DAWs used within the randomizer communities.

=== "Soundfont"
    The **Soundfont** will allow you to preview your music similar to how it would sound in-game using a DAW capable of music playback with a soundfont allowing you to easily modify your music before you convert it. The soundfonts do not sound exactly like how in-game sounds will sound, however it is close enough to give you a good idea of how it will sound.

=== "N64 Emulator"
    An **N64 Emulator** is used to preview your music in-game, this will allow you to make sure there are no problems with the sequence or audiobank in-game. The emulators linked above are mostly standalone Nintendo 64 emulators, with only ares being a multi-system emulator. It is recommended to *avoid* RetroArch and other multi-system emulators and frontends.

=== "nDEC"
    **nDEC** is used to decompress your ROM so that you are able to edit it in SEQ64. nDEC is simple enough to use as there is a file bundled with the program in the link provided that does all the work for you. Should you need detailed instructions on how to decompress your ROM you can find them on the ROM requirements page of the wiki.

-----

### Links to Advanced Tools
- #### **Sample Creation Tools**
    - **[z64audio](#){ target="_blank" }** <small> :material-open-in-new: </small>
    - **[ADPCM Predictor Conversion Scripts](#){ target="_blank" }** <small> :material-open-in-new: </small>`xml output`
    - **[ADPCM Predictor Conversion Scripts](#){ target="_blank" }** <small> :material-open-in-new: </small>`c output`
- #### **N64 Soundlist Tool**
    - **[N64 Soundlist Tool](https://github.com/jombo23/N64-Tools){ target="_blank" }** <small> :material-open-in-new: </small>
- #### **Audio Editing Tools**
    - **[Polyphone](https://www.polyphone-soundfonts.com/download){ target="_blank" }** <small> :material-open-in-new: </small> <small>recommended</small>
    - **[Audacity](https://www.audacityteam.org/download/){ target="_blank" }** <small> :material-open-in-new: </small>
- #### **Tuning Float Calculator**
    - **[Tuning Float Calculator](../assets/tools/Tuning%20Float%20Calculator.zip){ target="_blank" }** <small>v2024.07.07</small>
- #### **ADSR Converter**
    - **[Z64 ADSR Converter](../assets/tools/ADSR%20Converter.zip){ target="_blank" }** <small>v2024.07.07</small>
- #### **Audiobank Templates**
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

=== "Tuning Float Calculator"
    The **Tuning Float Calculator** is *optional*, but extremely useful for tuning your sampled instrument, drum, or sound effect.

    !!! warning "Windows Defender False Flagging"
        Due to the Tuning Float Caclulator being an unsigned executable file Windows Defender will falsely flag the application as a threat. To remedy this, follow the steps below:

        > 1. Open Windows Defender and navigate to "Virus & threat protection".
        > 2. In "Virus & threat protection" navigate to "Virus & threat protection settings > Manage settings".
        > 3. In "Virus & threat protection settings" navigate to "Exclusions > Add or remove exclusions".
        > 4. In "Exclusions" click the "+ Add an exclusion" button and locate the file or the folder the file is in to exclude.

        It is not recommended to exclude an entire folder unless you keep everything pertaining to Music Creation in the same folder; whenever possible always exclude single files for you and your computer's safety.

=== "ADSR Converter"
    The **ADSR Converter** is *optional*, but can be useful for helping convert `.sf2` envelopes into envelope data compatible with Ocarina of Time and Majora's Mask.

=== "Audiobank Templates"
    The **Audiobank Templates** are *optional*, but are made specifically for the creation of sampled instruments, drums, and sound effects and can be edited in SEQ64 or a text editor capable of editing `.xml` files. The Audiobank Templates contain placeholder data to be edited specifically for either instruments, drums, or sound effects.

    ??? tip "Recommendation"
        It is recommended to avoid using SEQ64 to edit audiobanks and instead use a text editor capable of editing `.xml` files. There is a learning curve, however it will bypass any bugs that SEQ64 introduces.

-----

## Obtaining a ROM
Along with the tools above, you will need to obtain a ROM of the game you wish to create custom music for. Sharing ROM files is illegal as the files are copyrighted by Nintendo, so this wiki cannot share links to any websites containing the ROM files. MD5 and CRC32 values are useful for checking to make sure your ROM is the correct version and does not contain any errors. You can find them on the [ROM requirements](../requirements){ target="_blank" }<small>:material-open-in-new: </small> page of the wiki.

!!! info "Dumping ROMs"
    If you have the capability, it is best to dump the ROM yourself from hardware, however all Virtual Console and Nintendo Switch Online versions of *Ocarina of Time* are version 1.2 and not version 1.0; for *The Legend of Zelda: Collector's Edition* the ROM files for *Ocarina of Time* and *Majora's Mask* are ROMs that were compiled specifically for *The Legend of Zelda: Collector's Edition* and cannot be used at all.

-----
