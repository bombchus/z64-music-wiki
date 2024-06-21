# Custom Music Creation Tools and Resources

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
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

### Link to Tools
- ##### **SEQ64**
    - **[v1.0.0](https://github.com/sauraen/seq64/releases/tag/V1.0){ target="_blank" }**<small> :material-open-in-new: </small><small>required for audiobank editing</small>
    - **[v1.5.0](https://github.com/sauraen/seq64/releases/tag/V1.5){ target="_blank" }**<small> :material-open-in-new: </small><small>required for audiobank editing</small>
    - **[v2.3.2](https://github.com/sauraen/seq64/releases/tag/2.3.2){ target="_blank" }**<small> :material-open-in-new: </small><small>recommended for sequence converting</small>
- ##### **ROM Description**
    - *Ocarina of Time* `ntsc-u` `v1.0`
        - **[ROM Description](#)**<small> :material-open-in-new: </small><small>v2.25.2024</small>
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`gm sample naming` <small>vX.XX.20XX</small>
    - *Majora's Mask* `ntsc-u` `v1.0`
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`stable` <small>v2.25.2024</small>
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`experimental` <small>v4.10.2024</small>
        - **[ROM Description](#)**<small> :material-open-in-new: </small>`experimental` `gm sample naming` <small>vX.XX.20XX</small>
- ##### **SEQ64 ABI File**
    - **[Zelda ABI](#)**<small> :material-open-in-new: </small><small>±2 semitone pitch bend scale</small>
    - **[Zelda ABI](#)**<small> :material-open-in-new: </small><small>±12 semitone pitch bend scale</small>
- ##### **MIDI Capable Digital Audio Workstation**
    - **[Fruity Loops Studio](https://www.image-line.com/fl-studio-download/){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[Sekaiju](https://openmidiproject.opal.ne.jp/Sekaiju_en.html){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[REAPER](https://www.reaper.fm/download.php){ target="_blank" }**<small> :material-open-in-new: </small>
- ##### **Soundfont Files**
    - **[Ocarina of Time Soundfont](#)**<small> :material-open-in-new: </small><small>v11.9.2023</small>
    - **[Majora's Mask Soundfont](#)**<small> :material-open-in-new: </small><small>v2.20.2024</small>
- ##### **Nintendo 64 Emulator**
    - **[Simple64](https://github.com/simple64/simple64/releases){ target="_blank" }**<small> :material-open-in-new: </small><small>recommended emulator</small>
    - **[Rosalie's Mupen GUI](https://github.com/Rosalie241/RMG/releases){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[ares](https://github.com/ares-emulator/ares/releases){ target="_blank" }**<small> :material-open-in-new: </small>
    - **[Project64](https://www.pj64-emu.com/public-releases){ target="_blank" }**<small> :material-open-in-new: </small>
- ##### **ROM Decompression Tool**
    - **[nDEC](#)**<small> :material-open-in-new: </small>

#### Brief Summary of Tools
=== "SEQ64"
    **SEQ64** is a tool created for making music sequences for first-party Nintendo 64 games (games made by Nntendo EAD/SRD). It has the capability of converting `.mid`, `.com`, and `.mus` files into sequences and vice versa; for `v1.0` and `v1.5` it has the ability to edit audiobank files as well, though this feature was removed for `v2.X.X` and is now dead for it due to ongoing decompilation of various Nintendo 64 games.

    !!! info "SEQ64 v1.0 versus v1.5"
        For all intents and purposes there are no differences in the main functionality of SEQ64 `v1.0` and `v1.5`, they are functionally identical, however SEQ64 `v1.0` has a light theme, and SEQ64 `v1.5` has a dark theme.

=== "ROM Description"
    The **ROM Description** is a data file containing music sequence format definition, audiobank binary format definition, addresses of key files and tables, and general program settings. This data file has been succeeded by the ABI data file for SEQ64 `v2.X.X` which only contains the music sequence format definition. The ROM descriptions provided with SEQ64 are very old, however the ROM descriptions linked to above have been edited with more information filled out.

=== "Digital Audio Workstation"
    **Digital Audio Workstations**, or **DAW** for short, are where you create or edit conventional music files. For the purposes of creating music for *Ocarina of Time* and *Majora's Mask* you need a DAW that is capable of creating and editing `.mid` files. The DAWs linked above are the most common DAWs used within the randomizer communities.

=== "Soundfont"
    The **Soundfont** will allow you to preview your music similar to how it would sound in-game using a DAW capable of music playback with a soundfont allowing you to easily modify your music before you convert it. The soundfonts don't sound exactly like how in-game sounds will sound, however it is close enough to give you a good idea of how it will sound.

=== "N64 Emulator"
    An **N64 Emulator** is used to preview your music in-game, this will allow you to make sure there are no problems with the sequence or audiobank in-game. The emulators linked above are mostly standalone Nintendo 64 emulators, with only ares being a multi-system emulator. It is recommended to *avoid* RetroArch and other multi-system emulators and frontends.

=== "nDEC"
    **nDEC** is used to decompress your ROM so that you are able to edit it in SEQ64. nDEC is simple enough to use as there is a file bundled with the program in the link provided that does all the work for you. Should you need detailed instructions on how to decompress your ROM you can find them on the ROM requirements page of the wiki.

-----

## Obtaining a ROM
Along with the tools above, you will need to obtain a ROM of *Ocarina of Time* and/or *Majora's Mask* and decompress it using a decompression tool. Sharing ROM files is illegal as the files are copyrighted by Nintendo, so this wiki cannot share links to any websites containing the ROM files. MD5 and *CRC32* values are *quite useful* when checking to make sure your ROM is the correct version you need for using the tools both of which are provided on the ROM requirements page to check your ROM file is correct and does not contain any errors.

!!! info "Dumping ROMs"
    If you have the capability, it is best to dump the ROM yourself from hardware, however all Virtual Console and Nintendo Switch Online versions of *Ocarina of Time* are version 1.2 and not version 1.0; for *The Legend of Zelda: Collector's Edition* the ROM files for *Ocarina of Time* and *Majora's Mask* are ROMs that were compiled specifically for *The Legend of Zelda: Collector's Edition* and cannot be used at all.

-----
