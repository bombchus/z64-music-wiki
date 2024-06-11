# Getting Started

## Requirements

a

???+ info "ROM Formats"

    === "Little Endian (`.n64`)"
        If your ROM has the file format of `.n64` you will need to use [Tool64](https://www.zophar.net/download_file/2854 "Click to download Tool64") to change the byte order of the ROM as the tools used to edit the ROM require it to use Big Endian byte ordering. Simply point the program to the folder containing your ROM(s) then right click and select `Big Endian`.

        For Ocarina of Time the title will be arranged as such in Little Endian byte ordering:
        ```
         EHTEGELO DNEZ FADL....C....ELZ
        ```
        For Majora's Mask the title will be arranged as such in Little Endian byte ordering:
        ```
        DLEZAM AAROJM S' KSA....N....ESZ
        ```

    === "Big Endian (`.z64`)"
        If your ROM has the file format of `.z64` you will not need to do anything to your ROM, however you can confirm the byte ordering is correct if you are unsure of whether or not the ROM has been tampered with or wish to confirm it uses the correct byte ordering anyway.

        For Ocarina of Time the title will be arranged as such in Big Endian byte ordering:
        ```
        THE LEGEND OF ZELDA .......CZLE
        ```
        For Majora's Mask the title will be arranged as such in Big Endian byte ordering:
        ```
        ZELDA MAJORA'S MASK .......NZSE
        ```

    === "Byteswapped (`.v64`)"
        If your ROM has the file format of `.v64` you will need to use [Tool64](https://www.zophar.net/download_file/2854 "Click to download Tool64") to change the byte order of the ROM as the tools used to edit the ROM require it to use Big Endian byte ordering. Simply point the program to the folder containing your ROM(s) then right click and select `Big Endian`.

        For Ocarina of Time the title will be arranged as such in Byteswapped byte ordering:
        ```
        HT EELEGDNO  FEZDL A......C.LZ.E
        ```
        For Majora's Mask the title will be arranged as such in Byteswapped byte ordering:
        ```
        EZDL AAMOJARS'MSA K......N.SZ.E
        ```