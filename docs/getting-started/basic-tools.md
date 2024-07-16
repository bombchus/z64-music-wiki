# Basic Tools and Resources

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

This page is where download links to the basic tools and resources used in custom music creation for *Ocarina of Time* and *Majora's Mask* are available.

!!! alert "Procuring a ROM"
    This page, as well as the wiki itself, can not and will not supply any ROM files or links to any ROM files for *Ocarina of Time* and *Majora's Mask* as it is illegal to do so. This wiki is not meant for piracy of copyrighted materials, it is meant to help those interested in creating custom music for *Ocarina of Time* and *Majora's Mask* learn the process and other details related to music creation for the games.

## Basic Custom Music Creation Tools
Below is a list of tools that are used for creating music for *Ocarina of Time* and *Majora's Mask*. It is recommended to download all the tools needed right now to save on needing to go back and forth between downloading and visiting the relevant wiki pages.

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
    - **[FL Studio](https://www.image-line.com/fl-studio-download/){ target="_blank" }**<small> :material-open-in-new: </small>
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

### Brief Summary of Tools
=== "SEQ64"
    **SEQ64** is a tool created for making music sequences for first-party Nintendo 64 games (games made by Nintendo EAD/SRD). It is capable of converting `.mid`, `.com`, and `.mus` files into the sequence files used in Ocarina of Time and Majora's Mask and vice versa. SEQ64 versions 1.0 and 1.5 have the ability to edit audiobank files as well.  The ability to edit audiobanks is not available in version 2.0 and above.

    !!! info "SEQ64 versions 1.0 and 1.5"
        For all intents and purposes, there are no differences in the main functionality of SEQ64 version 1.0 and version 1.5. However, SEQ64 version 1.0 has a light theme, and SEQ64 version 1.5 has a dark theme.

=== "ROM Description"
    The **ROM Description** is a data file containing music sequence format definitions, audiobank binary format definitions, addresses of key files and tables, and general program settings for SEQ64. The ABI data file (which only contains sequence format definitions) succeeded ROM description files for SEQ64 version 2.0 and above. The ROM descriptions provided with SEQ64 versions 1.0 and 1.5 are very old and contain less information as well as less accurate information. The ROM descriptions linked above are up-to-date and contain more information as well as more accurate information.

=== "Digital Audio Workstation"
    **Digital Audio Workstations**, or **DAW(s)** for short, are where conventional music files are created or edited. For the purposes of creating music for *Ocarina of Time* and *Majora's Mask* a DAW that is capable of creating and editing `.mid` files is needed. The DAWs linked above are the most common DAWs used within the randomizer communities.
    
    Sekaiju is not a DAW, it is a MIDI sequencer; it lacks many of the standard audio features a regular DAW may have.

=== "Soundfont"
    **Soundfont(s)** will allow previewing of a song with the instruments the games use when using a DAW capable of music playback with a soundfont. This allows for quick changes to the music before conversion. The soundfonts do not sound exactly like in-game instruments sound. However, they are close enough to give a good idea of how a song will sound in-game.

=== "N64 Emulator"
    An **N64 Emulator** is used to preview music in-game. This is to make sure there are no problems with the sequence or audiobank in-game. The emulators Simple64, Rosalie's Mupen GUI, and Project64 are all standalone. Ares is a multi-system emulator. It is recommended to *avoid* RetroArch and other multi-system emulators and frontends.

=== "nDEC"
    **nDEC** decompresses a ROM so that it can be edited with SEQ64. Included in the nDEC download is a batch script that makes using nDEC simple. For more detailed instructions on how to decompress a ROM with nDEC, there is a section on the [ROM requirements](../requirements/#decompressing-a-rom){ target="__blank" }<small>:material-open-in-new: </small> page of the wiki detailing the process.

-----