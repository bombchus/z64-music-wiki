# Assigning Instruments

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details how to assign instruments in MIDI and sequences, so that instruments assigned in MIDI will match those inside of the audiobank used for a sequence in *Ocarina of Time* and *Majora's Mask*.

## Summary of Assigning Instruments
In MIDI, instruments are assigned by a control change command using the values 192 (0xC0) to 207 (0xCF). Generally only a single instrument can be assigned per channel. However, instruments can be swapped at any point using a MIDI program change message.

MIDI instrument banks using the GM specification normally contain 127 possible instruments with MIDI channel 10 always being reserved for percussion kits, where instead of using a program change to individual drums, it instead changes the entire percussion kit itself with individual drum sounds being assigned to different keys on the virtual MIDI piano (the range of possible samples is from keys 35 to 81). Instrument banks in MIDI contain those 127 instruments and percussion kits within a single instrument bank. However, in *Ocarina of Time* and *Majora's Mask* there are multiple instrument banks commonly referred to as "audiobanks" or "soundfonts". Setting instruments depends entirely on the audiobank used; in vanilla audiobanks there will almost always only be 1 (0x00) to 16 (0x0F) instruments with instrument 126 (0x7E) assigning the sound effects to a channel and instrument 127 (0x7F) assigning the percussion kit to a channel. Audiobanks can contain up to 255 (0xFF) instruments that may be assigned to a channel. However, instruments 126 (0x7E) and 127 (0x7F) are always reserved for sound effects and percussion kits respectively.

Some audiobanks may have fewer instruments, different sound effects, or contain entirely different percussion kits. The reason for using multiple smaller audiobanks is to reduce the amount of RAM required by the audio system in *Ocarina of Time* and *Majora's Mask*.

??? info "Drums and Sound Effects"
    Drums and sound effects in *Ocarina of Time* and *Majora's Mask* work almost identically to how they do in MIDI with different values corresponding to different individual drum sounds. The only difference is that there is a single percussion kit per audiobank, and it is assigned to program 127 (0x7F) instead of being assigned to a specific MIDI channel.

To properly assign the instruments a sequence will use, it is necessary to determine which instrument inside the audiobank used corresponds to the equivalent MIDI program value. The [vanilla audiobank references](../../vanilla-reference/audiobanks){ target="__blank" }<small>:material-open-in-new: </small> wiki page contains a list of all audiobanks and their corresponding instruments and instrument assignment values.

<style>
/*
THE GREAT REWRITE WILL BE FINISHED EVENTUALLY!!!

To use instruments in a MIDI channel a MIDI program change message must be sent to the MIDI channel. Each MIDI channel may only have a single instrument assigned to it at a time. However, the instrument used by a MIDI channel can be changed at any time. To change the instrument a MIDI channel uses, another MIDI program change message must be sent to the MIDI channel. Percussion kits may only be used in MIDI channel 10.

To use instruments in a sequence channel the sequence command "0xC1" must be sent to the sequence channel. Each sequence channel may only have a single instrument assigned to it at a time. However, the instrument used by a sequence channel can be changed at any time. To change the instrument a sequence channel uses, another sequence command "0xC1" must be sent to the sequence channel. Percussion kits have an instrument assignment value of 0x7F (127) in Ocarina of Time and Majora's Mask.
*/
</style>

## Assigning Instruments in MIDI
In MIDI, instruments and percussion kits are assigned to a channel by sending a MIDI program change message to that channel. There may only be a single instrument or percussion kit assigned to a channel at any time. However, the channel's assigned instrument or percussion kit can be changed at any point by sending another MIDI program change message to the channel. MIDI program change messages have two bytes. The first byte of a MIDI program change message is the status byte with values ranging from 0xC0 to 0xCF. The first half-byte determines the message type; the second half-byte points to the MIDI channel the message is sent to. The status byte determines the channel the message is sent to. The second byte of a MIDI program change message is the data byte with values ranging from 0x00 (0) to 0x7F (127). The data byte determines what instrument or percussion kit the channel will use. Instruments may be set in any MIDI channel except for MIDI channel 10.

### Using Percussion Kits in MIDI
While regular instruments can be assigned to any MIDI channel other than MIDI channel 10, percussion kits can only be assigned in MIDI channel 10. Percussion kits in MIDI have their own separate banks that are assigned solely to MIDI channel 10. Because of this, percussion kits are only available in MIDI channel 10 and cannot be used in any of the other MIDI channels.

## Assigning Instruments in Sequences
In *Ocarina of Time* and *Majora's Mask*, instruments, sound effects, and percussion kits are assigned to a channel with the sequence command 0xC1 (Set Instrument). There may only be a single instrument, sound effects, or percussion kit assigned to a channel at any given time. However, the channel's assigned instrument, sound effects, or percussion kit can be changed at any point by sending another sequence command of 0xC1 (Set Instrument). The sequence command 0xC1 (Set Instrument) only has a data byte with values ranging from 0x00 (0) to 0xFF (255). This data byte determines what instrument, sound effects, or percussion kit the channel will use. Instruments may be set in any sequence channel.

### Using Percussion Kits and Sound Effects in Sequences
Unlike in MIDI, percussion kits and sound effects can be assigned to any channel in a sequence. Percussion kits and sound effects are reserved solely for the sequence command 0xC1 (Set Instrument) data byte values of 0x7E (126) for sound effects and 0x7F (127) for percussion kits. Because of this, it is possible to use percussion kits and sound effects in any channel in a sequence. However, there is only one percussion kit and sound effect set available per audiobank in *Ocarina of Time* and *Majora's Mask*.

## Assigning Appropriate MIDI Instruments
Instruments in MIDI are not one-to-one with instruments in *Ocarina of Time* and *Majora's Mask*. For example, in MIDI, the "Strings" instrument has a MIDI program change value of 48 (0x30). In *Ocarina of Time* and *Majora's Mask*, the "Strings" instrument has an instrument assignment value dependent on the bank used by a sequence. Unlike in MIDI, in *Ocarina of Time* and *Majora's Mask*, it is also possible that the "Strings" instrument may not be present in a bank at all. As an example, in *Ocarina of Time* and *Majora's Mask*, bank 0x03 assigns the "Strings" instrument to a value of 10 (0x0A) or 11 (0x0B), while bank 0x02 does not contain the "Strings" instrument at all in either game and only contains ambient nature sounds. So, to make sure instruments, sound effects, and percussion kits are assigned to the proper channel in a sequence, it is required to adjust MIDI program change message values to match the assignment value of the counterpart chosen in the *Ocarina of Time* and *Majora's Mask* bank being used.

## placeholder
placeholder

### midi banks
In MIDI, instruments and percussion kits are stored inside of banks. In the General MIDI 1.0 specification (which does not support MIDI bank select messages), bank 0 (0x00) contains only instruments with bank 128 (0x80) containing only percussion kits. Bank 0 is the default bank for all MIDI channels with bank 128 as the default bank in MIDI channel 10.

### oot and mm banks
In Ocarina of Time and Majora's Mask, instruments, sound effects, and percussion kits are stored inside of banks (commonly referred to as "audiobanks" or "soundfonts"). Unlike MIDI, *Ocarina of Time* and *Majora's Mask* store instruments, sound effects, and percussion kits inside of a single bank. And while a sequence command for changing banks does exist, it can only load banks that are currently loaded into RAM.