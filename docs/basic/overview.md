# Overview

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

## Summary of Music Creation

placeholder


## Sequence Limitations
1. Tempo cannot go above a value of 255 (0xFF).
    - Because the data that stores tempo information is an 8 bit unsigned integer (u8) value, the tempo command has a limit of 255 (0xFF) for sequences; it cannot go any higher.
2. Volume cannot go above a value of 255 (0xFF).
    - Because the data that stores volume information is an 8 bit unsigned integer (u8) value, the volume commands have a limit of 255 (0xFF) for sequences; it cannot go any higher. In MIDI, the data that stores volume information is a 7 bit unsigned integer value. Volume messages have a limit of 127 (0x7F) for MIDI; it cannot go any higher.
3. Instrument assignments cannot go above a value of 255 (0xFF).
    - Because the data that stores instrument assignment information is an 8 bit unsigned integer (u8) value, the instrument change command has a limit of 255 (0xFF) for sequences; it cannot go any higher. In MIDI, the data that stores program assignment information is a 7 bit unsigned integer value. Program change messages have a limit of 127 (0x7F) for MIDI; it cannot go any higher.
3. Channels are polyphonic; however, only a maximum of four voices (played notes) of differing pitches can play within a single channel at any given time.
4. One pair of *Note On* and *Note Off* messages cannot intersect, or overlap, another pair of *Note On* and *Note Off* messages for a note of the same pitch.[^1]
5. Delay values cannot go above a value of 32767 (0x7FFF)
    - Because the data that stores delay frames is a 16 bit unsigned integer (u16) value, the delay command has a limit of 32767 (0x7FFF) for sequences; it cannot go any higher.
6. A MIDI marker message cannot intersect a pair of *Note On* and *Note Off* messages.

[^1]: While many DAWs allow you to stack notes on top of other notes, or overlap your notes without immediate issues, the MIDI standard stresses it is invalid to send a second *Note On* message for a note of the same pitch in the same channel before a *Note Off* message is sent for the first *Note On* message. This is because of the way MIDI messages are interpreted, you can either use a pair of *Note On* and *Note Off* messages or a pair of *Note On* messages with the *Note On* message with a velocity of zero acts as a *Note Off* message. Many DAWs will attempt to connect the proper *Note On* and *Note Off* messages; however, it will inevitably fail as *Note On* messages can be seen as both *Note On* or *Note Off*.

### Assigning Appropriate MIDI Program Numbers
In MIDI, instruments are assigned by a control change command using the values 192 (0xC0) to 207 (0xCF). You can generally only have one single instrument per channel. However, you can swap the instrument at any point using a MIDI program change message.

MIDI instrument banks using the GM specification normally contain 127 possible instruments with MIDI channel 10 always being reserved for percussion kits, where instead of using a program change to individual drums, you instead change the entire percussion kit itself with individual drum sounds being assigned to different keys on the virtual MIDI piano (the range of possible samples is from keys 35 to 81). Instrument banks in MIDI contain those 127 instruments and percussion kits within a single instrument bank. However, in *Ocarina of Time* and *Majora's Mask* there are multiple instrument banks commonly referred to as "audiobanks" or "soundfonts". Setting instruments depends entirely on the audiobank you are using; in vanilla audiobanks there will almost always only be 1 (0x00) to 16 (0x0F) instruments with instrument 126 (0x7E) assigning the sound effects to a channel and instrument 127 (0x7F) assigning the percussion kit to a channel. Audiobanks can contain up to 255 (0xFF) instruments that may be assigned to a channel. However, instruments 126 (0x7E) and 127 (0x7F) are always reserved for sound effects and percussion kits respectively.

Some audiobanks may have fewer instruments, different sound effects, or contain entirely different percussion kits; the reason for breaking audiobanks into smaller sub-banks is used as a way to reduce the amount of RAM required by the audio system in *Ocarina of Time* and *Majora's Mask*.

??? info "Drums and Sound Effects"
    Drums and sound effects in *Ocarina of Time* and *Majora's Mask* work almost identically to how they do in MIDI with different values corresponding to different individual drum sounds. The only difference is that there is a single percussion kit per audiobank, and it is assigned to program 127 (0x7F) instead of being assigned to a specific MIDI channel.

To properly assign the instruments you want, you will need to determine which instrument inside the audiobank you are using corresponds to the equivalent MIDI program value. If you need to know which audiobank has which instruments, you can use the [vanilla audiobank references](../../vanilla-reference/audiobanks){ target="__blank" }<small>:material-open-in-new: </small> wiki page.

## Instrument Types
In *Ocarina of Time* and *Majora's Mask* there are two different types of instruments:

1. Channel-Based Instruments
2. Key-Based Instruments

### Channel-Based Instruments
Channel-based instruments, commonly referred to as just simply "Instruments", are instruments that assign three different samples to three different note regions on the virtual MIDI piano. The low sample occupies the note region from note 0 (C0) to the note specified by the low-mid region split inside the audiobank, the mid or normal sample occupies the note region from the note specified by the low-mid region split to the note specified by the mid-high region split inside the audiobank, and the high sample occupies the note region from the note specified by the mid-high region split to note 127 (G10). Each sample is automatically pitch shifted with the starting pitch determined by the tuning float value.

#### Special Instruments
In *Ocarina of Time* and *Majora's Mask*, there exists a special set of channel-based instruments commonly referred to as "synth wave", "waveform", or "chiptune" instruments. These instruments have their sample data stored outside any audiobanks; this makes them available to use at all times, regardless of the audiobank currently being used by a sequence. More detailed information on these instruments, and how to assign them to a channel can be found on the [vanilla audiobank reference](../vanilla-reference/audiobanks/#audiobank-reference-waveform-instruments){ target="__blank"}<small>:material-open-in-new: </small> wiki page.

### Key-Based Instruments
Key-based instruments, commonly referred to as "Drums" and "Sound Effects", are instruments which have a single sample assigned to a single key on the virtual MIDI piano. Key-based instruments, despite what the name "key-based" may imply, are used in channels just like channel-based instruments are. However, the way their data is handled is the basis for their name. Key-based instruments as previously stated assign a single sample, ADSR envelope, and pan value to a single piano key in the virtual MIDI piano from the note range 21 (A1) to 85 (C7); the way key-based instruments are tuned in *Ocarina of Time* and *Majora's Mask* is different as well.

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
        Any omitted values are values which are not cleanly divisible by their longer-duration counterparts.

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
        Any omitted values are values which are not cleanly divisible by their longer-duration counterparts.

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
        Any omitted values are values which are not cleanly divisible by their longer-duration counterparts.

To create a note division table for a PPQN or tick value not in the above tables, take the regular quarter note tick value of the desired PPQN, then:

1. Use the following formula to find the longer duration note's tick values:
    - $n * 2$
2. Use the following formula to find the shorter duration note's tick values:
    - $n / 2$
3. Use the following formula to find the dotted note values:
    - $(n / 2) + n$
4. Use the following formula to find the triplet note values:
    - $n - (n / 3)$

Where *n* is the value of the regular note you wish to use. As an example, if *n* equals 48, then a half note would be 96, an eighth note would be 24, a dotted quarter note would be 72, and a quarter triplet would be 32.

!!! info "Nintendo 64 Native PPQN"
    Sequences in *Ocarina of Time* and *Majora's Mask* have a native resolution of 48 PPQN. The default PPQN of Fruity Loops Studio is 96 PPQN, and the default PPQN of Sekaiju is 120 PPQN. It is easier for a MIDI file to be converted into a sequence if it is already at the native PPQN of *Ocarina of Time* and *Majora's Mask* than to have SEQ64 convert it to 48 PPQN.

!!! warning "Note Corruption"
    It is recommended not to have notes shorter than a duration of 4 ticks at 48 PPQN in your sequence as notes that are too short can end up corrupting other notes in the sequence; this may cause issues with notes being dropped by a channel during playback.