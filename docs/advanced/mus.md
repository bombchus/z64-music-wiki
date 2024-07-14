# Music Assembly Language

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

!!! warning "Music Assembly Language is not Music Macro Language!"
    Despite `.mus` files being called "Music Macro Language", they are *not* Music Macro Language (MML)[^1]. MML is well-defined and is a sub-language of BASIC. However, modern MML notation is quite different from the original MML's BASIC notation. Music Assembly Language (`.mus`) files are a sub-language of Assembly (ASM). As such, they should avoid being called "Music Macro Language". Instead, `.mus` files should be called "Music Assembly Language (MAL)".

## placeholder
placeholder

=== "Header"
    | MAL Command | SEQ Command |
    | --- | --- |
    | `notedvg` | Note (D, V, G) |
    | `notedv` | Note (D, V) |
    | `notevg` | Note (V, G) |
    | `snoted` | — |
    | `snotedef` | — |
    | `snotelast` | — |
    | `ldelay` | Layer Delay |
    | `shortvel` | Set Short Note Velocity |
    | `ltp` | Layer Transpose |
    | `shortdelay` | Set Default Short Note Delay |
    | `legatoon` | Continuous On |
    | `legatooff` | Continuous Off |
    | `linst` | Set Instrument (Layer) |
    | `portamento` | Enable Portamento |
    | `portamentooff` | Disable Portamento |
    | `shortgate` | Set Short Note Gatetime |
    | `lpan` | Set Pan (Layer) |
    | `lenvelope` | Set Envelope (Layer) |
    | `drumpanoff` | Ignore Drum Pan |
    | `reverbphase` | Set Stereo Effects |
    | `lbend2` | Set Pitch Bend (±2 Semitones, Layer) |
    | `lrelease` | Set Decay Index (Layer) |
    | `shorttablevel` | Set Short Note Velocity from Table |
    | `shorttablegate` | Set Short Note Gatetime from Table |

=== "Channel"
    | MAL Command | SEQ Command |
    | --- | --- |
    | `cdelay` | Channel Delay |
    | `loadspl` | Load Sample |
    | `startchan` | Start Channel |
    | `stcio` | IO Write Value 2 |
    | `ldcio` | IO Read Value 2 |
    | `subio` | [v] -= IO[c] |
    | `ldio` | [v] = IO[c] |
    | `stio` | IO[c] = [v] |
    | `rstartlayer` | Start Layer (Relative) |
    | `testlayer` | Test Layer is Finished |
    | `startlayer` | Start Layer (Absolute) |
    | `stoplayer` | Stop Layer |
    | `dynstartlayer` | Dyn Start Layer |
    | `setfilter` | Set Filter |
    | `cleafilter` | Clear Filter |
    | `copyfilter` | Load Filter |
    | `p2dyntable` | Set Dyntable Large |
    | `dyntable2p` | Read Dyntable Large |
    | `lddyn` | Read Dyntable |
    | `randp` | Random Large |
    | `rand` | [v] = Random Value |
    | `velrand` | Set Velocity (Random Variance) |
    | `gaterand` | Set Gatetime (Random Variance) |
    | `chorus` | Set Chorus |
    | `addp` | [p] += cmdArg[0] |
    | `randaddp` | — |
    | `instr` | Set Instrument (Channel) |
    | `dyntable` | Set Dyntable |
    | `shorton` | Large Notes Off |
    | `shortoff` | Large Notes On |
    | `dynsetdyntable` | Dyn Set Dyntable |
    | `bank` | Set Soundfont |
    | `sts` | seqData[addr] = [v] + Immediate |
    | `sub` | [v] -= Set Value |
    | `and` | [v] &= Set Value |
    | `mutebhv` | Set Mute Behavior |
    | `lds` | [v] = seqData([addr] + [v]) |
    | `ldi` | [v] = Set Value |
    | `stopchan` | Disable Channel |
    | `ldpi` | unk_22 |
    | `stps` | Store Pointer |
    | `stereoheadseteffects` | Set Stereo Headset Effect |
    | `noteallocpolicy` | Set Note Allocation Policy |
    | `relsustain` | Set Sustain |
    | `pitchbend` | Set Pitch Bend (±12 Semitones) |
    | `reverb` | Set Reverb |
    | `vibfreq` | Set Vibrato Rate |
    | `vibdepth` | Set Vibrato Depth |
    | `release` | Set Decay Index |
    | `cenvelope` | Set Envelope |
    | `ctp` | Set Transposition (Channel) |
    | `panmix` | Set Pan Mix |
    | `cpan` | Set Pan (Channel) |
    | `freqscale` | Set Freqscale |
    | `cvol` | Set Volume (Channel) |
    | `cexp` | Set Expression (Channel) |
    | `vibfreqenv` | Set Vibrato Rate (Linear) |
    | `vibdepthenv` | Set Vibrato Depth (Linear) |
    | `vibdelay` | Set Vibrato Delay |
    | `dyncall` | Dyncall |
    | `reverbidx` | Set Reverb Index |
    | `splvari` | Set Codebook Offset |
    | `ldcparams` | Load Channel Parameters |
    | `cparams` | Set Channel Parameters |
    | `notepriority` | Set Note Priortity |
    | `halt` | Stop Script |
    | `bankinstr` | Set Soundfont & Instrument |
    | `chanreset` | Reset Channel |
    | `filgain` | Set HiLo Gain |
    | `cbend2` | Set Pitch Bend (±2 Semitones, Channel) |

=== "Header"
    | MAL Command | SEQ Command |
    | --- | --- |
    | `testchan` | — |
    | `stopchan` | Stop Channel |
    | `subio` | [v] -= IO[c] |
    | `loadbank` | Async Load |
    | `stio` | IO[c] = [v] |
    | `ldio` | [v] = IO[c] |
    | `startchan` | Start Channel |
    | `rstartchan` | Start Channel (Relative) |
    | `loadseq` | Load Sequence |
    | `unk_C4` | Call Sequence (?) |
    | `unk_C5` | Unk_16 = Address (?) |
    | `unk_C6` | Stop Script (?) |
    | `sub` | [v] -= Set Value |
    | `and` | [v] &= Set Value |
    | `ldi` | [v] = Set Value |
    | `tblcall` | Dyncall |
    | `rand` | [v] = Random Value |
    | `noteallocpolicy` | Set Note Allocation Policy |
    | `ldshorttablegate` | Set Short Note Gatetime Table |
    | `ldshorttablevel` | Set Short Note Velocity Table |
    | `mutebhv` | Set Mute Behavior |
    | `mute` | Mute Sequence |
    | `mutescale` | Set Mute Scale |
    | `disablechan` | Disable Channels |
    | `initchan` | Initialize Channels |
    | `sexp` | Set Expression (Sequence) |
    | `sfade` | Change Volume (Fade) |
    | `svol` | Set Volume (SysEx Master Volume) |
    | `tempovar` | Add Tempo |
    | `tempo` | Set Tempo |
    | `stprel` | Set Transposition (Relative, Sequence) |
    | `stp` | Set Transposition (Sequence) |
    | `print` | Print [3] Bytes |
    | `unreservenotes` | Unreserve Notes |
    | `rbltz` | Jump Relative if [v] < 0 |
    | `rbeqz` | Jump Relative if [v] = 0 |
    | `rjump` | Jump Relative |
    | `bgez` | Jump Absolute if [v] >= 0 |
    | `break` | Loop Break |
    | `loopend` | Loop End |
    | `loop` | Loop Start |
    | `bltz` | Jump Absolute if [v] < 0 |
    | `beqz` | Jump Absolute if [v] = 0 |
    | `jump` | Jump Absolute |
    | `call` | Call Absolute |
    | `delay` | Delay [n] Frames |
    | `yield` | Delay 1 Frame |
    | `end` | End of Script |

-----

=== "Header"
    ```asm linenums="0"
    ;**********
    ;* HEADER *
    ;**********

    _start
      mutebhv      32
      mutescale    50
      initchan     $0001
    start:
      startchan    0, start_chn0
      tempo        120
      svol         127
      delay        672
      jump         start
      disablechan  $0001
      end
    ```

=== "Channel"
    ```asm linenums="0"
    ;***********
    ;* CHANNEL *
    ;***********

    start_chn0:
      shortoff
      startlayer    0, start_chn0_ly0
      bank          0
      instr         79
      cvol          127
      cpan          64
      cexp          127
      reverb        40
      notepriority  3
      delay         672
    ```

=== "Layer"
    ```asm linenums="0"
    ;*********
    ;* LAYER *
    :*********

    start_chn0_ly0
      ltp      0
      loop     1
      call     _chn0_ly0_call0
      loopend
    ; COMMUNITY DIALECT: Zelda Note = MIDI Note -21
    ;   notedvg note, delay, valocity, gate
    ;   notevg note, velocity, gate
    ;   notedv note, delay, velocity
      notedvg  39, 240, 100, 51
      notevg   39, 100, 511
      notedv   39, 192, 100
    ; NINTENDO (CANON) DIALECT: NOTE = MIDI Note -1 Octave
    ;   NOTE:ACCIDENTAL:OCTAVE:B:?:W  , delay, velocity, gate
    ;   NOTE:ACCIDENTAL:OCTAVE:B:?    , velocity, gate
    ;   NOTE:ACCIDENTAL:OCTAVE:B:?:W  , delay , velocity
    ; CN4B0W   , 240, 127, 51
    ; CN4B1    , 100, 51
    ; CN4B1W   , 192, 100
      end
    ```

=== "Calls"
    ```asm linenums="0"
    ;*********
    ;* CALLS *
    ;*********

    _chn0_ly0_call0:
      break
      end
    ```

[^1]: For more information on Music Macro Language, please visit the [Wikipedia](https://en.wikipedia.org/wiki/Music_Macro_Language) article on it.