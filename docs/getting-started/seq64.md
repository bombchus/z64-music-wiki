# Using SEQ64

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page goes over how to get started with SEQ64 for creating custom music in *Ocarina of Time* and *Majora's Mask*. It will give a basic rundown on the program as well as importing and converting a `.mid` file into a sequence file.

!!! info
    Please be aware that SEQ64 is an old program with many bugs, some known and others unknown. You may encounter errors and issues when using the program when editing a ROM, ROM description, sequence file, or audiobank file.

## Loading a ROM and ROM Description <small>v1.0.0 and v1.5.0 only</small> { #loading-a-rom-and-rom-description data-toc-label="Loading a ROM and ROM Description" }
When you first open SEQ64 you will see that everything is blank and none of the program's fields are populated with information. To begin working you will need to load your ROM into SEQ64 and load a ROM description for it. The images below highlight how to load a ROM and ROM Description. It should not matter what order you load your ROM or ROM description in, however it may be safest to load the ROM description first.

=== "Loading a  ROM"
    ![](../assets/images/seq64/seq64-load-rom.png){ .on-glb }

    ```linenums="0" hl_lines="2"
    │ ROM │ RomDesc │ Tools │ Help │
    ├─ Load...
    ├───────────────────
    ├─ Byte Ordering...
    ├───────────────────
    ├─ Save
    └─ Save As...
    ```

    To load your ROM into SEQ64 simply click the "ROM" button, then click the "Load..." option from the context menu that appears.

=== "Loading a ROM Description"
    ![](../assets/images/seq64/seq64-load-romdesc.png){ .on-glb }

    ```linenums="0" hl_lines="2"
    │ ROM │ RomDesc │ Tools │ Help │
          ├─ Load...
          ├────────────
          ├─ Save
          └─ Save As...
    ```

    To load your ROM description into SEQ64 simply click the "RomDesc" button, then click the "Load..." option from the context menu that appears.

!!! info
    If your ROM has byte ordering other than Big Endian then the ROM's internal title shown in the title bar of SEQ64 will be switched around. You can change the byte ordering SEQ64 uses, however your ROM should be Big Endian byte ordering otherwise data may end up misaligned.

-----