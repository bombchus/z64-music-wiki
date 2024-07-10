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
    **SEQ64** is a tool created for making music sequences for first-party Nintendo 64 games (games made by Nintendo EAD/SRD). It is capable of converting `.mid`, `.com`, and `.mus` files into the sequence files used in Ocarina of Time and Majora's Mask and vice versa. SEQ64 versions 1.0 and 1.5 have the ability to edit audiobank files as well.  The ability to edit audiobanks is not available in version 2.0 and above.

    !!! info "SEQ64 versions 1.0 and 1.5"
        For all intents and purposes, there are no differences in the main functionality of SEQ64 version 1.0 and version 1.5. However, SEQ64 version 1.0 has a light theme, and SEQ64 version 1.5 has a dark theme.

=== "ROM Description"
    The **ROM Description** is a data file containing music sequence format definitions, audiobank binary format definitions, addresses of key files and tables, and general program settings for SEQ64. The ABI data file (which only contains sequence format definitions) succeeded ROM description files for SEQ64 version 2.0 and above. The ROM descriptions provided with SEQ64 versions 1.0 and 1.5 are very old and contain less information as well as less accurate information. The ROM descriptions linked above are up-to-date and contain more information as well as more accurate information.

=== "Digital Audio Workstation"
    **Digital Audio Workstations**, or **DAW(s)** for short, are where you create or edit conventional music files. For the purposes of creating music for *Ocarina of Time* and *Majora's Mask* you need a DAW that is capable of creating and editing `.mid` files. The DAWs linked above are the most common DAWs used within the randomizer communities.
    
    Sekaiju is not a DAW, it is a MIDI sequencer; it lacks many of the standard audio features a regular DAW may have.

=== "Soundfont"
    **Soundfont(s)** will allow previewing of a song with the instruments the games use when using a DAW capable of music playback with a soundfont. This allows for quick changes to the music before conversion. The soundfonts do not sound exactly like in-game instruments sound. However, they are close enough to give a good idea of how a song will sound in-game.

=== "N64 Emulator"
    An **N64 Emulator** is used to preview music in-game. This is to make sure there are no problems with the sequence or audiobank in-game. The emulators Simple64, Rosalie's Mupen GUI, and Project64 are all standalone. Ares is a multi-system emulator. It is recommended to *avoid* RetroArch and other multi-system emulators and frontends.

=== "nDEC"
    **nDEC** decompresses a ROM so that it can be edited with SEQ64. Included in the nDEC download is a batch script that makes using nDEC simple. For more detailed instructions on how to decompress a ROM with nDEC, there is a section on the [ROM requirements](../requirements/#decompressing-a-rom){ target="__blank" }<small>:material-open-in-new: </small> page of the wiki detailing the process.

-----

### Links to Advanced Tools
- #### **Sample Creation Tools**
    - **[z64audio](../assets/tools/z64audio%20with%20CLI%20Script.zip){ target="_blank" }** <small> :material-open-in-new: </small>
    - **[ADPCM Predictor Conversion Scripts](../assets/tools/ADPCM%20Predictor%20BIN%20to%20XML.zip){ target="_blank" }** <small> :material-open-in-new: </small>`xml output`
    - **[ADPCM Predictor Conversion Scripts](../assets/tools/ADPCM%20Predictor%20BIN%20to%20C.zip){ target="_blank" }** <small> :material-open-in-new: </small>`c output`
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
    The **Sample Creation Tools** are required for converting `.wav` files to `.bin` (or `.zsound`) sample files and obtaining codebook and loopbook ADPCM predictor data.

=== "N64 Soundlist Tool"
    **N64 Soundlist Tool** is used to rip `.bin` (or `.zsound`) sample files and obtain their codebook and loopbook ADPCM predictor data—as well as other instrument, drum, and sound effect data—from Nintendo 64 games.

=== "Polyphone"
    **Polyphone** is *optional*, but can be used to obtain `.wav` files from `.sf2` (soundfont) files to convert into a `.bin` (`.zsound`) file with the "Sample Creation Tools". Polyphone can also edit `.wav` files in a few different ways, such as resampling, pitch-shifting, or setting loop points.

=== "Audacity"
    **Audacity** is *optional*, but is a powerful audio editing tool. Audacity can edit audio files in many different ways, such as resampling, pitch-shifting, or trimming unneeded portions of audio.

=== "Tuning Float Calculator"
    The **Tuning Float Calculator** is *optional*, but it can find the tuning float value for a sampled instrument, drum, or sound effect. The tuning float value for samples goes inside of an audiobank and adjusts the tuning of a sample.

    !!! warning "Windows Defender False Flagging"
        Because the Tuning Float Calculator is an unsigned executable file, Windows Defender may false flag it as malware (`Trojan:Win32/Wacatac.B!ml`). To remedy this, follow the steps below:

        > 1. Open Windows Defender and navigate to "Virus & threat protection".
        > 2. In "Virus & threat protection", navigate to "Virus & threat protection settings > Manage settings".
        > 3. In "Virus & threat protection settings", navigate to "Exclusions > Add or remove exclusions".
        > 4. In "Exclusions", click the "+ Add an exclusion" button and locate the file or the folder the file is in to exclude.

        It is not recommended to exclude an entire folder unless everything related to Music Creation is being kept in a single folder. Whenever possible, always exclude single files you can trust. The application does not contain any malicious code. If that statement is untrustworthy, then do not download it. And if it is already downloaded, then do not add a Windows Defender exclusion for it.

=== "ADSR Converter"
    The ADSR Converter is optional, but it can convert a soundfont's (`.sf2`) ADSR data into ADSR data compatible with Ocarina of Time and Majora's Mask.

    !!! warning "Windows Defender False Flagging"
        Because the Tuning Float Calculator is an unsigned executable file, Windows Defender may false flag it as malware (`Trojan:Win32/Wacatac.B!ml`). To remedy this, follow the steps below:

        > 1. Open Windows Defender and navigate to "Virus & threat protection".
        > 2. In "Virus & threat protection", navigate to "Virus & threat protection settings > Manage settings".
        > 3. In "Virus & threat protection settings", navigate to "Exclusions > Add or remove exclusions".
        > 4. In "Exclusions", click the "+ Add an exclusion" button and locate the file or the folder the file is in to exclude.

        It is not recommended to exclude an entire folder unless everything related to Music Creation is being kept in a single folder. Whenever possible, always exclude single files you can trust. The application does not contain any malicious code. If that statement is untrustworthy, then do not download it. And if it is already downloaded, then do not add a Windows Defender exclusion for it.

=== "Audiobank Templates"
    The **Audiobank Templates** are *optional*, and made for the creation of sampled instruments, drums, and sound effects. SEQ64 or a text editor capable of opening and editing `.xml` files can edit the placeholder data in the template files. There are templates available for instruments, drums, or sound effects.

    ??? tip "Recommendation"
        SEQ64 is not recommended for audiobank editing, a text editor capable of editing `.xml` files is instead recommended. There is a learning curve to editing audiobank `.xml` files. However, editing audiobanks in a text editor will bypass any bugs that SEQ64 can introduce during editing.

-----

## Obtaining a ROM
Along with the tools above, you will need to obtain a ROM of the game you wish to create custom music for. Sharing ROM files is illegal as the files are copyrighted by Nintendo, so this wiki cannot share links to any websites containing the ROM files. MD5 and CRC32 values are useful for checking to make sure your ROM is the correct version and does not contain any errors. You can find them on the [ROM requirements](../requirements){ target="_blank" }<small>:material-open-in-new: </small> page of the wiki.

!!! info "Dumping ROMs"
    If you have the capability, it is best to dump the ROM yourself from hardware, however, all Virtual Console and Nintendo Switch Online versions of *Ocarina of Time* are version 1.2 and not version 1.0; for *The Legend of Zelda: Collector's Edition* the ROM files for *Ocarina of Time* and *Majora's Mask* are ROMs that were compiled specifically for *The Legend of Zelda: Collector's Edition* and cannot be used at all.

-----
