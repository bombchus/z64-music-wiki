---
hide:
  #- toc
icon: material/waveform
---

<style>
  /* Change table width to full */
  .md-typeset__table {
    width: 100%;
  }
  .md-typeset__table table:not([class]) {
    display: table;
  }
  /* Hide Table of Contents without reducing width */
  .md-sidebar--secondary .md-sidebar__scrollwrap {
    display: none;
  }

</style>

# Vanilla Sample Addresses

Below is a list containing all of the samples in the Ocarina of Time and Majora's Mask ROMs in decimal and hexadecimal. Instrument samples are organized using GM[^1] instrument program number specification going from the lowest instrument sample to highest instrument sample for each instrument. Some instruments however do not fit into GM, so they are placed in the table where they would most likely fit instead.

=== "Ocarina of Time Samples"

    ## Instrument Samples

    placeholder

    ## Drum Samples

    placeholder

    ## Sound Effect Samples

    placeholder

=== "Majora's Mask Samples"

    ## Instrument Samples

    ??? info "Sample Names to Possibly Be Changed"
        `Giants' Voice` to `CARTOON, YELL - FUNNY TARZAN YELL 01`  
        `Metal Bang` to `CARTOON, HIT - BIG, HEAVY METALLIC HIT`

    Below is a list of instrument samples located in audiobanks `0x03` to `0x27`. Audiobank `0x28` does not contain any useful sample data so it has been omitted.

    ??? waveform "Instrument Sample Table"
        | Sample Name | Sample Address (DEC) | Sample Address (HEX) | Audiotable |
        | --- | :-: | :-: | :-: |
        | Piano Low | `4165648` | `0x003F9010` | `ATNUM 1` |
        | Piano Mid | `4196832` | `0x004009E0` | `ATNUM 1` |
        | Piano High | `2817232` | `0x002AFCD0` | `ATNUM 1` |
        | E. Rhodes Piano Low | `4577744` | `0x0045D9D0` | `ATNUM 1` |
        | E. Rhodes Piano Mid | `4589792` | `0x0046D8E0` | `ATNUM 1` |
        | Harpsichord | `5106448` | `0x004DEB10` | `ATNUM 1` |
        | Glockenspiel | `4014816` | `0x003D42E0` | `ATNUM 1` |
        | Marimba Mid | `5321248` | `0x00513220` | `ATNUM 1` |
        | Marimba High | `5331136` | `0x005158C0` | `ATNUM 1` |
        | Reverb Marimba | `34352` | `0x00008630` | `ATNUM 2` |
        | Carillon Bell | `5366464` | `0x0051E2C0` | `ATNUM 1` |
        | Electric Organ | `4720128` | `0x00480600` | `ATNUM 1` |
        | Harmonica | `4413472` | `0x00435820` | `ATNUM 1` |
        | Bandoneon | `2603312` | `0x0027B930` | `ATNUM 1` |
        | Nylon Str. Guitar Mid | `4422352` | `0x00437AD0` | `ATNUM 1` |
        | Nylon Str. Guitar High | `4438832` | `0x0043BB30` | `ATNUM 1` |
        | Steel Str. Guitar Mid | `2707520` | `0x00295040` | `ATNUM 1` |
        | Steel Str. Guitar High | `4137424` | `0x003F21D0` | `ATNUM 1` |
        | Sustain E. Guitar Low | `5339728` | `0x00517A50` | `ATNUM 1` |
        | Sustain E. Guitar Mid | `5349936` | `0x0051A230` | `ATNUM 1` |
        | Sustain E. Guitar High | `5358576` | `0x0051C3F0` | `ATNUM 1` |
        | Muted E. Guitar | `4663536` | `0x004728F0` | `ATNUM 1` |
        | Pizz. Double Bass | `4481440` | `0x004461A0` | `ATNUM 1` |
        | Fretless Bass | `2844016` | `0x002B6570` | `ATNUM 1` |
        | Solo Violin | `4235680` | `0x0040A1A0` | `ATNUM 1` |
        | Strings Low | `4296960` | `0x00419100` | `ATNUM 1` |
        | Strings Mid | `4317472` | `0x0041E120` | `ATNUM 1` |
        | Strings High | `4335568` | `0x004227D0` | `ATNUM 1` |
        | Pizz. Strings Mid | `4455008` | `0x0043FA60` | `ATNUM 1` |
        | Pizz. Strings High | `4468000` | `0x00442D20` | `ATNUM 1` |
        | Harp Mid | `3999280` | `0x003D0630` | `ATNUM 1` |
        | Harp High | `2621536` | `0x00280060` | `ATNUM 1` |
        | Synth Strings | `4688928` | `0x00478C20` | `ATNUM 1` |
        | Female Choir Mid | `3936032` | `0x003C0F20` | `ATNUM 1` |
        | Female Choir High | `3965936` | `0x003C83F0` | `ATNUM 1` |
        | Male Choir Low | `4732448` | `0x00483620` | `ATNUM 1` |
        | Male Choir Mid | `4753840` | `0x004889B0` | `ATNUM 1` |
        | Lulu's Voice | `2639248` | `0x00284590` | `ATNUM 1` |
        | Goron Elder Son's Voice | `2851552` | `0x002B82E0` | `ATNUM 1` |
        | Giants' Voice | `2864912` | `0x002BB710` | `ATNUM 1` |
        | Trumpet (C5-72) | `4387024` | `0x0042F0D0` | `ATNUM 1` |
        | Trumpet (G4-67) | `4146112` | `0x003F43C0` | `ATNUM 1` |
        | Trumpet (B3-59) | `2730224` | `0x0029A8F0` | `ATNUM 1` |
        | Tuba | `4401328` | `0x004328B0` | `ATNUM 1` |
        | French Horn | `4355952` | `0x00427770` | `ATNUM 1` |
        | Tenor Saxophone Low | `4125376` | `0x003EF2C0` | `ATNUM 1` |
        | Tenor Saxophone Mid | `4130688` | `0x003F0780` | `ATNUM 1` |
        | Oboe | `4351168` | `0x004264C0` | `ATNUM 1` |
        | Bassoon Low | `4449632` | `0x0043E560` | `ATNUM 1` |
        | Bassoon Mid | `5136544` | `0x004E60A0` | `ATNUM 1` |
        | Clarinet | `5162576` | `0x004EC650` | `ATNUM 1` |
        | Piccolo | `2646016` | `0x00286000` | `ATNUM 1` |
        | Ocarina | `2590384` | `0x002786B0` | `ATNUM 1` |
        | Digi Pad 04 | `5415520` | `0x0052A260` | `ATNUM 1` |
        | Mystic Pad | `4918480` | `0x004B0CD0` | `ATNUM 1` |
        | Velocity (MC-202) | `4933952` | `0x004B4940` | `ATNUM 1` |
        | Chip SFX | `4918176` | `0x004B0BA0` | `ATNUM 1` |
        | Fantasia | `4497712` | `0x0044A130` | `ATNUM 1` |
        | ELVES | `5137904` | `0x004E65F0` | `ATNUM 1` |
        | ICELAND 1 | `5063216` | `0x004D4230` | `ATNUM 1` |
        | OMINOUSITY | `4606320` | `0x00464970` | `ATNUM 1` |
        | DANGER | `4668944` | `0x00473E10` | `ATNUM 1` |
        | TUNNEL RAIN | `4872064` | `0x004A5780` | `ATNUM 1` |
        | EERIE WIND | `4530384` | `0x004520D0` | `ATNUM 1` |
        | PIT HIT 1 | `4645696` | `0x0046E340` | `ATNUM 1` |
        | African Vocal Phrase 2 | `4833120` | `0x0049BF60` | `ATNUM 1` |
        | Awk Bird Low | `4819792` | `0x00498B50` | `ATNUM 1` |
        | Awk Bird Mid | `4826736` | `0x0049A670` | `ATNUM 1` |
        | Sitar | `5174848` | `0x004EF640` | `ATNUM 1` |
        | Banjo Low | `5190720` | `0x004F3440` | `ATNUM 1` |
        | Banjo Mid | `5202560` | `0x004F6280` | `ATNUM 1` |
        | Bouzouki Low | `4941328` | `0x004B6610` | `ATNUM 1` |
        | Bouzouki Mid | `4955360` | `0x004B9CE0` | `ATNUM 1` |
        | Shehnai | `5165632` | `0x004ED240` | `ATNUM 1` |
        | Cowbell | `5246928` | `0x00500FD0` | `ATNUM 1` |
        | Metal Knock | `4910880` | `0x004AEF20` | `ATNUM 1` |
        | Steel Drum Mid | `5386000` | `0x00522F10` | `ATNUM 1` |
        | Steel Drum High | `5404442` | `0x00527B70` | `ATNUM 1` |
        | Surdo | `2664080` | `0x0028A690` | `ATNUM 1` |
        | Tabla Mid | `4777056` | `0x0048E460` | `ATNUM 1` |
        | Tabla High | `4788368` | `0x00491090` | `ATNUM 1` |
        | Rawhide Drum | `2693024` | `0x002917A0` | `ATNUM 1` |
        | Djembe Open | `4973968` | `0x004BE590` | `ATNUM 1` |
        | Djembe Slap | `4978096` | `0x004BF5B0` | `ATNUM 1` |
        | Djembe Muted | `4984224` | `0x004C0DA0` | `ATNUM 1` |
        | Hi-Hat Noise | `4631440` | `0x0046AB90` | `ATNUM 1` |
        | Chinese Gong Low | `5250192` | `0x00501C90` | `ATNUM 1` |
        | Chiense Gong Mid | `2770752` | `0x002A4740` | `ATNUM 1` |
        | Chinese Gong High | `5286464` | `0x0050AA40` | `ATNUM 1` |
        | Gong | `4988096` | `0x004C1CC0` | `ATNUM 1` |
        | Chimes | `5030384` | `0x004CC1F0` | `ATNUM 1` |
        | Kagura Suzu | `4111008` | `0x003EBAA0` | `ATNUM 1` |
        | Metal Bang | `4897088` | `0x004AB940` | `ATNUM 1` |
        | Bongo & Slap Low | `4800112` | `0x00493E70` | `ATNUM 1` |
        | Bongo & Slap Mid | `4805184` | `0x00495240` | `ATNUM 1` |
        | Bent Conga | `5053680` | `0x004D1CF0` | `ATNUM 1` |
        | Bent Conga | `0` | `0x00000000` | `ATNUM 2` |
        | Leaves Brush | `4810256` | `0x00496610` | `ATNUM 1` |
        | Tambourine Slap | `2674592` | `0x0028CFA0` | `ATNUM 1` |
        | Tambourine Tap | `4143488` | `0x003F3980` | `ATNUM 1` |
        | Tambourine Shake | `2683504` | `0x0028F270` | `ATNUM 1` |
        | Cuica Open | `29392` | `0x000072D0` | `ATNUM 2` |
        | Cuica Mute | `31600` | `0x00007B70` | `ATNUM 2` |
        

    ## Drum Samples

    placeholder

    ??? waveform "Drum Sample Table"
        | Sample Name | Sample Address (DEC) | Sample Address (HEX) | Audiotable |
        | --- | :-: | :-: | :-: |
        | a | `0` | `0x00` | `ATNUM 1` |

    ## Sound Effect Samples

    placeholder

    ??? waveform "Sound Effect Sample Table"
        | Sample Name | Sample Address (DEC) | Sample Address (HEX) | Audiotable |
        | --- | :-: | :-: | :-: |
        | a | `0` | `0x00` | `ATNUM 1` |

[^1]: For more information on General MIDI specification, please visit the [Wikipedia](https://en.wikipedia.org/wiki/General_MIDI) article on it, or visit the [midi.org](https://midi.org/specs) specification page on it.