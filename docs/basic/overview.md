# Overview

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
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
- One pair of *Note On* and *Note Off* messages cannot intersect, or overlap, another pair of *Note On* and *Note Off* messages for a note of the same pitch.[^1]
- Max Delay value cannot go above a value of 32767 (0x7FFF)
- A section marker cannot intersect a pair of *Note On* and *Note Off* messages.

[^1]: While many DAWs allow for you to stack notes on top of other notes, or overlap your notes without immediate issues, the MIDI standard stresses it is invalid to send a second *Note On* message for a note with the same pitch in the same channel before a *Note Off* message is sent for the first *Note On* message. This is because of the way MIDI messages are interpreted, you can either use a pair of *Note On* and *Note Off* messages or a pair of *Note On* messages with the *Note On* message with a velocity of zero acts as a *Note Off* message. DAWs will attempt to connect the proper *Note On* and *Note Off* messages, however it will inevitably fail as *Note On* messages can be seen as both *Note On* or *Note Off*.

### Assigning Appropriate MIDI Program Numbers
In MIDI instruments are assigned by a control change command using the values 192 (0xC0) to 207 (0xCF). You can generally only have one single instrument per channel, however you can swap the instrument at any point using a MIDI program change message.

MIDI using the GM specification normally has 127 possible instruments with Channel 10 always being reserved for percussion instruments (instead of using a program change to individual drums you instead change the entire kit itself with individual drum sounds being assigned to note values 35 to 81), and uses a single instrument bank. However in *Ocarina of Time* and *Majora's Mask* there are multiple instrument banks commonly referred to as "audiobanks" (or soundfonts if you are working with decomp) and setting instruments depends entirely on the instrument bank you are using. In vanilla audiobanks there will almost always be 1 (0x00) to 16 (0x0F) instruments with instrument 126 (0x7E) assigning the sound effects to a channel and instrument 127 (0x7F) assigning the percussion kit to a channel. Some audiobanks have less instruments, or different sound effects, or different percussion kits.

??? info "Drums and Sound Effects"
    Drums and sound effects in *Ocarina of Time* and *Majora's Mask* work almost identically to how they do in MIDI with different values corresponding to different individual drum sounds. The only difference is hat there is a single percussion kit per audiobank and is assigned to program 127 (0x7F) instead of being assigned to a specific channel.

To properly assign the instruments you want you will need to find which instrument in the audiobank you are using corresponds to the equivalent MIDI program value. If you need to know which audiobank has which instruments, you can use the [vanilla audiobank references](../../vanilla-reference/audiobanks){ target="__blank" }<small>:material-open-in-new: </small> wiki page.

## Instrument Types
In *Ocarina of Time* and *Majora's Mask* there are two different types of instruments:

1. Channel-Based Instruments
2. Key-Based Instruments

### Channel-Based Instruments
Channel-based instruments, commonly referred to as just simply "Instruments", are instruments that assign three samples to three different note regions. The low sample occupies the note region from note 0 (C0) to the note specified by the low-mid region split inside the audiobank, the mid or normal sample occupies the note region from the note specified by the low-mid region split to the note specified by the mid-high region split inside the audiobank, and the high sample occupies the note region from the note specified by the mid-high region split to note 127 (G10). Each sample is automatically pitch shifted with the starting pitch determined by the tuning float value.

### Key-Based Instruments
Key-based instruments, commonly referred to as "Drums" and "Sound Effects", are instruments that assign a single sample file to each individual key within the range of note 21 (A1) to note 84 (C7). Each sample plays at the exact pitch determined by the tuning float value.

### Synth Wave Instruments
Also known as "chiptune" instruments, the synth wave instruments are a set of instruments available at all times no matter what audiobank is assigned to your sequence as they are special instruments with sample data assigned to very specific instrument slots (overwriting these slots with other instruments gives priorioty to audiobank instruments first, and synth waves second). There is a section about these instruments and how to access them available in the vanilla audiobank reference wiki page.

## Common SEQ64 Errors
=== "Overlapping Notes"
    For a channel containing overlapping or stacked notes, SEQ64 will give the following error in the console window or debug output when importing a MIDI file: 
    
    - `Note off (ch=# note=# time=#) received for note that is not on!`

=== "Voice Limit"
    For a channel containing more than four voices sounding at once, SEQ64 will give the following error in the console window or debug output when importing a MIDI file: 
    
    - `Channel # has more than 4 notes on at a time (at t=#)!`

Common SEQ64 Errors

- `Warning, extremely short note (pitch #, chn #, quarter note~), may be dropped or corrupt nearby note on/offs!`
- `Section boundary (e.g. loop point) in the middle of a note, note # channel #! Cutting off the note!`
- `Trying to fix section boundary in middle of note failed, broken sequence!`
- `Duplicate note on in chan # t=#, ignoring`
- `Channel # has more than # notes on at a time (at t=#)!`
- `Note off (ch=# note=# time=#) received for note that is not on!`
- `Chan # lyr # track has # (odd number of) events!`
- `No Master Volume sysex command in the MIDI, adding default 0x##`
- `Multiple cc command # (channel # timestamp # first cc #) missing required secondary CC #, setting to zero!`
- `Ran off end of track looking for note off!`
- `Note Off out of order! Cancelling track import!`
- `Note On out of order! Cancelling track import!`
- `Zero-length note with no delay afterwards in chn # ly # at t=#, discarding!`
- `Zero-length note in chn # ly # at t=#! Making small length instead...`
- `No [action] command defined in stype [stype] with all the needed parameters!`
- `Want: [idMeaning] value [idValue]`

## MIDI Note Division Tables
Listed below are notes with their corresponding tick values at common MIDI resolutions.

===+ "48 PPQN"
    | Regular Note | MIDI Ticks | Dotted Note | MIDI Ticks | Triplet | MIDI Ticks |
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | Whole Note | 192 | Dotted Whole | 288 | Whole Triplet | 128 |
    | Half Note | 96 | Dotted Half | 144 | Half Triplet | 64 |
    | Quarter Note | 48 | Dotted Quarter | 72 | Quarter Triplet | 32 | 
    | Eighth Note | 24 | Dotted Eighth | 36 | Eighth Triplet | 16 |
    | 16th Note | 12 | Dotted 16th | 18 | 16th Triplet| 8 |
    | 32nd Note | 6 | Dotted 32nd | 9 | 32nd Triplet | 4 |
    | 64th Note | 3 | Dotted 64th | — | 64th Triplet | 2 |

    !!! info "Omitted Values"
        Any values that are omitted are values that are not cleanly divisible by their longer counterpart.

=== "96 PPQN"
    | Regular Note | MIDI Ticks | Dotted Note | MIDI Ticks | Triplet | MIDI Ticks |
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | Whole Note | 384 | Dotted Whole | 576 | Whole Triplet | 256 |
    | Half Note | 192 | Dotted Half | 288 | Half Triplet | 128 |
    | Quarter Note | 96 | Dotted Quarter | 144 | Quarter Triplet | 64 | 
    | Eighth Note | 48 | Dotted Eighth | 72 | Eighth Triplet | 32 |
    | 16th Note | 24 | Dotted 16th | 36 | 16th Triplet| 16 |
    | 32nd Note | 12 | Dotted 32nd | 18 | 32nd Triplet | 8 |
    | 64th Note | 6 | Dotted 64th | 9 | 64th Triplet | 4 |

    !!! info "Omitted Values"
        Any values that are omitted are values that are not cleanly divisible by their longer counterpart.

=== "120 PPQN"
    | Regular Note | MIDI Ticks | Dotted Note | MIDI Ticks | Triplet | MIDI Ticks |
    | :-: | :-: | :-: | :-: | :-: | :-: |
    | Whole Note | 480 | Dotted Whole | 720 | Whole Triplet | 320 |
    | Half Note | 240 | Dotted Half | 360 | Half Triplet | 160 |
    | Quarter Note | 120 | Dotted Quarter | 180 | Quarter Triplet | 80 | 
    | Eighth Note | 60 | Dotted Eighth | 90 | Eighth Triplet | 40 |
    | 16th Note | 30 | Dotted 16th | 45 | 16th Triplet| 20 |
    | 32nd Note | 15 | Dotted 32nd | — | 32nd Triplet | 10 |
    | 64th Note | 8 | Dotted 64th | — | 64th Triplet | 5 |

    !!! info "Omitted Values"
        Any values that are omitted are values that are not cleanly divisible by their longer counterpart.

To create a note division table for a PPQN or tick value not in the above tables take the regular quarter note tick value of the desired PPQN then:

1. Use the following formula to find the longer duration note's tick values:
    - $n * 2$
2. Use the following formula to find the shorter duration note's tick values:
    - $n / 2$
3. Use the following formula to find the dotted note values:
    - $(n / 2) + n$
4. Use the following formula to find the triplet note values:
    - $n - (n /3 )$

Where *n* is the value of the regular note you wish to use. As an example, if *n* equals 48, then a half note would be 96, an eighth note would be 24, a dotted quarter note would be 72, and a quarter triplet would be 32.

!!! info "Nintendo 64 Native PPQN"
    Sequences in *Ocarina of Time* and *Majora's Mask* have a native resolution of 48 PPQN. The default PPQN of Fruity Loops Studio is 96 PPQN, and the default PPQN of Sekaiju is 120 PPQN. It is easier for a MIDI file to be converted into a sequence if it is already at the native PPQN of *Ocarina of Time* and *Majora's Mask* than to have SEQ64 convert it to 48 PPQN.

!!! warning "Note Corruption"
    It is recommended not to have notes shorter than a duration of 4 ticks at 48 PPQN in your sequence as notes that are too short can end up corrupting other notes in the sequence; this will cause issues with dropped channels