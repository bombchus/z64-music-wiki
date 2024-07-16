# Advanced Tools and Resources

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

This page is where download links to the advanced tools and resources used in custom music creation for *Ocarina of Time* and *Majora's Mask* are available.

!!! alert "Procuring a ROM"
    This page, as well as the wiki itself, can not and will not supply any ROM files or links to any ROM files for *Ocarina of Time* and *Majora's Mask* as it is illegal to do so. This wiki is not meant for piracy of copyrighted materials, it is meant to help those interested in creating custom music for *Ocarina of Time* and *Majora's Mask* learn the process and other details related to music creation for the games.

## Advanced Custom Music Creation Tools
Below is a list of tools that are used for creating music for *Ocarina of Time* and *Majora's Mask*. It is recommended to download all the tools needed right now to save on needing to go back and forth between downloading and visiting the relevant wiki pages.

### Links to Advanced Tools
- #### **Sample Creation Tools**
    - **[z64audio](../assets/tools/z64audio%20with%20CLI%20Script.zip){ target="_blank" }** <small> :material-open-in-new: </small>
    - **[ADPCM Predictor Conversion Scripts](../assets/tools/ADPCM%20Predictor%20BIN%20to%20XML.zip){ target="_blank" }** <small> :material-open-in-new: </small>`xml output`
    - **[ADPCM Predictor Conversion Scripts](../assets/tools/ADPCM%20Predictor%20BIN%20to%20C.zip){ target="_blank" }** <small> :material-open-in-new: </small>`c output`
- #### **N64 Soundlist Tool**
    - **[N64 Soundlist Tool](https://github.com/jombo23/N64-Tools){ target="_blank" }** <small> :material-open-in-new: </small>
- #### **Audio Editing Tools**
    - **[Polyphone](https://www.polyphone-soundfonts.com/download){ target="_blank" }** <small> :material-open-in-new: </small> <small>recommended</small>
    - **[Audacity](https://www.audacityteam.org/download/){ target="_blank" }** <small> :material-open-in-new: </small>
- #### **Tuning Float Calculator**
    - **[Tuning Float Calculator](../assets/tools/Tuning%20Float%20Calculator.zip){ target="_blank" }** <small>v2024.07.07</small>
- #### **ADSR Converter**
    - **[Z64 ADSR Converter](../assets/tools/ADSR%20Converter.zip){ target="_blank" }** <small>v2024.07.07</small>
- #### **Audiobank Templates**
    - **[Audiobank Templates](#){ target="_blank" }** <small> :material-open-in-new: </small> <small>recommended</small>

### Brief Summary of Tools
=== "Sample Creation Tools"
    The **Sample Creation Tools** are required for converting `.wav` files to `.bin` (or `.zsound`) sample files and obtaining codebook and loopbook ADPCM predictor data.

=== "N64 Soundlist Tool"
    **N64 Soundlist Tool** is used to rip `.bin` (or `.zsound`) sample files and obtain their codebook and loopbook ADPCM predictor data — as well as other instrument, drum, and sound effect data — from Nintendo 64 games.

=== "Polyphone"
    **Polyphone** is *optional*, but can be used to obtain `.wav` files from `.sf2` (soundfont) files to convert into a `.bin` (`.zsound`) file with the "Sample Creation Tools". Polyphone can also edit `.wav` files in a few different ways, such as resampling, pitch-shifting, or setting loop points.

=== "Audacity"
    **Audacity** is *optional*, but is a powerful audio editing tool. Audacity can edit audio files in many different ways, such as resampling, pitch-shifting, or trimming unneeded portions of audio.

=== "Tuning Float Calculator"
    The **Tuning Float Calculator** is *optional*, but it can find the tuning float value for a sampled instrument, drum, or sound effect. The tuning float value for samples goes inside of an audiobank and adjusts the tuning of a sample.

    !!! warning "Windows Defender False Flagging"
        Because the Tuning Float Calculator is an unsigned executable file, Windows Defender may false flag it as malware (`Trojan:Win32/Wacatac.B!ml`). To remedy this, follow the steps below:

        > 1. Open Windows Defender and navigate to "Virus & threat protection".
        > 2. In "Virus & threat protection", navigate to "Virus & threat protection settings > Manage settings".
        > 3. In "Virus & threat protection settings", navigate to "Exclusions > Add or remove exclusions".
        > 4. In "Exclusions", click the "+ Add an exclusion" button and locate the file or the folder the file is in to exclude.

        It is not recommended to exclude an entire folder unless everything related to Music Creation is being kept in a single folder. Whenever possible, always exclude trusted single files. The application does not contain any malicious code. If that statement is untrustworthy, then do not download it. And if it is already downloaded, then do not add a Windows Defender exclusion for it.

=== "ADSR Converter"
    The ADSR Converter is optional, but it can convert a soundfont's (`.sf2`) ADSR data into ADSR data compatible with Ocarina of Time and Majora's Mask.

    !!! warning "Windows Defender False Flagging"
        Because the Tuning Float Calculator is an unsigned executable file, Windows Defender may false flag it as malware (`Trojan:Win32/Wacatac.B!ml`). To remedy this, follow the steps below:

        > 1. Open Windows Defender and navigate to "Virus & threat protection".
        > 2. In "Virus & threat protection", navigate to "Virus & threat protection settings > Manage settings".
        > 3. In "Virus & threat protection settings", navigate to "Exclusions > Add or remove exclusions".
        > 4. In "Exclusions", click the "+ Add an exclusion" button and locate the file or the folder the file is in to exclude.

        It is not recommended to exclude an entire folder unless everything related to Music Creation is being kept in a single folder. Whenever possible, always exclude trusted single files. The application does not contain any malicious code. If that statement is untrustworthy, then do not download it. And if it is already downloaded, then do not add a Windows Defender exclusion for it.

=== "Audiobank Templates"
    The **Audiobank Templates** are *optional*, and made for the creation of sampled instruments, drums, and sound effects. SEQ64 or a text editor capable of opening and editing `.xml` files can edit the placeholder data in the template files. There are templates available for instruments, drums, or sound effects.

    ??? tip "Recommendation"
        SEQ64 is not recommended for audiobank editing, a text editor capable of editing `.xml` files is instead recommended. There is a learning curve to editing audiobank `.xml` files. However, editing audiobanks in a text editor will bypass any bugs that SEQ64 can introduce during editing.

-----