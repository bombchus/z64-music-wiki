# ROM Requirements

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details the requirements for ROMs of *Ocarina of Time* and *Majora's Mask* so that you will be able to use them to assist in creating cusom music by testing your sequences, and audiobanks, in-game to check for any errors as well as help you make any adjustments you may want to your custom music.

## General ROM Requirements
To be able to use SEQ64 your ROM will need to be decompressed as SEQ64 cannot decompress Yaz0 files despite having tools for compression and decompression of these files in SEQ64 `v1.0` and `v1.5`.

### Byte Ordering
While SEQ64 and emulators can work with all types of ROM byte ordering, to be able to work with the randomizers for custom music creation your ROM will need to be in the "Big Endian" byte order, MSB first and LSB last (e.g. `0x1234` is `0x1243`), and not in the "Little Endian" byte order, LSB first and MSB last (e.g. `0x1243` becomes `0x4312`), or in the "Byteswapped" byte order, every byte value is reversed (e.g. `0x1234` becomes `0x2143`). You can see more information in the info box below about how to make sure your ROM is Big Endian, and what you can do to change your ROM's byte ordering to Big Endian if it isn't already.

???+ info "ROM Byte Ordering"

    If your ROM has the file format of either `.n64` (Little Endian) or `.v64` (Byteswapped) you will need to use [Tool64](https://www.zophar.net/download_file/2854 "Click to download Tool64"){ target="_blank" }<small> :material-open-in-new:</small> to change the byte order of the ROM as the tools used to edit the ROM require it to use Big Endian (`.z64`) byte ordering.

    To use Tool64 simply open the folder containing your ROM(s) then right click the ROM(s) that appear and select "Big Endian" from the context menu that appears.

    If you're checking the ROM using a hex editor please refer to the ROM's internal name as it appears on the ROM in the hex editor using the information below (the title will be at the following address range `0x00000020` to `0x0000003F`):

    === "Little Endian (`.n64`)"
        For *Ocarina of Time* the ROM's internal name will be arranged as such in Little Endian byte ordering:
        ``` linenums="0"
         EHTEGELO DNEZ F ADL....C....ELZ
        ```
        For *Majora's Mask* the ROM's internal name will be arranged as such in Little Endian byte ordering:
        ``` linenums="0"
        DLEZAM AAROJM S' KSA....N....ESZ
        ```

    === "Big Endian (`.z64`)"
        For *Ocarina of Time* the ROM's internal name will be arranged as such in Big Endian byte ordering:
        ``` linenums="0"
        THE LEGEND OF ZELDA .......CZLE.
        ```
        For *Majora's Mask* the ROM's internal name will be arranged as such in Big Endian byte ordering:
        ``` linenums="0"
        ZELDA MAJORA'S MASK .......NZSE.
        ```

    === "Byteswapped (`.v64`)"
        For *Ocarina of Time* the ROM's internal name will be arranged as such in Byteswapped byte ordering:
        ``` linenums="0"
        HT EELEGDNO  FEZDL A......C.LZ.E
        ```
        For *Majora's Mask* the ROM's internal name will be arranged as such in Byteswapped byte ordering:
        ``` linenums="0"
        EZDL AAMOJARS'M SA K......N.SZ.E
        ```

## Ocarina of Time ROM Requirements

To be able to work with the tools required for custom music creation your *Ocarina of Time* ROM will need to be any NTSC region version 1.0 ROM; NTSC region version 1.1 ROMs, NTSC region version 1.2 ROMs, and any version of PAL region ROMs will not work. The tools used to create music for *Ocarina of Time* only support or have information available for NTSC region version 1.0 ROMs because the tool's developers and subsequently the randomizer's developers decided on using NTSC region version 1.0 ROMs instead of any other version, however for *Ocarina of Time* it does not matter if your ROM is NTSC-J or NTSC-U as the only difference between the NTSC-J and NTSC-U region ROMs is a toggle determining whether or not the language should be in Japanese or English.[^1]

To make sure you have an unmodified version of the ROM, there are MD5 checksums available below to reference for both compressed and decompressed *Ocarina of Time* NTSC version 1.0 ROMs

???+ success "ROM MD5 and CRC32 Checksums"

    A relatively easy way to check if you have the correct ROM is to go to [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher"){ target="_blank" }<small>:material-open-in-new: </small> and open your ROM (ROM File) to check your ROM's MD5 and CRC32 checksums.

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

To be able to work with the tools required for custom music creation your *Majora's Mask* ROM will need to be an NTSC-U version 1.0 ROM; NTSC-J version 1.0 ROMs, NTSC-J version 1.1 ROMs, and any version of PAL region ROMs will not work. The tools used to create music for *Majora's Mask* only support or have information available for NTSC-U version 1.0 because the tool's developers and subsequently the randomizer's developers decided on using NTSC-U version 1.0 instead of any other version, and unlike how NTSC versions work for *Ocarina of Time* there are multiple changes between the ROMs for NTSC versions of the game that make them vastly different (e.g. Owl Quicksaves being added in NTSC-U where they were absent from NTSC-J, or Zora Swimming physics being altered from NTSC-J to NTSC-U, etc).[^2]

To make sure you have an unmodified and correct version of the ROM, there are MD5 checksums available below to reference for both compressed and decompressed *Majora's Mask* NTSC-U version 1.0 ROMs.

???+ success "ROM MD5 Checksum"

    A relatively easy way to check if you have the correct ROM is to go to [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher"){ target="_blank" }<small>:material-open-in-new: </small> and open your ROM (ROM File) to check your ROM's MD5 and CRC32 checksums.

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

## placeholder

![](../assets/images/samples/piano-range-light.png#only-light){ .on-glb }
![](../assets/images/samples/piano-range-dark.png#only-dark){ .on-glb }

[^1]: For a full breakdown of every difference between versions in *The Legend of Zelda: Ocarina of Time*, please visit The Cutting Room Floor's [page](https://tcrf.net/The_Legend_of_Zelda:_Ocarina_of_Time/Version_Differences "The Legend of Zelda: Ocarina of Time Version Differences"){ target="_blank" }<small>:material-open-in-new: </small> on version differences.

[^2]: For a full breakdown of every difference between versions in *The Legend of Zelda: Majora's Mask*, please visit The Cutting Room Floor's [page](https://tcrf.net/The_Legend_of_Zelda:_Majora%27s_Mask/Program_Revision_Differences "The Legend of Zelda: Majora's Mask Program Revision Differences"){ target="_blank" }<small>:material-open-in-new: </small> on program revisions.