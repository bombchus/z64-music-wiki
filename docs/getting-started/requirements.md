# ROM Requirements

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    <table style="border: none;">
      <tbody>
        <tr>
          <td><a><img src="../assets/images/carpenters.png"></a></td>
          <td><i>This page is a work in progress and requires further editing.</i></td>
        </tr>
      </tbody>
    </table>

</div>

This page details the requirements for ROMs of *Ocarina of Time* and *Majora's Mask* so that you will be able to use them to assist in creating cusom music by testing your sequences, and audiobanks, in-game to check for any errors as well as help you make any adjustments you may want to your custom music.

## General ROM Requirements
To be able to work with the tools required for custom music creation edit your ROM will need to be in the "Big Endian" byte order, MSB first and LSB last (e.g. `0x1234` is `0x1243`), and not in the "Little Endian" byte order, LSB first and MSB last (e.g. `0x1243` becomes `0x4312`), or in the "Byteswapped" byte order, every byte value is reversed (e.g. `0x1234` becomes `0x2143`). You can see more information in the info box below about how to make sure your ROM is Big Endian, and what you can do to change your ROM's byte ordering to Big Endian if it isn't already.

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

    An easy way to check if your ROM is the correct ROM is to open [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher") and check your ROM's MD5 checksum.

    === "Compressed (NTSC-U)"
        `Legend of Zelda, The - Ocarina of Time (NTSC-U) [V1.0]`
        ``` linenums="0"
        CRC32: cd16c529
          MD5: 5bd1fe107bf8106b2ab6650abecd54d6
        ```

    === "Decompressed (NTSC-U)"
        `Legend of Zelda, The - Ocarina of Time (NTSC-U) [V1.0]`
        ``` linenums="0"
        CRC32: b94d8af1
          MD5: 6f7957f08d564ae255b25d54b9eb6774
        ```

    === "Compressed (NTSC-J)"
        `Zelda no Densetsu - Toki no Ocarina (NTSC-J) [V1.0]`
        ``` linenums="0"
        CRC32: d423e8b0
          MD5: 9f04c8e68534b870f707c247fa4b50fc
        ```

    === "Decompressed (NTSC-J)"
        `Zelda no Densetsu - Toki no Ocarina (NTSC-J) [V1.0]`
        ``` linenums="0"
        CRC32: 49a3439c
          MD5: 361f0a3bfc21289928d0f671517a6897
        ```

## Majora's Mask ROM Requirements

To be able to work with the tools required for custom music creation your *Majora's Mask* ROM will need to be an NTSC-U version 1.0 ROM; NTSC-J version 1.0 ROMs, NTSC-J version 1.1 ROMs, and any version of PAL region ROMs will not work. The tools used to create music for *Majora's Mask* only support or have information available for NTSC-U version 1.0 because the tool's developers and subsequently the randomizer's developers decided on using NTSC-U version 1.0 instead of any other version, and unlike how NTSC versions work for *Ocarina of Time* there are multiple changes between the ROMs for NTSC versions of the game that make them vastly different (e.g. Owl Quicksaves being added in NTSC-U where they were absent from NTSC-J, or Zora Swimming physics being altered from NTSC-J to NTSC-U, etc).[^2]

To make sure you have an unmodified and correct version of the ROM, there are MD5 checksums available below to reference for both compressed and decompressed *Majora's Mask* NTSC-U version 1.0 ROMs.

???+ success "ROM MD5 Checksum"

    An easy way to check if your ROM is the correct ROM is to open [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher") and check your ROM's MD5 checksum.

    === "Compressed (NTSC-U)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ``` linenums="0"
        CRC32: b428d8a7
          MD5: 2a0a8acb61538235bc1094d297fb6556
        ```

    === "Decompressed (NTSC-U)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ``` linenums="0"
        CRC32: 33751c40
          MD5: 05fd2b38816173f92ab279c059fabbfb
        ```

## placeholder

![](../assets/images/samples/piano-range-light.png#only-light){ .on-glb }
![](../assets/images/samples/piano-range-dark.png#only-dark){ .on-glb }

[^1]: For a full breakdown of every difference between versions in *The Legend of Zelda: Ocarina of Time*, please visit The Cutting Room Floor's [page](https://tcrf.net/The_Legend_of_Zelda:_Ocarina_of_Time/Version_Differences "The Legend of Zelda: Ocarina of Time Version Differences") on version differences.

[^2]: For a full breakdown of every difference between versions in *The Legend of Zelda: Majora's Mask*, please visit The Cutting Room Floor's [page](https://tcrf.net/The_Legend_of_Zelda:_Majora%27s_Mask/Program_Revision_Differences "The Legend of Zelda: Majora's Mask Program Revision Differences") on program revisions.