# Getting Started

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

placeholder

???+ info "ROM Byte Ordering"

    If your ROM has the file format of either `.n64` (Little Endian) or `.v64` (Byteswapped) you will need to use [`Tool64`](https://www.zophar.net/download_file/2854 "Click to download Tool64") to change the byte order of the ROM as the tools used to edit the ROM require it to use Big Endian (`.z64`) byte ordering.

    To use `Tool64` simply open the folder containing your ROM(s) then right click the ROM(s) that appear and select "Big Endian" from the context menu that appears.

    If you're checking the ROM using a hex editor please refer to the game's title as it appears on the ROM in the hex editor using the information below (the title will be at the following address range `0x00000020` to `0x0000003F`):

    === "Little Endian (`.n64`)"
        For Ocarina of Time the title will be arranged as such in Little Endian byte ordering:
        ``` linenums="0"
         EHTEGELO DNEZ F ADL....C....ELZ
        ```
        For Majora's Mask the title will be arranged as such in Little Endian byte ordering:
        ``` linenums="0"
        DLEZAM AAROJM S' KSA....N....ESZ
        ```

    === "Big Endian (`.z64`)"
        For Ocarina of Time the title will be arranged as such in Big Endian byte ordering:
        ``` linenums="0"
        THE LEGEND OF ZELDA .......CZLE.
        ```
        For Majora's Mask the title will be arranged as such in Big Endian byte ordering:
        ``` linenums="0"
        ZELDA MAJORA'S MASK .......NZSE.
        ```

    === "Byteswapped (`.v64`)"
        For Ocarina of Time the title will be arranged as such in Byteswapped byte ordering:
        ``` linenums="0"
        HT EELEGDNO  FEZDL A......C.LZ.E
        ```
        For Majora's Mask the title will be arranged as such in Byteswapped byte ordering:
        ``` linenums="0"
        EZDL AAMOJARS'M SA K......N.SZ.E
        ```

## Ocarina of Time ROM Requirements

???+ success "ROM MD5 Checksum"

    An easy way to check if your ROM is the correct ROM is to open [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher") and check your ROM's MD5 checksum.

    === "Compressed (NTSC-U)"
        `Legend of Zelda, The - Ocarina of Time (NTSC-U) [V1.0]`
        ``` linenums="0"
        5bd1fe107bf8106b2ab6650abecd54d6
        ```

    === "Decompressed (NTSC-U)"
        `Legend of Zelda, The - Ocarina of Time (NTSC-U) [V1.0]`
        ``` linenums="0"
        6f7957f08d564ae255b25d54b9eb6774
        ```

    === "Compressed (NTSC-J)"
        `Zelda no Densetsu - Toki no Ocarina (NTSC-J) [V1.0]`
        ``` linenums="0"
        9f04c8e68534b870f707c247fa4b50fc
        ```

    === "Decompressed (NTSC-J)"
        `Zelda no Densetsu - Toki no Ocarina (NTSC-J) [V1.0]`
        ``` linenums="0"
        361f0a3bfc21289928d0f671517a6897
        ```

## Majora's Mask ROM Requirements

To be able to work with the tools required for custom music creation your Majora's Mask ROM will need to be an NTSC-U version 1.0 ROM; your ROM cannot be NTSC-J version 1.0 or 1.1, nor can it be a PAL version 1.0 ROM. The tools used to create music for Majora's Mask only support or have information available for NTSC-U version 1.0, and unlike how NTSC versions work for Ocarina of Time there are multiple changes between the ROMs for NTSC versions of the game that make them vastly different (e.g. Owl Quicksaves being added in NTSC-U where they were absent from NTSC-J, or Zora Swimming physics being altered from NTSC-J to NTSC-U, etc).

To make sure you have an unmodified and correct version of the ROM, there are MD5 checksums available below to cross reference for both compressed ROMs and decompressed ROMs.

???+ success "ROM MD5 Checksum"

    An easy way to check if your ROM is the correct ROM is to open [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher") and check your ROM's MD5 checksum.

    === "Compressed (NTSC-U)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ``` linenums="0"
        2a0a8acb61538235bc1094d297fb6556
        ```

    === "Decompressed (NTSC-U)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ``` linenums="0"
        05fd2b38816173f92ab279c059fabbfb
        ```

## placeholder

![](assets/images/samples/piano-range-light.png#only-light){ .on-glb }
![](assets/images/samples/piano-range-dark.png#only-dark){ .on-glb }

-----