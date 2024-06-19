# Overview

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

## Summary of Music Creation

placeholder

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
        For a channel containing overlapping notes, SEQ64 will give the following error in the console window or debug output: *`Note off (ch=# note=# time=#) received for note that is not on!`*
    
    === "Voice Limit"
        For a channel containing more than four voices sounding at once, SEQ64 will give the following error in the console window of debug output: *`Channel # has more than 4 notes on at a time (at t=#)`*