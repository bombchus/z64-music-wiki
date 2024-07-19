# Music Creation Overview

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

## Summary of Music Creation
To create custom music in *Ocarina of Time* and *Majora's Mask*, a sequence file the audio engine can play back in real-time mut be used. Sequences are a form of compressed MIDI created by Nintendo for the Nintendo 64. Sequences are a set of commands, or instructions, that tell the audio engine what sample files to play, at what pitch, at what time, and how fast to play through the sequence. Due to the similarities between MIDI sequences and Nintendo 64 sequences, the most common way to create a sequence for *Ocarina of Time* and *Majora's Mask* is to convert a MIDI song into a sequence using SEQ64.

There are other ways to create a sequence aside from MIDI; however, using a MIDI sequence is the easiest due to their numerous similarities, and the ability to preview a song.

!!! info "Is it possible to use MP3 files?"
    It is not possible to take an MP3 file and play it back in real-time in *Ocarina of Time* and *Majora's Mask*. While both *Ocarina of Time* and *Majora's Mask* are capable of "streaming" audio, the only games on the Nintendo 64 known to be capable of MP3 decoding are *Conker's Bad Fur Day* and *Perfect Dark*.

## Sequence Limitations
Below is a list of technical limitations for sequences to be aware of when creating music for *Ocarina of Time* and *Majora's Mask*:

1. Like MIDI, a sequence can only have up to 16 (0x0F) channels.
    - Multiple tracks may be assigned to a single channel in MIDI; however, they are subject to the channel limitations sequences have.
2. A sequence's tempo cannot go above a value of 255 (0xFF).
    - Because the data that stores tempo information is an 8 bit unsigned integer (u8) value, the tempo command has a limit of 255 (0xFF) for sequences; it cannot go any higher.
3. A sequence's master, channel, and expression volume cannot go above a value of 255 (0xFF).
    - Because the data that stores volume information is an 8 bit unsigned integer (u8) value, the volume commands have a limit of 255 (0xFF) for sequences; it cannot go any higher. In MIDI, the data that stores volume information is a 7 bit unsigned integer value. Volume messages have a limit of 127 (0x7F) for MIDI; it cannot go any higher.
4. A sequence's instrument assignment values cannot go above a value of 255 (0xFF).
    - Because the data that stores instrument assignment information is an 8 bit unsigned integer (u8) value, the instrument change command has a limit of 255 (0xFF) for sequences; it cannot go any higher. In MIDI, the data that stores program assignment information is a 7 bit unsigned integer value. Program change messages have a limit of 127 (0x7F) for MIDI; it cannot go any higher.
5. Like MIDI, channels in a sequence are polyphonic; however, only a maximum of four voices of differing pitches can play within a single channel at any given time.
6. Like MIDI, one pair of *Note On* and *Note Off* messages cannot intersect, or overlap, another pair of *Note On* and *Note Off* messages for a note of the same pitch in a sequence.
    - While a DAW may allow stacked notes or overlapped notes without immediate issue, it is invalid to send a second *Note On* message for a note of the same pitch in the same channel before a *Note Off* message is sent for the first *Note On* message. In MIDI, a *Note On* message with a velocity of zero is interpreted as a *Note Off* message, and while many DAWs will attempt to properly pair note messages, they will fail.
7. A sequence's delay values cannot go above a value of 32767 (0x7FFF)
    - Because the data that stores delay frames is a 16 bit unsigned integer (u16) value, the delay command has a limit of 32767 (0x7FFF) for sequences; it cannot go any higher.
8. A MIDI marker message cannot intersect a pair of *Note On* and *Note Off* messages.
    - placeholder

<style>
/* MOVED TO A NEW PAGE?
## Assigning Instruments
In MIDI, instruments are assigned by a control change command using the values 192 (0xC0) to 207 (0xCF). Generally only a single instrument can be assigned per channel. However, instruments can be swapped at any point using a MIDI program change message.

MIDI instrument banks using the GM specification normally contain 127 possible instruments with MIDI channel 10 always being reserved for percussion kits, where instead of using a program change to individual drums, it instead changes the entire percussion kit itself with individual drum sounds being assigned to different keys on the virtual MIDI piano (the range of possible samples is from keys 35 to 81). Instrument banks in MIDI contain those 127 instruments and percussion kits within a single instrument bank. However, in *Ocarina of Time* and *Majora's Mask* there are multiple instrument banks commonly referred to as "audiobanks" or "soundfonts". Setting instruments depends entirely on the audiobank used; in vanilla audiobanks there will almost always only be 1 (0x00) to 16 (0x0F) instruments with instrument 126 (0x7E) assigning the sound effects to a channel and instrument 127 (0x7F) assigning the percussion kit to a channel. Audiobanks can contain up to 255 (0xFF) instruments that may be assigned to a channel. However, instruments 126 (0x7E) and 127 (0x7F) are always reserved for sound effects and percussion kits respectively.

Some audiobanks may have fewer instruments, different sound effects, or contain entirely different percussion kits; the reason for breaking audiobanks into smaller sub-banks is used as a way to reduce the amount of RAM required by the audio system in *Ocarina of Time* and *Majora's Mask*.

??? info "Drums and Sound Effects"
    Drums and sound effects in *Ocarina of Time* and *Majora's Mask* work almost identically to how they do in MIDI with different values corresponding to different individual drum sounds. The only difference is that there is a single percussion kit per audiobank, and it is assigned to program 127 (0x7F) instead of being assigned to a specific MIDI channel.

To properly assign the instruments a sequence will use, it is necessary to determine which instrument inside the audiobank used corresponds to the equivalent MIDI program value. The [vanilla audiobank references](../../vanilla-reference/audiobanks){ target="__blank" }<small>:material-open-in-new: </small> wiki page contains a list of all audiobanks and their corresponding instruments and instrument assignment values.
*/

/*
THE GREAT REWRITE WILL BE FINISHED EVENTUALLY!!!

To use instruments in a MIDI channel a MIDI program change message must be sent to the MIDI channel. Each MIDI channel may only have a single instrument assigned to it at a time. However, the instrument used by a MIDI channel can be changed at any time. To change the instrument a MIDI channel uses, another MIDI program change message must be sent to the MIDI channel. Percussion kits may only be used in MIDI channel 10.

To use instruments in a sequence channel the sequence command "0xC1" must be sent to the sequence channel. Each sequence channel may only have a single instrument assigned to it at a time. However, the instrument used by a sequence channel can be changed at any time. To change the instrument a sequence channel uses, another sequence command "0xC1" must be sent to the sequence channel. Percussion kits have an instrument assignment value of 0x7F (127) in Ocarina of Time and Majora's Mask.
*/

/* MOVED TO NEW PAGE?
### Assigning Instruments in MIDI
In MIDI, instruments and percussion kits are assigned to a channel by sending a MIDI program change message to that channel. There may only be a single instrument or percussion kit assigned to a channel at any time. However, the channel's assigned instrument or percussion kit can be changed at any point by sending another MIDI program change message to the channel. MIDI program change messages have two bytes. The first byte of a MIDI program change message is the status byte with values ranging from 0xC0 to 0xCF. The first half-byte determines the message type; the second half-byte points to the MIDI channel the message is sent to. The status byte determines the channel the message is sent to. The second byte of a MIDI program change message is the data byte with values ranging from 0x00 (0) to 0x7F (127). The data byte determines what instrument or percussion kit the channel will use. Instruments may be set in any MIDI channel, while percussion kits may only be set in MIDI channel 10 as MIDI channel 10 is reserved solely for percussion kits.

#### Using Percussion Kits
In MIDI, percussion kits are only available in MIDI channel 10.

In MIDI, instruments and percussion kits are stored inside of banks. In the General MIDI 1.0 specification (which does not support MIDI bank select messages), bank 0 (0x00) contains only instruments with bank 128 (0x80) containing only percussion kits. Bank 0 is the default bank for all MIDI channels with bank 128 as the default bank in MIDI channel 10.

### Assigning Instruments in Sequences
In *Ocarina of Time* and *Majora's Mask*, instruments, sound effects, and percussion kits are assigned to a channel with the sequence command 0xC1 (Set Instrument). There may only be a single instrument, sound effects, or percussion kit assigned to a channel at any given time. However, the channel's assigned instrument, sound effects, or percussion kit can be changed at any point by sending another sequence command of 0xC1 (Set Instrument). The sequence command 0xC1 (Set Instrument) only has a data byte with values ranging from 0x00 (0) to 0xFF (255). This data byte determines what instrument, sound effects, or percussion kit the channel will use. Instruments, sound effects, and percussion kits may be set in any sequence channel. However, unlike MIDI, sequence command 0xC1's instrument assignments for values 126 (0x7E) and 127 (0x7F) are reserved for sound effects and percussion kits respectively.

In Ocarina of Time and Majora's Mask, instruments, sound effects, and percussion kits are stored inside of banks (commonly referred to as "audiobanks" or "soundfonts"). Unlike MIDI, *Ocarina of Time* and *Majora's Mask* store instruments, sound effects, and percussion kits inside of a single bank. And while a sequence command for changing banks does exist, it can only load banks that are currently loaded into RAM.

### Assigning Appropriate MIDI Instruments
Instruments in MIDI are not one-to-one with instruments in *Ocarina of Time* and *Majora's Mask*. In MIDI, the "Strings" instrument has a MIDI program change value of 48 (0x30). In *Ocarina of Time* and *Majora's Mask*, the "Strings" instrument has an instrument assignment value dependent on the bank used by a sequence. Unlike in MIDI, in *Ocarina of Time* and *Majora's Mask*, it is also possible that the "Strings" instrument may not be present in a bank at all. As an example, in *Ocarina of Time* and *Majora's Mask*, bank 0x03 assigns the "Strings" instrument to a value of 10 (0x0A) or 11 (0x0B), while bank 0x02 does not contain the "Strings" instrument at all in either game and only contains ambient nature sounds. So, to make sure instruments, sound effects, and percussion kits are assigned to the proper channel in a sequence, it is required to adjust MIDI program change message values to match the assignment value of the counterpart chosen in the *Ocarina of Time* and *Majora's Mask* bank being used.
*/
</style>

## Instrument Types
In *Ocarina of Time* and *Majora's Mask* there are two different types of instruments:

1. Channel-Based Instruments
2. Key-Based Instruments

### Channel-Based Instruments
Channel-based instruments, commonly referred to as just simply "instruments", are instruments that assign three different samples to three different note regions on the virtual MIDI piano. The low sample occupies the note region from note 0 (C0) to the note specified by the low-mid region split inside the audiobank, the mid or normal sample occupies the note region from the note specified by the low-mid region split to the note specified by the mid-high region split inside the audiobank, and the high sample occupies the note region from the note specified by the mid-high region split to note 127 (G10). Each sample is automatically pitch shifted with the starting pitch determined by the tuning float value.

#### Special Instruments
In *Ocarina of Time* and *Majora's Mask*, there exists a special set of channel-based instruments commonly referred to as "synth wave", "waveform", or "chiptune" instruments. These instruments have their sample data stored outside any audiobanks; this makes them available to use at all times, regardless of the audiobank currently being used by a sequence. More detailed information on these instruments, and how to assign them to a channel can be found on the [vanilla audiobank reference](../vanilla-reference/audiobanks/#audiobank-reference-waveform-instruments){ target="__blank"}<small>:material-open-in-new: </small> wiki page.

### Key-Based Instruments
Key-based instruments, commonly referred to as "drums" and "sound effects", are instruments which have a single sample assigned to a single key on the virtual MIDI piano. Key-based instruments, despite what the name "key-based" may imply, are used in channels just like channel-based instruments are. However, the way their data is handled is the basis for their name. Key-based instruments as previously stated assign a single sample, ADSR envelope, and pan value to a single piano key in the virtual MIDI piano from the note range 21 (A1) to 85 (C7); the way key-based instruments are tuned in *Ocarina of Time* and *Majora's Mask* is different as well.

## Instrument Ranges
Instruments in *Ocarina of Time* and *Majora's Mask* are limited in their range. The Nintendo 64 Programming Manual states the following: "The pitch shifter resamples the resulting data (up one octave, down any number of octaves) to the desired pitch."[^1] However, the playback code given to the synthesis driver — which is responsible for pitch shifting sample data — in *Ocarina of Time* and *Majora's Mask* allows for an increase of two octaves instead of just a single octave:

=== ":material-code-braces:&nbsp; C"
    ```c title="playback.c" linenums="0"
    void AudioPlayback_NoteSetResamplingRate(NoteSampleState* sampleState,
                                             f32 resamplingRateInput) {
        // Set the initial resampling rate to 0.0f
        f32 resamplingRate = 0.0f;


        // Determines if the given resampling rate is lower than 2.0f
        if (resamplingRateInput < 2.0f) {
              sampleState->bitField1.hasTwoParts = false;
              resamplingRate = CLAMP_MAX(resamplingRateInput, 1.99998f);

        // If the given resampling rate is higher than 2.0f the following happens
        } else {
            sampleState->bitField1.hasTwoParts = true;
            // If the given resampling rate is above 4.0f, cap the resampling rate to 2.0f
            if (resamplingRateInput > 3.99996f) {
                resamplingRate = 1.99998f;
            // If the resampling rate is not above 4.0f then set the resampling rate equal
            // to half the given resampling rate.
            } else {
                resamplingRate = resamplingRateInput * 0.5f;
            }
        }
        sampleState->frequencyFixedPoint = (s32)(resamplingRate * 32768.0f);
    }
    ```

If a note is above a sample's pitch cap, then it 

![](../assets/images/samples/piano-range-light.png#only-light){ .on-glb }
![](../assets/images/samples/piano-range-dark.png#only-dark){ .on-glb }

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

## MIDI Note Division Tables <small>move to separate page</small> { #midi-note-division-tables data-toc-label="MIDI Note Division Tables" }
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

Where *n* is the value of the regular note to use. As an example, if *n* equals 48, then a half note would be 96, an eighth note would be 24, a dotted quarter note would be 72, and a quarter triplet would be 32.

!!! info "Nintendo 64 Native PPQN"
    Sequences in *Ocarina of Time* and *Majora's Mask* have a native resolution of 48 PPQN. The default PPQN of FL Studio is 96 PPQN, and the default PPQN of Sekaiju is 120 PPQN. It is easier for a MIDI file to be converted into a sequence if it is already at the native PPQN of *Ocarina of Time* and *Majora's Mask* than to have SEQ64 convert it to 48 PPQN.

!!! warning "Note Corruption"
    It is recommended not to have notes shorter than a duration of 4 ticks at 48 PPQN in a sequence as notes that are too short can end up corrupting other notes in the sequence; this may cause issues with notes being dropped by a channel during playback.


## seq loop <small>move to separate page</small> { #seq-loop data-toc-label="seq loop" }
Section markers, commonly referred to as "loop points", placeholder.

When SEQ64 is creating sections in a sequence it looks specifically for MIDI meta message markers with a name of "section" and "loop".

=== "Section 1"
    ``` linenums="0" hl_lines="4-13"
    @Addr: Data         Command
    ————————————————————————————————————————————————————
    @0010: D7 8E DB     Initialize Channels
    @0013: 90 00 7D     Set Channel
    @0016: 91 00 F4     Set Channel
    @0019: 93 01 02     Set Channel
    @001C: 94 01 10     Set Channel
    @001F: 96 02 7F     Set Channel
    @0022: 97 02 8D     Set Channel
    @0025: 99 02 9B     Set Channel
    @0028: 9A 02 AB     Set Channel
    @002B: 9B 03 2C     Set Channel
    @002E: 9F 03 53     Set Channel
    @0031: DB 50        Set Volume (SysEx Master Volume)
    @0033: DD 64        Set Tempo
    @0035: FD 84 80     Delay [n] Frame(s)
    @0038: DD 50        Set Tempo
    @003A: FD 80 C0     Delay [n] Frame(s)
    @003D: 90 03 61     Set Channel
    @0040: 91 03 6D     Set Channel
    @0043: 93 03 80     Set Channel
    @0046: 94 04 07     Set Channel
    @0049: 96 05 E6     Set Channel
    @004C: 97 06 F1     Set Channel
    @004F: 99 07 01     Set Channel
    @0052: 9A 07 77     Set Channel
    @0055: 9B 09 48     Set Channel
    @0058: 9F 0A 04     Set Channel
    ```

=== "Section 2"
    ``` linenums="0" hl_lines="19-28"
    @Addr: Data         Command
    ————————————————————————————————————————————————————
    @0010: D7 8E DB     Initialize Channels
    @0013: 90 00 7D     Set Channel
    @0016: 91 00 F4     Set Channel
    @0019: 93 01 02     Set Channel
    @001C: 94 01 10     Set Channel
    @001F: 96 02 7F     Set Channel
    @0022: 97 02 8D     Set Channel
    @0025: 99 02 9B     Set Channel
    @0028: 9A 02 AB     Set Channel
    @002B: 9B 03 2C     Set Channel
    @002E: 9F 03 53     Set Channel
    @0031: DB 50        Set Volume (SysEx Master Volume)
    @0033: DD 64        Set Tempo
    @0035: FD 84 80     Delay [n] Frame(s)
    @0038: DD 50        Set Tempo
    @003A: FD 80 C0     Delay [n] Frame(s)
    @003D: 90 03 61     Set Channel
    @0040: 91 03 6D     Set Channel
    @0043: 93 03 80     Set Channel
    @0046: 94 04 07     Set Channel
    @0049: 96 05 E6     Set Channel
    @004C: 97 06 F1     Set Channel
    @004F: 99 07 01     Set Channel
    @0052: 9A 07 77     Set Channel
    @0055: 9B 09 48     Set Channel
    @0058: 9F 0A 04     Set Channel
    ```

=== "Loop Address"
    ``` linenums="0" hl_lines="19"
    @Addr: Data         Command
    ————————————————————————————————————————————————————
    @0010: D7 8E DB     Initialize Channels
    @0013: 90 00 7D     Set Channel
    @0016: 91 00 F4     Set Channel
    @0019: 93 01 02     Set Channel
    @001C: 94 01 10     Set Channel
    @001F: 96 02 7F     Set Channel
    @0022: 97 02 8D     Set Channel
    @0025: 99 02 9B     Set Channel
    @0028: 9A 02 AB     Set Channel
    @002B: 9B 03 2C     Set Channel
    @002E: 9F 03 53     Set Channel
    @0031: DB 50        Set Volume (SysEx Master Volume)
    @0033: DD 64        Set Tempo
    @0035: FD 84 80     Delay [n] Frame(s)
    @0038: DD 50        Set Tempo
    @003A: FD 80 C0     Delay [n] Frame(s)
    @003D: 90 03 61     Set Channel
    @0040: 91 03 6D     Set Channel
    @0043: 93 03 80     Set Channel
    @0046: 94 04 07     Set Channel
    @0049: 96 05 E6     Set Channel
    @004C: 97 06 F1     Set Channel
    @004F: 99 07 01     Set Channel
    @0052: 9A 07 77     Set Channel
    @0055: 9B 09 48     Set Channel
    @0058: 9F 0A 04     Set Channel
    ```

### Adding Loop Points in FL Studio
When working with FL Studio extra steps have to be taken as FL Studio Does not support SysEx MIDI messages or MIDI marker meta messages. The markers mentioned by FL Studio during export are FL Studio specific markers, they are not MIDI marker meta messages. There are two ways to get around this:

1. Open the MIDI file in Sekaiju, or other MIDI sequencing software that supports MIDI marker meta messages. Then add a MIDI marker meta message with the name "section" or "loop".
2. Insert MIDI CC#115 in MIDI channel 1. Then conver the MIDI file into a sequence using SEQ64 version 2.0 and above while "FL Studio compatibility mode" is enabled.

When FL Studio compatibility mode is enabled in SEQ64 version 2.0 and above, SEQ64 will recognize MIDI CC#114 as master volume and MIDI CC#115 as a section marker. These MIDI control change messages must be placed in MIDI channel 1. For MIDI CC#115, its value must not be zero, and each section marker must have a value different than the last section marker.

-----

[^1]: Infomation found in [Chapter 17.4.5: Allocating and Controlling Voices](https://ultra64.ca/files/documentation/online-manuals/man/pro-man/pro17/index17.4.html){ target="__blank" }<small>:material-open-in-new:</small> of the Nintendo 64 Programming Manual.