# ROM Requirements

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

!!! alert "Procuring a ROM"
    This page, as well as the wiki itself, can not and will not supply any ROM files or links to any ROM files for *Ocarina of Time* and *Majora's Mask* as it is illegal to do so. This wiki is not meant for piracy of copyrighted materials, it is meant to help those interested in creating custom music for *Ocarina of Time* and *Majora's Mask* learn the process and other details related to music creation for the games.

This page details the ROM requirements for ROMs of *Ocarina of Time* and *Majora's Mask* for use in creating custom music by testing sequences and audiobanks in-game to check for any errors as well as help making any adjustments to the custom music.

## Ocarina of Time ROM Requirements
To be able to work with the tools required for custom music creation, the *Ocarina of Time* ROM will need to be any NTSC region version 1.0 ROM. NTSC region version 1.1 ROMs, NTSC region version 1.2 ROMs, and any version of PAL region ROMs will not work. The tools used to create music for *Ocarina of Time* only support or only have information available for NTSC region version 1.0 ROMs because the tool's developers decided on using NTSC region version 1.0 ROMs. However, for *Ocarina of Time* it does not matter if the ROM is NTSC-J or NTSC-U as the only difference between the NTSC-J and NTSC-U region ROMs is a toggle determining whether the language displayed should be in Japanese or English.[^1]

To make sure the ROM is unmodified and is the correct game version, there are MD5 checksums available below to reference for both compressed and decompressed *Ocarina of Time* NTSC version 1.0 ROMs:

!!! success "ROM MD5 and CRC32 Checksums"

    A relatively easy way to check if a ROM is correct is to go to [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher"){ target="_blank" }<small>:material-open-in-new: </small> and open the ROM to check the ROM's MD5 and CRC32 checksums.

    === "Compressed (NTSC-U)"
        `Legend of Zelda, The - Ocarina of Time (NTSC-U) [V1.0]`
        ``` linenums="0"
        CRC32: CD16C529
          MD5: 5BD1FE107BF8106B2AB6650ABECD54D6
        ```

    === "Decompressed (NTSC-U)"
        `Legend of Zelda, The - Ocarina of Time (NTSC-U) [V1.0]`
        ``` linenums="0"
        CRC32: B94D8AF1
          MD5: 6F7957F08D564AE255B25D54B9EB6774
        ```

    === "Compressed (NTSC-J)"
        `Zelda no Densetsu - Toki no Ocarina (NTSC-J) [V1.0]`
        ``` linenums="0"
        CRC32: D423E8B0
          MD5: 9F04C8E68534B870F707C247FA4B50FC
        ```

    === "Decompressed (NTSC-J)"
        `Zelda no Densetsu - Toki no Ocarina (NTSC-J) [V1.0]`
        ``` linenums="0"
        CRC32: 49A3439C
          MD5: 361F0A3BFC21289928D0F671517A6897
        ```

## Majora's Mask ROM Requirements
To be able to work with the tools required for custom music creation, the *Majora's Mask* ROM will need to be an NTSC-U version 1.0 ROM. NTSC-J version 1.0 ROMs, NTSC-J version 1.1 ROMs, and any version of PAL region ROMs will not work. The tools used to create music for *Majora's Mask* only support or have information available for NTSC-U version 1.0 because the tool's developers decided on using NTSC-U version 1.0. Unlike NTSC versions of *Ocarina of Time* there are multiple version differences between the NTSC versions of the game that make them vastly different (e.g., Owl Quicksaves being added to NTSC-U where they were absent from NTSC-J, or Zora Swimming physics being altered from NTSC-J to NTSC-U, etc.).[^2]

To make sure the ROM is unmodified and is the correct game version, there are MD5 checksums available below to reference for both compressed and decompressed *Majora's Mask* NTSC-U version 1.0 ROMs:

!!! success "ROM MD5 Checksum"

    A relatively easy way to check if a ROM is correct is to go to [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher"){ target="_blank" }<small>:material-open-in-new: </small> and open the ROM to check the ROM's MD5 and CRC32 checksums.

    === "Compressed (NTSC-U)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ``` linenums="0"
        CRC32: B428D8A7
          MD5: 2A0A8ACB61538235BC1094D297FB6556
        ```

    === "Decompressed (NTSC-U)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ``` linenums="0"
        CRC32: 33751C40
          MD5: 05FD2B38816173F92AB279C059FABBFB
        ```

## ROM Compression Requirements
To be able to use and edit a ROM with SEQ64 versions 1.0 and 1.5, it needs to be decompressed. If the ROM is not decompressed, then it will not be able to be used with SEQ64 to create sequences, test sequences on vanilla ROMs, or create custom audiobanks. SEQ64 cannot decompress ROMs, a different tool must be used. Any Yaz0 file compression or decompression SEQ64 versions 1.0 and 1.5 can do are only for single files, not entire ROMs.

!!! info
    Sequences can still be created without a compressed ROM using SEQ64 versions 2.0 and above. However, either the *Ocarina of Time* randomizer or *Majora's Mask* randomizer must be used to test the sequences in-game. This method is not recommended as a new seed must be created to test any new changes made to the sequence.

### Decompressing a ROM
To decompress a ROM, it is best to use the ROM decompression tool nDEC. While there are other ROM decompression tools available, nDEC is one of the few decompression tools that can properly decompress *Majora's Mask*. Other tools may properly decompress *Ocarina of Time*, but as stated previously they will not properly decompress *Majora's Mask*.

!!! info "nDEC"
    nDEC is a tool for decompressing Nintendo 64 Zelda ROMs written in the C programming language that requires usage of the command line and must be compiled. An already compiled nDEC that includes an easy-to-use Windows batch file can be downloaded on the [tools and resources](../tools/#rom-decompression-tool){ target="_blank" }<small>:material-open-in-new: </small> page of this wiki.
    
To use nDEC and the batch file, simply follow the steps below:

> 1. Move a compressed ROM (input ROM) of *Ocarina of Time* or *Majora's Mask* into the same folder as the nDEC executable file (`ndec.exe`) and Windows batch script file (`Drop Your ROM Here.bat`).
> 2. Click and drag the compressed ROM (input ROM) of *Ocarina of Time* or *Majora's Mask* onto the Windows batch script file (`Drop Your ROM Here.bat`).
> 3. Wait for nDEC to decompress the compressed ROM (input ROM) and for the command line window to close.

Once completed, a decompressed ROM (output ROM) will have automatically been moved into a folder that shares the same name as the compressed ROM (input ROM) with the decompressed ROM (output ROM) having been renamed to "DECOMPRESSED_ROM".

!!! alert
    For a ROM to be decompressed with nDEC it must be in the Big Endian byte order.

## ROM Byte Ordering
While SEQ64 and emulators can work with all types of ROM byte ordering, to be able to decompress a ROM and use it with the randomizers for custom music creation, the ROM will need to be in the "Big Endian" byte order, MSB first and LSB last (e.g. `0x1234` is `0x1234`). The ROM cannot be in the "Little Endian" byte order, LSB first and MSB last (e.g. `0x1243` becomes `0x3412`), or in the "Byteswapped" byte order, every byte value is reversed (e.g. `0x1234` becomes `0x2143`). More information is available in the info box below about how to make sure a ROM is Big Endian, and what can be done to change the ROM's byte ordering to Big Endian if it is not already in the proper byte order.

While SEQ64 versions 1.0 and 1.5, as well as emulators, can work with ROMs using any byte order, for a ROM to work with nDEC it must be in the "Big Endian" byte order. If a ROM is in the "Little Endian" or "Byteswapped" byte order, it cannot be decompressed with nDEC. Big endian orders the bytes from MSB to LSB (e.g., `0x1234` will be `0x1234`). Little endian orders the bytes from LSB to MSB (e.g., `0x1234` will be `0x3412`). Byteswapped byte order reverses every byte (e.g., `0x1234` will be `0x2143`).

### Checking a ROM's Byte Ordering
There are two ways to check a ROM's byte order:

1. Check the ROM's file extension.
2. Open the ROM in a hex editor and reading the ROM's internal name.

It is recommended not to check just by using a file extension, because file extensions can be changed at any point. Checking the ROM's byte order by checking the ROM's internal name is the best way to find out a ROM's byte order. However, at a glance the file extension can be useful.

To check a ROM's byte order without relying on the file's extension, refer to the ROM's internal name as it appears in a hex editor using the information below (the internal name will be at the following address range: `0x00000020` to `0x0000003F`):

!!! info "ROM Internal Names"

    === "Little Endian (`.n64`)"
        For *Ocarina of Time*, the ROM's internal name with little endian byte ordering will be:
        ``` linenums="0"
        EHTEGELO DNEZ F ADL....C....ELZ
        ```
        For *Majora's Mask*, the ROM's internal name with little endian byte ordering will be:
        ``` linenums="0"
        DLEZAM AAROJM S' KSA....N....ESZ
        ```

    === "Big Endian (`.z64`)"
        For *Ocarina of Time*, the ROM's internal name with big endian byte ordering will be:
        ``` linenums="0"
        THE LEGEND OF ZELDA .......CZLE.
        ```
        For *Majora's Mask*, the ROM's internal name with big endian byte ordering will be:
        ``` linenums="0"
        ZELDA MAJORA'S MASK .......NZSE.
        ```

    === "Byteswapped (`.v64`)"
        For *Ocarina of Time*, the ROM's internal name with byteswapped byte ordering will be:
        ``` linenums="0"
        HT EELEGDNO  FEZDL A......C.LZ.E
        ```
        For *Majora's Mask*, the ROM's internal name with byteswapped byte ordering will be:
        ``` linenums="0"
        EZDL AAMOJARS'M SA K......N.SZ.E
        ```

### Changing a ROM's Byte Ordering
If a ROM has the file extension of either `.n64` (Little Endian) or `.v64` (Bytesswapped), the byte order will need to be changed to `z64` (Big Endian) using [Tool64](https://www.zophar.net/download_file/2854 "Click to download Tool64"){ target="__blank" }<small>:material-open-in-new:</small>.

To change a ROM's byte ordering with Tool64 follow the steps below:
> 1. Open Tool64.
> 2. At the top of the window, click "File > Open...".
> 3. In the new window that appears, select the directory containing the ROM to be modified.
> 4. Click "OK".
> 5. In the main window, Select the ROM to modify the byte order of.
> 6. Right-click and select "Big Endian" from the context menu.

!!! warning
    Just changing the ROM's file extension will not change the ROM's byte ordering.

[^1]: For a full breakdown of every difference between versions in *The Legend of Zelda: Ocarina of Time*, please visit The Cutting Room Floor's [page](https://tcrf.net/The_Legend_of_Zelda:_Ocarina_of_Time/Version_Differences "The Legend of Zelda: Ocarina of Time Version Differences"){ target="_blank" }<small>:material-open-in-new: </small> on version differences.

[^2]: For a full breakdown of every difference between versions in *The Legend of Zelda: Majora's Mask*, please visit The Cutting Room Floor's [page](https://tcrf.net/The_Legend_of_Zelda:_Majora%27s_Mask/Program_Revision_Differences "The Legend of Zelda: Majora's Mask Program Revision Differences"){ target="_blank" }<small>:material-open-in-new: </small> on program revisions.