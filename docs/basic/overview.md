# Overview

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

## Summary of Music Creation

placeholder


## Sequence Limitations
- Tempo cannot go above a value of 255 (0xFF).
- Volume cannot go above a value of 255 (0xFF).
    - MIDI cannot go above a value of 127 (0x7F).
- Program changes cannot go above a value of 255 (0xFF).
    - MIDI cannot go above a value of 127 (0x7F).
- Channels are polyphonic, however only a maximum of four voices, or notes, of differing pitches can be played at any given time in a single channel.
- One pair of *`Note On`* and *`Note Off`* commands cannot intersect, or overlap, another pair of *`Note On`* and *`Note Off`* commands for a note of the same pitch.[^1]

[^1]: placeholder

!!! info "SEQ64 Errors"
    === "Overlapping Notes"
        For a channel containing overlapping notes, SEQ64 will give the following error in the console window or debug output when importing a MIDI file: *`Note off (ch=# note=# time=#) received for note that is not on!`*
    
    === "Voice Limit"
        For a channel containing more than four voices sounding at once, SEQ64 will give the following error in the console window of debug output when importing a MIDI file: *`Channel # has more than 4 notes on at a time (at t=#)`*

### Assigning Appropriate MIDI Program Numbers
In MIDI instruments are assigned by a control change command using the values 192 (0xC0) to 207 (0xCF). You can generally only have one single instrument per channel, though you can swap the instrument at any point using a MIDI program change command.

MIDI using the GM specification normally has 127 possible instruments with Channel 10 always being reserved for percussion instruments (instead of using a program change to individual drums you instead change the entire kit itself with individual drum sounds being assigned to note values 35 to 81), and uses a single instrument bank. However in *Ocarina of Time* and *Majora's Mask* there are multiple instrument banks (called audiobanks, or soundfonts if you're working with decomp) and setting instruments depends entirely on the audiobank you are using. In vanilla audiobanks there will almost always be 1 (0x00) to 16 (0x0F) instruments with instrument 126 (0x7E) assigning the sound effects to a channel and instrument 127 (0x7F) assigning the percussion kit to a channel. Some audiobanks have less instruments, or different sound effects, or different percussion kits.

??? info "Percussion Kits and Sound Effects"
    Percussion kist and sound effects in *Ocarina of Time* and *Majora's Mask* work almost identically to how they do in MIDI with different values corresponding to different individual drum sounds. The only difference is hat there is a single percussion kit per audiobank and is assigned to program 127 (0x7F) instead of being assigned to a specific channel.

To properly assign the instruments you want you will need to find which instrument in the audiobank you are using corresponds to the equivalent MIDI program value. If you need to know which audiobank has which instruments, you can use the [vanilla audiobank references](../../vanilla-reference/audiobanks) wiki page.

## Instrument Types
In *Ocarina of Time* and *Majora's Mask* there are three different types of instrument types:

1. Instruments
2. Drums
3. Sound Effects

### Instruments
Instruments assign three different samples to different MIDI keyboard regions, the low sample starts from note index 0 and moves all the way up until the first keymap split, the mid sample occupies the place between both keymap splits, and the high sample starts from the second keymap split and moves all the way up to the last note index 127. Each sample gets automatically pitch shifted inside its region.

### Drums and Sound Effects
Drums and sound effects assaign a single sample to each individual key within the range of note 21 (A1) to note 84 (C7). Each sample plays at the exact pitch determined by the tuning float value.

### Synth Wave Instruments
Also known as "chiptune" instruments, the synth wave instruments are a set of instruments available at all times no matter what audiobank is assigned to your sequence as they are special instruments with sample data assigned to very specific instrument slots (overwriting these slots with other instruments gives priorioty to audiobank instruments first, and synth waves second). There is a section about these instruments and how to access them available in the vanilla audiobank reference wiki page.