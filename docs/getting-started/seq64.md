# Using SEQ64

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page goes over how to get started with SEQ64 for creating custom music in *Ocarina of Time* and *Majora's Mask*. It will give a basic rundown on the program as well as importing and converting a `.mid` file into a sequence file.

!!! warning "Bugs and Errors"
    Please be aware that SEQ64 is an old program with many bugs, some known and others unknown. Errors and issues may be encountered when using the program when editing a ROM, ROM description, sequence file, or audiobank file.

!!! info
    This page will be using SEQ64 `v1.5.0` and SEQ64 `v2.3.3` for images, SEQ64 `v1.0.0` should have no dfference from `v1.5.0` other than the UI style and theme of the program. Everything should be located in the same place and have all the same options for SEQ64 versions 1.0 and 1.5.

## Loading a ROM and ROM Description <small>v1.0.0 and v1.5.0 only</small> { #loading-a-rom-and-rom-description data-toc-label="Loading a ROM and ROM Description" }
When SEQ64 first opens everything will be blank and none of the program's fields will be populated with information. To begin working a ROM and ROM description will need to be loaded into SEQ64. The images below highlight how to load a ROM and ROM Description. It should not matter what order the ROM or ROM description are loaded in. However, it may be safest to load the ROM description first.

=== "Loading a  ROM"
    ![](../assets/images/seq64/seq64-load-rom.png){ .on-glb }

    !!! outline
        > 1. At the top of the window click "ROM > Load...".
        > 2. In the file explorer window, navigate to the folder your decompressed ROM is in.
        > 3. Select your ROM and click "Open" in file explorer.

=== "Loading a ROM Description"
    ![](../assets/images/seq64/seq64-load-romdesc.png){ .on-glb }

    !!! outline
        > 1. At the top of the window click "RomDesc > Load...".
        > 2. In the file explorer window, navigate to the folder your ROM description is in.
        > 3. Select your ROM description and click "Open" in file explorer.

!!! info
    If the ROM has byte ordering other than Big Endian then the ROM's internal title shown in the title bar of SEQ64 will be switched around. The byte ordering SEQ64 uses can be changed. However, the ROM should be Big Endian byte ordering otherwise data may end up misaligned.

After loading a ROM and ROM description all of the program's fields should be populated with ROM information and all the information inside of the ROM description. If the ROM description was loaded first then fields will be populated. However, not all of the fields will be populated until a ROM is also loaded.

## Importing a MIDI File Into SEQ64
placeholder

=== "SEQ64 v1.0.0 and v1.5.0"
    ![](../assets/images/seq64/seq64-midi-1.png){ .on-glb }

    Press the "Import MIDI" button to import a `.mid` file to convert into a sequence. Before importing the highlighted values can be changed

    The **"Chn volume to"** dropdown determines the MIDI control change message to be converted to the channel sequence command 0xDF or "Set Volume".

    The **"Master volume to"** dropdown determines the MIDI control change or SysEx message to be converted to the header sequence command 0xDB or "Set Volume (SysEX Master Volume)".

    The **"Chn priority to"** dropdown determines the MIDI control change message to be converted to the channel sequence command 0xE9 or "Set Note Priority".

    The **"Create command to loop whole sequence"** checkbox determines whether or not SEQ64 will create the control flow sequence command 0xFB or "Jump Absolute" in the sequence and point to the correct address; if a MIDI has no marker meta message containing the text "loop" or "section" then it will point to the start of the sequence, and if a MIDI does contain marker meta messages containing the text "loop" or "section" then it will point to the first section created by SEQ64 during the MIDI to sequence conversion process.

    Fields highlighted in <span style="color:#f9ad81">orange</span> are fields that are optional fields that can change how a sequence looks when imported.
    
    Fields highlighted in <span style="color:#a3d39c">green</span> are fields that should not be changed, and instead be left as is.

=== "SEQ64 v2.X.X"
    ![](../assets/images/seq64/seq64-midi-2.png){ .on-glb }

    Press the "Import MIDI" button to import a `.mid` file to convert into a sequence. Before importing the highlighted values can be changed

    Fields highlighted in <span style="color:#f9ad81;">orange</span> are fields that are optional fields that can change how a sequence looks when imported.
    
    Fields highlighted in <span style="color:#a3d39c;">green</span> are fields that should not be changed, and instead be left as is.

-----