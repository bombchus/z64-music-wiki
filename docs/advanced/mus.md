# Music Assembly Language

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

!!! warning
    Despite SEQ64 calling `.mus` files Music Macro Language (MML)[^1], they are *not* Music Macro Language. MML is well-defined and is a sub-language of BASIC. However, modern MML notation is quite different from the original MML's BASIC notation. Music Assembly Language (`.mus`) files are a sub-language of Assembly (ASM). As such, they should avoid being called "Music Macro Language". Instead, `.mus` files should be called "Music Assembly Language (MAL)".

## placeholder
placeholder

`notedvg`
`notedv`
`notevg`
`snoted`
`snotedef`
`snotelast`
`ldelay`
`shortvel`
`ltp`
`shortdelay`
`legatoon`
`legatooff`
`linst`
`portamento`
`portamentooff`
`shortgate`
`lpan`
`lenvelope`
`drumpanoff`
`reverbphase`
`lbend2`
`lrelease`
`shorttablevel`
`shorttablegate`
`cdelay`
`loadspl`
`startchan`
`stcio`
`ldcio`
`subio`
`ldio`
`stio`
`rstartlayer`
`testlayer`
`startlayer`
`stoplayer`
`dynstartlayer`
`setfilter`
`cleafilter`
`copyfilter`
`p2dyntable`
`dyntable2p`
`lddyn`
`randp`
`rand`
`velrand`
`gaterand`
`chorus`
`addp`
`randaddp`
`instr`
`dyntable`
`shorton`
`shortoff`
`dynsetdyntable`
`bank`
`sts`
`sub`
`and`
`mutebhv`
`lds`
`ldi`
`stopchan`
`ldpi`
`stps`
`stereoheadseteffects`
`noteallocpolicy`
`relsustain`
`pitchbend`
`reverb`
`vibfreq`
`vibdepth`
`release`
`cenvelope`
`ctp`
`panmix`
`cpan`
`freqscale`
`cvol`
`cexp`
`vibfreqenv`
`vibdepthenv`
`vibdelay`
`dyncall`
`reverbidx`
`splvari`
`ldcparams`
`cparams`
`notepriority`
`halt`
`bankinstr`
`chanreset`
`filgain`
`cbend2`
`testchan`
`stopchan`
`subio`
`loadbank`
`stio`
`ldio`
`startchan`
`rstartchan`
`loadseq`
`unk_C4`
`unk_C5`
`unk_C6`
`sub`
`and`
`ldi`
`tblcall`
`rand`
`noteallocpolicy`
`ldshorttablegate`
`ldshorttablevel`
`mutebhv`
`mute`
`mutescale`
`disablechan`
`initchan`
`sexp`
`sfade`
`svol`
`tempovar`
`tempo`
`stprel`
`stp`
`print`
`unreservenotes`
`rbltz`
`rbeqz`
`rjump`
`bgez`
`break`
`loopend`
`loop`
`bltz`
`beqz`
`jump`
`call`
`delay`
`yield`
`end`

[^1]: For more information on Music Macro Language, please visit the [Wikipedia](https://en.wikipedia.org/wiki/Music_Macro_Language) article on it.

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