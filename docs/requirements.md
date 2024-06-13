# Requirements


???+ success "ROM MD5 Checksum"

    An easy way to check if your ROM is the correct ROM is to open [this site](https://www.marcrobledo.com/RomPatcher.js/ "ROM Patcher") and check your ROM's MD5 checksum.

    === "OoT (Compressed)"
        `Legend of Zelda, The - Ocarina of Time (U) (V1.0)`
        ```
        5bd1fe107bf8106b2ab6650abecd54d6
        ```

    === "OoT (Decompressed)"
        `Legend of Zelda, The - Ocarina of Time (U) (V1.0)`
        ```
        6f7957f08d564ae255b25d54b9eb6774
        ```

    === "MM (Compressed)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ```
        2a0a8acb61538235bc1094d297fb6556
        ```

    === "MM (Decompressed)"
        `Legend of Zelda, The - Majora's Mask (NTSC-U) [v1.0]`
        ```
        05fd2b38816173f92ab279c059fabbfb
        ```

???+ info "ROM Byte Ordering"

    If your ROM has the file format of either `.n64` (Little Endian) or `.v64` (Byteswapped) you will need to use [`Tool64`](https://www.zophar.net/download_file/2854 "Click to download Tool64") to change the byte order of the ROM as the tools used to edit the ROM require it to use Big Endian (`.z64`) byte ordering.

    To use `Tool64` simply open the folder containing your ROM(s) then right click the ROM(s) that appear and select "Big Endian" from the context menu that appears.

    If you're checking the ROM using a hex editor please refer to the game's title as it appears on the ROM in the hex editor using the information below (the title will be at the following address range `0x00000020` to `0x0000003F`):

    === "Little Endian (`.n64`)"
        For Ocarina of Time the title will be arranged as such in Little Endian byte ordering:
        ```
         EHTEGELO DNEZ F ADL....C....ELZ
        ```
        For Majora's Mask the title will be arranged as such in Little Endian byte ordering:
        ```
        DLEZAM AAROJM S' KSA....N....ESZ
        ```

    === "Big Endian (`.z64`)"
        For Ocarina of Time the title will be arranged as such in Big Endian byte ordering:
        ```
        THE LEGEND OF ZELDA .......CZLE.
        ```
        For Majora's Mask the title will be arranged as such in Big Endian byte ordering:
        ```
        ZELDA MAJORA'S MASK .......NZSE.
        ```

    === "Byteswapped (`.v64`)"
        For Ocarina of Time the title will be arranged as such in Byteswapped byte ordering:
        ```
        HT EELEGDNO  FEZDL A......C.LZ.E
        ```
        For Majora's Mask the title will be arranged as such in Byteswapped byte ordering:
        ```
        EZDL AAMOJARS'M SA K......N.SZ.E
        ```

-----