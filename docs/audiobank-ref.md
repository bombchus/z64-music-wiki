---
hide:
  #- navigation
  #- toc
icon: material/playlist-music
---

<style>
  /* Hide Table of Contents without reducing width */
  .md-sidebar--secondary .md-sidebar__scrollwrap {
    display: none;
  }

</style>

# Vanilla Audiobank Reference

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

Below is a list of every audiobank in the vanilla ROM of Ocarina of Time and Majora's Mask, every entry contains the following information:

* Audiobank index value
* Audiobank name (Same as the ROM Description name)
* Sequences that use the audiobank
* Number of instruments within the audiobank (indicated by `NUM_INST`)
* Number of drums within the audiobank (indicated by `NUM_DRUM`)
* Number of sound effects within the audiobank (indicated by `NUM_SFX`)
* Audiotable the audiobank uses (indicated by `ATnum`)
* Instrument list, drum list, and sound effect list (if there are no drums or sound effects there will be no list)
* MIDI program numbers you can use to access the instruments, drums, or sound effects
* MIDI note ranges for the different drum samples within the percussion kits

!!! info "Index Number to Note Number"
    For instruments the pointer index value is equivalent to the program number, however for drums & sound effects the pointer index value is equivalent to the MIDI note number minus `21`.

!!! info "MIDI Notation"
    All notes (e.g. `C5 (60)`) are using MIDI notation, they are not using piano notation. Using piano notation, the equivalent to MIDI note `60` would be `C4` instead of `C5`.

-----

=== "Ocarina of Time Audiobanks"

    !!! info "Instrument Names"
        Some instruments are named after the closest instrument known by the community, though some are named after the name of the sample that was used to create the instrument (e.g. Shine, Fantasia, Spaceosphere, Enigmatic).

    ??? audiobank "Audiobank 0x00 (SFX Bank)"

        Audiobank `0x00` is the first of the two main SFX audiobanks. It's mostly guesswork for what most of the sound effects are as mapping them out is done completely by listening to the samples themselves in `N64 Soundlist Tool` (for which many samples are pitched up or down in-game, so the pitches are "off" when being played back) and figuring out what sound is used where in the game.

        Sequences that use this audiobank are listed below:

        * `0x00: Master Sequence`
        * `0x44: Ocarina Song: "Saria's Song"`
        * `0x45: Ocarina Song: "Epona's Song"`
        * `0x46: Ocarina Song: "Zelda's Lullaby"`
        * `0x47: Ocarina Song: "Sun's Song"`
        * `0x48: Ocarina Song: "Song of Time"`
        * `0x49: Ocarina Song: "Song of Storms"`
        * `0x6D: Unknown Technical Sequence`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:

        * `NUM_INST: 92`
        * `NUM_DRUM: 4`
        * `NUM_SFX: 136`
        * `ATnum: 0`

        ## Instruments (Program Number: 0x00 to 0x5B)
        Below is a list of the "instruments" inside of audiobank `0x00`. These work exactly as regular instruments do, you can even import them into a custom audiobank as an instrument and use it in a sequence just like any regular instrument; and this is a common structure for the sound effects within the game.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x5B (91)`
        !!! info "Program Numbers"  
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Some sound effects using the instrument structure have multiple samples, the sound effects using multiple samples indicate which region contains which sound effect sample (e.g. `0x00: Low: SFX name, Mid: SFX Name, High: SFX Name`). Any sound effects without multiple regions use the mid (primary) sample.

        **Instrument List:**
        ```
        0x00. Dirt Footstep SFX?
        0x01. Sand Footstep SFX?
        0x02. Stone Footstep SFX
        0x03. Water Footstep SFX
        0x04. Splash Footstep SFX
        0x05. Unknown SFX (Rock?)
        0x06. Unknown SFX (Footstep?)
        0x07. Grass Footstep SFX
        0x08. Chest reveal SFX, Others?
        0x09. Snow Footstep SFX?
        0x0A. Unknown SFX (Rock related?)
        0x0B. Unknown SFX (Footstep?)
        0x0C. Splash SFX 1
        0x0D. Splash SFX 2
        0x0E. Unknown Sand SFX (Quicksand?)
        0x0F. Mid: Egg Hatch SFX 1, High: Wind SFX
        0x10. Unknown SFX (Sand?)
        0x11. Unknown White Noise SFX 1
        0x12. Unknown White Noise SFX 2
        0x13. Splash SFX 3
        0x14. Swimming SFX
        0x15. Mid: Drum SFX?, High: Gunshot SFX
        0x16. Footstep SFX?
        0x17. Footstep SFX ?
        0x18. Iron Boot Footstep SFX
        0x19. Hover Boot/Ice Footstep SFX
        0x1A. Mid: Sword Clink SFX 1, High: Sword Clink SFX 2
        0x1B. Scratch SFX?
        0x1C. Link Sword Sheathe SFX
        0x1D. Link Sword Unsheathe SFX
        0x1E. Whoosh SFX
        0x1F. Unknown SFX
        0x20. Metal Clang SFX
        0x21. Mid: Bow Draw SFX, High: Bow Twang SFX
        0x22. Mid: Hookshot Chain SFX
        0x23. Mid: Bombchu Fuse SFX, High: Bombchu Moving SFX
        0x24. Megaton Hammer SFX (MM Bank Stamp)
        0x25. Like Like SFX?
        0x26. Arrow Hitting Wood/Kakariko Child Hammer SFX
        0x27. Whoosh SFX 2 (Boomerang?)
        0x28. Unknown SFX (Rock related?)
        0x29. Mid: Pop SFX, High: Cursor SFX?
        0x2A. Robotic Buzzing SFX
        0x2B. Mid: Unknown SFX (A Thud Sound?)
        0x2C. Mid: Lens of Truth SFX, High: Whoosh SFX 3
        0x2D. Mid: Wooden Door Open SFX, High: Wooden Door Close SFX
        0x2E. Mid: Blue Warp SFX?, High: Squeaking SFX?
        0x2F. Explosion SFX
        0x30. Horse Gallop SFX
        0x32. Mid: Horse Whinny SFX, High: Horse Snort SFX
        0x31. ⛔ (nullptr)
        0x33. Mid: Running Water SFX, High: White Noise SFX 1 (Waterfall)
        0x34. Ocarina SFX 1 (Special Effect)
        0x35. Ocarina SFX 2
        0x36. Mid: Stone Moving on Stone SFX, High: Metal Door Closing SFX
        0x37. Rock Rolling SFX?
        0x38. Mid: Lava Bubbling SFX
        0x39. Chain Pulley SFX (Hyrule Castle Gate)
        0x3A. Mid: Chicken Cluck SFX, High: Frog Ribbit SFX
        0x3B. Door Thud SFX
        0x3C. Wind SFX
        0x3D. Mid: Rooster Crow SFX, High: Wolf Howl SFX
        0x3E. Light Splash SFX (Fish?)
        0x3F. Mid: Wooden Clack SFX, High: Stick Clack SFX
        0x40. Fairy Flying SFX 1? (Fairy Related)
        0x41. Unknown SFX
        0x42. Mid: Door Creak SFX, High: Door Creak Low SFX
        0x43. Unknown SFX
        0x44. Glass Hum SFX
        0x45. Fairy Flying SFX 2? (Fairy Related)
        0x46. Mid: Electric SFX (Barinade?), High: Pot Break SFX
        0x47. Water Drip SFX
        0x48. Water Bubbling SFX (Morpha Cutscene?)
        0x49. Mid: Fire Crackle SFX, High: Cow Moo SFX
        0x4A. Mid: Balloon Inflate SFX, High: Thunder SFX
        0x4B. Unknown SFX
        0x4C. Unknown SFX (Pop? Bang? Thud?)
        0x4D. Mid: Wind SFX?, High: Revving SFX
        0x4E. Mid: Cloth Flutter SFX
        0x4F. Mid: Castle Town Crowd SFX, High: Glass Shatter SFX (Ice?)
        0x50. Scratch SFX 2?
        0x51. Mid: Dodongo Roar SFX, High: Dog Bark SFX
        0x52. Woodwind Noise SFX
        0x53. Accordion Noise SFX
        0x54. Piano/Harp Noise SFX 1
        0x55. Malon Voice SFX
        0x56. Whistle Noise SFX?
        0x57. Mid: Wrong Note SFX, High: Unknown Metal Sound SFX
        0x58. Bird Chirp SFX
        0x59. Piano/Harp Noise SFX 2
        0x5A. Mid: Camera Alignment SFX, High: Lock-on SFX
        0x5B. Metal Chain SFX
        ```

        ## Sound Effects (Program Number: 7E)
        Below is a list of the "sound effects" inside of audiobank `0x00`. These work nearly identical to how percussion sets work except for how they are structured, they cannot be imported into audiobanks because their structure is built directly into a pointer array within `<absfxlist>`.

        You can access these sound effects when using this audiobank using MIDI program number(s): `0x7E (126)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Sound effects can only have one sample per sound effect, but some sound effect indexes point to the same sample in the audiobank. The indexes that use the same sample as another index are marked: `[Same sample as (index value)]`

        **Sound Effect List:**
        ```
        0x00. [absfxlist:0]
        0x01. [absfxlist:1]
        0x02. [absfxlist:2]
        0x03. [absfxlist:3]
        0x04. [absfxlist:4]
        0x05. [absfxlist:5]
        0x06. [absfxlist:6]
        0x07. [absfxlist:7]
        0x08. [absfxlist:8]
        0x09. [absfxlist:9]
        0x0A. [absfxlist:10]
        0x0B. [absfxlist:11]
        0x0C. [absfxlist:12]
        0x0D. [absfxlist:13]
        0x0E. [absfxlist:14]
        0x0F. [absfxlist:15]
        0x10. [absfxlist:16]
        0x11. [absfxlist:17]
        0x12. [absfxlist:18]
        0x13. [absfxlist:19]
        0x14. [absfxlist:20, absfxlist:64]
        0x15. [absfxlist:21]
        0x16. [absfxlist:22]
        0x17. [absfxlist:23]
        0x18. [absfxlist:24]
        0x19. [absfxlist:25]
        0x1A. [absfxlist:26]
        0x1B. [absfxlist:27]
        0x1C. [absfxlist:28]
        0x1D. [absfxlist:29]
        0x1E. [absfxlist:30]
        0x1F. [absfxlist:31]
        0x20. [absfxlist:32]
        0x21. [absfxlist:33]
        0x22. [absfxlist:34]
        0x23. [absfxlist:35]
        0x24. [absfxlist:36]
        0x25. [absfxlist:37]
        0x26. [absfxlist:38]
        0x27. [absfxlist:39]
        0x28. [absfxlist:40]
        0x29. [absfxlist:41]
        0x2A. [absfxlist:42]
        0x2B. [absfxlist:43]
        0x2C. [absfxlist:44]
        0x2D. [absfxlist:45]
        0x2E. [absfxlist:46]
        0x2F. [absfxlist:47]
        0x30. [absfxlist:48]
        0x31. [absfxlist:49]
        0x32. [absfxlist:50]
        0x33. [absfxlist:51]
        0x34. [absfxlist:52]
        0x35. [absfxlist:53]
        0x36. [absfxlist:54]
        0x37. [absfxlist:55]
        0x38. [absfxlist:56]
        0x39. [absfxlist:57, absfxlist:102]
        0x3A. [absfxlist:58, absfxlist:103]
        0x3B. [absfxlist:59, absfxlist:104]
        0x3C. [absfxlist:60]
        0x3D. [absfxlist:61]
        0x3E. [absfxlist:62]
        0x3F. [absfxlist:63]
        0x40. [absfxlist:20, absfxlist:64]
        0x41. [absfxlist:65]
        0x42. [absfxlist:66]
        0x43. [absfxlist:67]
        0x44. ⛔ (nullptr)
        0x45. [absfxlist:69]
        0x46. [absfxlist:70]
        0x47. [absfxlist:71]
        0x48. [absfxlist:72]
        0x49. [absfxlist:73]
        0x4A. [absfxlist:74]
        0x4B. [absfxlist:75]
        0x4C. [absfxlist:76]
        0x4D. [absfxlist:77]
        0x4E. [absfxlist:78]
        0x4F. [absfxlist:79]
        0x50. [absfxlist:80]
        0x51. [absfxlist:81]
        0x52. [absfxlist:82]
        0x53. [absfxlist:83]
        0x54. [absfxlist:84]
        0x55. [absfxlist:85]
        0x56. [absfxlist:86]
        0x57. [absfxlist:87]
        0x58. [absfxlist:88]
        0x59. [absfxlist:89]
        0x5A. [absfxlist:90]
        0x5B. [absfxlist:91]
        0x5C. [absfxlist:92]
        0x5D. [absfxlist:93]
        0x5E. [absfxlist:94]
        0x5F. [absfxlist:95]
        0x60. [absfxlist:96]
        0x61. [absfxlist:97]
        0x62. [absfxlist:98]
        0x63. [absfxlist:99]
        0x64. [absfxlist:100]
        0x65. [absfxlist:101]
        0x66. [absfxlist:57, absfxlist:102]
        0x67. [absfxlist:58, absfxlist:103]
        0x68. [absfxlist:59, absfxlist:104]
        0x69. [absfxlist:105]
        0x6A. [absfxlist:106]
        0x6B. [absfxlist:107]
        0x6C. [absfxlist:108]
        0x6D. [absfxlist:109]
        0x6E. [absfxlist:110]
        0x6F. [absfxlist:111]
        0x70. [absfxlist:112]
        0x71. [absfxlist:113]
        0x72. [absfxlist:114]
        0x73. [absfxlist:115]
        0x74. [absfxlist:116]
        0x75. [absfxlist:117]
        0x76. [absfxlist:118]
        0x77. [absfxlist:119]
        0x78. [absfxlist:120]
        0x79. [absfxlist:121]
        0x7A. [absfxlist:122]
        0x7B. [absfxlist:123]
        0x7C. [absfxlist:124]
        0x7D. [absfxlist:125]
        0x7E. [absfxlist:126]
        0x7F. [absfxlist:127]
        0x80. [absfxlist:128]
        0x81. [absfxlist:129]
        0x82. [absfxlist:130]
        0x83. [absfxlist:131]
        0x84. [absfxlist:132]
        0x85. ⛔ (nullptr)
        0x86. [absfxlist:134]
        0x87. [absfxlist:135]
        ```

        ## Drums (Program Number: 7F)
        Below is a list of the "drums" inside of audiobank `0x00`. Unlike instrument index pointers, percussion index pointers represent a MIDI note instead of a program number.

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        **Drum List:**
        ```
        0x00. [abdrumlist:0]
        0x01. [abdrumlist:1]
        0x02. [abdrumlist:2]
        0x03. [abdrumlist:3]
        ```

    ??? audiobank "Audiobank 0x01 (Actor Sounds)"

        Audiobank `0x01` is the second of the two main SFX audiobanks. It's mostly guesswork for what most of the sound effects are as mapping them out is done completely by listening to the samples themselves in `N64 Soundlist Tool` (for which many samples are pitched up or down in-game, so the pitches are "off" when being played back) and figuring out what sound is used where in the game.

        Sequences that use this audiobank are listed below:
        
        * `0x00: Master Sequence`
        * `0x6D: Unknown Technical Sequence`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 51`
        * `NUM_DRUM: 1`
        * `NUM_SFX: 41`
        * `ATnum: 0`

        ## Instruments (Program Number: 0x00 to 0x7D)
        Below is a list of the "instruments" inside of audiobank `0x01`. These work exactly as regular instruments do, you can even import them into a custom audiobank as an instrument and use it in a sequence just like any regular instrument; and this is a common structure for the sound effects within the game.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x7D (125)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.*

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Some sound effects using the instrument structure have multiple samples, the sound effects using multiple samples indicate which region contains which sound effect sample (e.g. `0x00: Low: SFX name, Mid: SFX Name, High: SFX Name`). Any sound effects without multiple regions use the mid (primary) sample.

        **Instrument List:**
        ```
        0x00. Pop/Thud SFX (Shabom?)
        0x01. Dodongo Roar SFX
        0x02. Balloon Inflate SFX
        0x03. Doom Monster Roar SFX
        0x04. Skulltula Skitter SFX
        0x05. Spider Egg Hatch SFX
        0x06. Rock Explosion SFX
        0x07. Unknown Buzz SFX (Creaking? Frog?)
        0x08. Poe Hover SFX?
        0x09. Clicking SFX (Keese Attack?)
        0x0A. Wing Flap SFX
        0x0B. Volvagia Pained Roar SFX
        0x0C. Scratch/Electric SFX (Skulltula Related?)
        0x0D. "Ah" SFX (Frog Croak?)
        0x0E. SM64 Boo Laugh SFX (Lizalfos Laugh?)
        0x0F. Mid: Lizalfos SFX, High: Lizalfos Footstep SFX
        0x10. Deku Scrub Voice SFX
        0x11. Glass Break SFX (Ice?)
        0x12. Wind SFX 1
        0x13. Unknown White Noise SFX
        0x14. Mid: Gulp SFX, High: Stick Clack SFX
        0x15. Deku Baba Beak Snap SFX
        0x16. Wind SFX 2
        0x17. Crow/Eagle/Bat SFX
        0x18. Mid: Buzz SFX, High: Deku Baba Breath SFX
        0x19. Stalfos Sword Swing SFX
        0x1A. Stalchild Laughing SFX
        0x1B. Stalfos Laughing SFX
        0x1C. Whip SFX (Used for Garo in MM)
        0x1D. Thunder SFX
        0x1E. Electric SFX (Ganon Summoning Orb)
        0x1F. Phantom/Regular Ganon Hover SFX
        0x20. Phantom Ganon Attack SFX?
        0x21. Whoosh SFX
        0x22. Thunder SFX 2
        0x23. Ganon Related SFX?
        0x24. Ganondorf "Ha!" SFX
        0x25. Flare Dancer SFX?
        0x26. Splash SFX
        0x27. Splish SFX (Footstep on Watery Surface)
        0x28. Mid: Boulder Explosion SFX, High: Lava Bubbling SFX
        0x29. Unknown Monster Roar SFX (King Dodongo/Volvagia?)
        0x2A. Mid: Redead/Gibdo SFX (Pamela's Father in MM), High: Goron Falling Asleep SFX
        0x2B. Poe Laugh SFX (SM64 Boo)
        0x2C. Water Bubbling SFX (Morpha Cutscene?)
        0x2D. Mid: Unknown Growl SFX, High: Poe Defeat Shriek SFX
        0x2E. Mid: Goron "Hmm?" SFX, High: Goron "Ooooh..." SFX
        0x2F. Mid: Metal Clink SFX, High: Leever SFX? (Sandy Sound)
        0x30. Mid: Bongo Bongo Drum Hit SFX, High: Unknown Voice SFX
        0x31. Mid: Wolfos Howl, High: Guay Caw SFX
        0x32. Mid: Witch Argument SFX, High: Metal Clank SFX (Iron Knuckle?)
        ```

        ## Sound Effects (Program Number: 7E)
        Below is a list of the "sound effects" inside of audiobank `0x01`. These work nearly identical to how percussion sets work except for how they are structured, they cannot be imported into audiobanks because their structure is built directly into a pointer array within `<absfxlist>`.

        You can access these sound effects when using this audiobank using MIDI program number(s): `0x7E (126)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.*

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Sound effects can only have one sample per sound effect, but some sound effect indexes point to the same sample in the audiobank. The indexes that use the same sample as another index are marked: `[Same sample as (index value)]`

        **Sound Effect List:**
        ```
        0x00. [absfxlist:0]
        0x01. [absfxlist:1]
        0x02. [absfxlist:2]
        0x03. [absfxlist:3]
        0x04. [absfxlist:4]
        0x05. [absfxlist:5]
        0x06. [absfxlist:6]
        0x07. [absfxlist:7]
        0x08. [absfxlist:8]
        0x09. [absfxlist:9]
        0x0A. [absfxlist:10]
        0x0B. [absfxlist:11]
        0x0C. [absfxlist:12]
        0x0D. [absfxlist:13]
        0x0E. [absfxlist:14]
        0x0F. [absfxlist:15]
        0x10. [absfxlist:16]
        0x11. [absfxlist:17]
        0x12. [absfxlist:18]
        0x13. [absfxlist:19]
        0x14. [absfxlist:20]
        0x15. [absfxlist:21]
        0x16. [absfxlist:22]
        0x17. [absfxlist:23]
        0x18. [absfxlist:24]
        0x19. [absfxlist:25]
        0x1A. [absfxlist:26]
        0x1B. [absfxlist:27]
        0x1C. [absfxlist:28]
        0x1D. [absfxlist:29]
        0x1E. [absfxlist:30]
        0x1F. [absfxlist:31]
        0x20. [absfxlist:32]
        0x21. [absfxlist:33]
        0x22. [absfxlist:34]
        0x23. [absfxlist:35]
        0x24. [absfxlist:36]
        0x25. [absfxlist:37]
        0x26. [absfxlist:38]
        0x27. [absfxlist:39]
        0x28. [absfxlist:40]
        ```

        ## Drums (Program Number: 7F)
        Below is a list of the "drums" inside of audiobank `0x00`. There's one single drum pointer, but it's just a null pointer value with no sample being pointed to.

        **Drum List:**
        ```
        0x00. ⛔ (nullptr)
        ```

    ??? audiobank "Audiobank 0x02 (Ambient Sounds)"

        Audiobank `0x02` is used pretty much for basically every ambient sound in the game. It's mostly guesswork for what most of the sound effects are as mapping them out is done completely by listening to the samples themselves in `N64 Soundlist Tool` (for which many samples are pitched up or down in-game, so the pitches are "off" when being played back) and figuring out what sound is used where in the game.

        Sequences that use this audiobank are listed below:
        
        * `0x01: Nature Ambience`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 21`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 0`

        ## Instruments (Program Name: 0x00 to 0x14)
        Below is a list of the "instruments" inside of audiobank `0x02`. These work exactly as regular instruments do, you can even import them into a custom audiobank as an instrument and use it in a sequence just like any regular instrument; and this is a common structure for the sound effects within the game.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x14 (20)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Bird Chirp SFX 1
        0x02. Bird Chitter SFX
        0x03. Bird Trill SFX
        0x04. Bird Song SFX
        0x05. Bird Chirp SFX 2
        0x06. Crow Caw SFX
        0x07. Swamp Bird SFX (Some type of honking bird)
        0x08. Peacock SFX?
        0x09. Bird Twitter SFX
        0x0A. Rooster Crow SFX
        0x0B. Owl Hoot SFX
        0x0C. Eagle SFX
        0x0D. Bird Chirp SFX 3
        0x0E. Guay Caw SFX
        0x0F. White Noise SFX (Waterfall)
        0x10. Wind SFX (Haunted Wasteland Sandstorm)
        0x11. Wind SFX 2 (Haunted Wasteland Sandstorm)
        0x12. Rain SFX
        0x13. Thunder SFX
        0x14. Thunder SFX 2
        ```

    ??? audiobank "Audiobank 0x03 (Main Orchestra)"

        Audiobank `0x03` is one of the largest regular audiobanks which makes it the best candidate to overwrite when making a custom audiobank.

        Sequences that use this audiobank are listed below:
        
        * `0x02: Hyrule Field (Master)`
        * `0x03: Hyrule Field (Day 1 - GG - Opening)`
        * `0x04: Hyrule Field (Day 2 - GF - Trumpets 1)`
        * `0x05: Hyrule Field (Day 3 - GF - Trumpets 2)`
        * `0x06: Hyrule Field (Day 4 - GFEb - Clarinets)`
        * `0x07: Hyrule Field (Day 5 - GCB - Strings, Pizz. Strings)`
        * `0x08: Hyrule Field (Day 6 - GFEm - OoT Theme)`
        * `0x09: Hyrule Field (Day 7 - CD - French Horns)`
        * `0x0A: Hyrule Field (Day 8 - CD - Strings)`
        * `0x0B: Hyrule Field (Day 9 - GG - French Horns)`
        * `0x0C: Hyrule Field (Day 10 - GBbDb - French Horns)`
        * `0x0D: Hyrule Field (Day 11 - AbCF - French Horns)`
        * `0x0E: Hyrule Field (Day 12 - GG - Neutral Opening)`
        * `0x0F: Hyrule Field (Battle 1 - OoT Theme Deconstruction)`
        * `0x10: Hyrule Field (Battle 2 - Brass)`
        * `0x11: Hyrule Field (Battle 3 - Brass, Marimba)`
        * `0x12: Hyrule Field (Battle 4 - Stabs, OoT Theme)`
        * `0x13: Hyrule Field (Battle 5 - Stabs, Ocarina)`
        * `0x14: Hyrule Field (Sunset 1 - Oboe)`
        * `0x15: Hyrule Field (Sunset 2 - Piccolo)`
        * `0x16: Hyrule Field (Sunset 3 - Strings)`
        * `0x17: Hyrule Field (Sunset 4 - OoT Theme)`
        * `0x19: Kakariko Village (Strings, Adult) [2]`
        * `0x1A: Battle: Regular Enemy`
        * `0x1B: Battle: Boss [1]`
        * `0x1F: Inside a House`
        * `0x21: Fanfare: Boss Defeated!`
        * `0x23: Fanfare: Ganondorf Appears!`
        * `0x2B: Fanfare: Open a Treasure Chest!`
        * `0x2D: Castle Courtyard`
        * `0x31: Hyrule Field (Morning, Day 1)`
        * `0x32: Fanfare: Get a Spiritual Stone!`
        * `0x38: Battle: Miniboss`
        * `0x3B: Fanfare: Escape from Lon Lon Ranch!`
        * `0x43: Fanfare: Get a Medallion!`
        * `0x4A: Intro Cutscene ~Fairy Flying~`
        * `0x51: Fanfare: A Meeting with Zelda! (Generic Reunion Theme)`
        * `0x52: Zelda's Theme ~Reprise~`
        * `0x53: Fanfare: Pull the Master Sword!`
        * `0x54: Ganondorf's Theme`
        * `0x62: Castle Collapsing`
        * `0x6C: Timed Minigame`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x03`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.*

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Oboe
        0x02. Clarinet
        0x03. Bassoon
        0x04. French Horn
        0x05. Trumpet
        0x06. Trombone
        0x07. Tuba
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. Piano
        0x0E. Harp
        0x0F. Marimba
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x03`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x04 (Deku Tree)"

        Sequences that use this audiobank are listed below:
        
        * `0x1C: Inside the Deku Tree & Secret Grottos`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 2`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 2`

        ## Instruments (Program Name: 0x00 to 0x01)
        Below is a list of the instruments inside of audiobank `0x04`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x01 (1)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Enigmatic
        0x01. Enigmatic ALT
        ```

    ??? audiobank "Audiobank 0x05 (Hylian Troupe)"

        Sequences that use this audiobank are listed below:
        
        * `0x1D: Hyrule Castle Town`
        * `0x3E: Lost Woods`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x05`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Ocarina
        0x02. Bassoon
        0x03. Oboe
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. Pizz. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x05`. This percussion set is referred to as "Tambourine Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Tambourine Slap: `A1 (21)` to `B3 (47)`
        - Tambourine Tap: `C4 (48)` to `C♯4 (49)`
        - Tambourine Shake: `D4 (50)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Tambourine Slap [1]
        0x01. Tambourine Slap [2]
        0x02. Tambourine Slap [3]
        0x03. Tambourine Slap [4]
        0x04. Tambourine Slap [5]
        0x05. Tambourine Slap [6]
        0x06. Tambourine Slap [7]
        0x07. Tambourine Slap [8]
        0x08. Tambourine Slap [9]
        0x09. Tambourine Slap [10]
        0x0A. Tambourine Slap [11]
        0x0B. Tambourine Slap [12]
        0x0C. Tambourine Slap [13]
        0x0D. Tambourine Slap [14]
        0x0E. Tambourine Slap [15]
        0x0F. Tambourine Slap [16]
        0x10. Tambourine Slap [17]
        0x11. Tambourine Slap [18]
        0x12. Tambourine Slap [19]
        0x13. Tambourine Slap [20]
        0x14. Tambourine Slap [21]
        0x15. Tambourine Slap [22]
        0x16. Tambourine Slap [23]
        0x17. Tambourine Slap [24]
        0x18. Tambourine Slap [25]
        0x19. Tambourine Slap [26]
        0x1A. Tambourine Slap [27]
        0x1B. Tambourine Tap [1]
        0x1C. Tambourine Tap [2]
        0x1D. Tambourine Shake [1]
        0x1E. Tambourine Shake [2]
        0x1F. Tambourine Shake [3]
        0x20. Tambourine Shake [4]
        0x21. Tambourine Shake [5]
        0x22. Tambourine Shake [6]
        0x23. Tambourine Shake [7]
        0x24. Tambourine Shake [8]
        0x25. Tambourine Shake [9]
        0x26. Tambourine Shake [10]
        0x27. Tambourine Shake [11]
        0x28. Tambourine Shake [12]
        0x29. Tambourine Shake [13]
        0x2A. Tambourine Shake [14]
        0x2B. Tambourine Shake [15]
        0x2C. Tambourine Shake [16]
        0x2D. Tambourine Shake [17]
        0x2E. Tambourine Shake [18]
        0x2F. Tambourine Shake [19]
        0x30. Tambourine Shake [20]
        0x31. Tambourine Shake [21]
        0x32. Tambourine Shake [22]
        0x33. Tambourine Shake [23]
        0x34. Tambourine Shake [24]
        0x35. Tambourine Shake [25]
        0x36. Tambourine Shake [25*]
        0x37. Tambourine Shake [25*]
        0x38. Tambourine Shake [25*]
        0x39. Tambourine Shake [25*]
        0x3A. Tambourine Shake [25*]
        0x3B. Tambourine Shake [25*]
        0x3C. Tambourine Shake [25*]
        0x3D. Tambourine Shake [25*]
        0x3E. Tambourine Shake [25*]
        0x3F. Tambourine Shake [25*]
        ```

    ??? audiobank "Audiobank 0x06 (Title Screen)"

        Sequences that use this audiobank are listed below:
        
        * `0x1E: Title Screen`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x06`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Ocarina
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. ⛔ (nullptr)
        0x0D. Piano
        0x0E. Piano ALT (Splits: 22 & 44, Release: 93)
        ```

    ??? audiobank "Audiobank 0x07 (Jabu-Jabu's Belly)"

        Audiobank `0x06` is a bit of a special audiobank, it uses a different audiotable than other audiobanks and the offsets reference data later in the audiotable causing the ADPCM data for their samples to be split; however, `SEQ64` will automatically update their sample location upon importing.

        Sequences that use this audiobank are listed below:
        
        * `0x26: Jabu-Jabu's Belly`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 3`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x07`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Wind
        0x01. ⛔ (nullptr)
        0x02. Synth Strings
        0x03. Crunch Roar
        0x04. Crunch Roar
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x07`. This percussion set is referred to as "Trip Hopping Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Trip Hopping Kick: `A1 (21)` to `C♯3 (37)`
        - Trip Hopping Snare: `D3 (38)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Trip Hopping Kick [1]
        0x01. Trip Hopping Kick [2]
        0x02. Trip Hopping Kick [3]
        0x03. Trip Hopping Kick [4]
        0x04. Trip Hopping Kick [5]
        0x05. Trip Hopping Kick [6]
        0x06. Trip Hopping Kick [7]
        0x07. Trip Hopping Kick [8]
        0x08. Trip Hopping Kick [9]
        0x09. Trip Hopping Kick [10]
        0x0A. Trip Hopping Kick [11]
        0x0B. Trip Hopping Kick [12]
        0x0C. Trip Hopping Kick [13]
        0x0D. Trip Hopping Kick [14]
        0x0E. Trip Hopping Kick [15]
        0x0F. Trip Hopping Kick [16]
        0x10. Trip Hopping Kick [17]
        0x11. Trip Hopping Snare [1]
        0x12. Trip Hopping Snare [2]
        0x13. Trip Hopping Snare [3]
        0x14. Trip Hopping Snare [4]
        0x15. Trip Hopping Snare [5]
        0x16. Trip Hopping Snare [6]
        0x17. Trip Hopping Snare [7]
        0x18. Trip Hopping Snare [8]
        0x19. Trip Hopping Snare [9]
        0x1A. Trip Hopping Snare [10]
        0x1B. Trip Hopping Snare [11]
        0x1C. Trip Hopping Snare [12]
        0x1D. Trip Hopping Snare [13]
        0x1E. Trip Hopping Snare [14]
        0x1F. Trip Hopping Snare [15]
        0x20. Trip Hopping Snare [16]
        0x21. Trip Hopping Snare [17]
        0x22. Trip Hopping Snare [18]
        0x23. Trip Hopping Snare [19]
        0x24. Trip Hopping Snare [20]
        0x25. Trip Hopping Snare [21]
        0x26. Trip Hopping Snare [22]
        0x27. Trip Hopping Snare [23]
        0x28. Trip Hopping Snare [24]
        0x29. Trip Hopping Snare [25]
        0x2A. Trip Hopping Snare [26]
        0x2B. Trip Hopping Snare [27]
        0x2C. Trip Hopping Snare [28]
        0x2D. Trip Hopping Snare [29]
        0x2E. Trip Hopping Snare [30]
        0x2F. Trip Hopping Snare [31]
        0x30. Trip Hopping Snare [32]
        0x31. Trip Hopping Snare [33]
        0x32. Trip Hopping Snare [34]
        0x33. Trip Hopping Snare [35]
        0x34. Trip Hopping Snare [36]
        0x35. Trip Hopping Snare [37]
        0x36. Trip Hopping Snare [38]
        0x37. Trip Hopping Snare [39]
        0x38. Trip Hopping Snare [40]
        0x39. Trip Hopping Snare [41]
        0x3A. Trip Hopping Snare [42]
        0x3B. Trip Hopping Snare [43]
        0x3C. Trip Hopping Snare [44]
        0x3D. Trip Hopping Snare [45]
        0x3E. Trip Hopping Snare [46]
        0x3F. Trip Hopping Snare [47]
        ```

    ??? audiobank "Audiobank 0x08 (Kakariko Village (Guitar))"

        Sequences that use this audiobank are listed below:
        
        * `0x27: Kakariko Village (Guitar, Child) [1]`
        * `0x4C: Windmill Hut`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x08`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Harmonica
        0x01. Nylon Guitar (Release: 233)
        0x02. Nylon Guitar (Release: 234)
        0x03. Ocarina
        0x04. Glockenspiel
        0x05. Accordion
        0x06. Accordion
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x08`. This percussion set is referred to as "Tambourine Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Tambourine Slap: `A1 (21)` to `B3 (47)`
        - Tambourine Tap: `C4 (48)` to `C♯4 (49)`
        - Tambourine Shake: `D4 (50)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Tambourine Slap [1]
        0x01. Tambourine Slap [2]
        0x02. Tambourine Slap [3]
        0x03. Tambourine Slap [4]
        0x04. Tambourine Slap [5]
        0x05. Tambourine Slap [6]
        0x06. Tambourine Slap [7]
        0x07. Tambourine Slap [8]
        0x08. Tambourine Slap [9]
        0x09. Tambourine Slap [10]
        0x0A. Tambourine Slap [11]
        0x0B. Tambourine Slap [12]
        0x0C. Tambourine Slap [13]
        0x0D. Tambourine Slap [14]
        0x0E. Tambourine Slap [15]
        0x0F. Tambourine Slap [16]
        0x10. Tambourine Slap [17]
        0x11. Tambourine Slap [18]
        0x12. Tambourine Slap [19]
        0x13. Tambourine Slap [20]
        0x14. Tambourine Slap [21]
        0x15. Tambourine Slap [22]
        0x16. Tambourine Slap [23]
        0x17. Tambourine Slap [24]
        0x18. Tambourine Slap [25]
        0x19. Tambourine Slap [26]
        0x1A. Tambourine Slap [27]
        0x1B. Tambourine Tap [1]
        0x1C. Tambourine Tap [2]
        0x1D. Tambourine Shake [1]
        0x1E. Tambourine Shake [2]
        0x1F. Tambourine Shake [3]
        0x20. Tambourine Shake [4]
        0x21. Tambourine Shake [5]
        0x22. Tambourine Shake [6]
        0x23. Tambourine Shake [7]
        0x24. Tambourine Shake [8]
        0x25. Tambourine Shake [9]
        0x26. Tambourine Shake [10]
        0x27. Tambourine Shake [11]
        0x28. Tambourine Shake [12]
        0x29. Tambourine Shake [13]
        0x2A. Tambourine Shake [14]
        0x2B. Tambourine Shake [15]
        0x2C. Tambourine Shake [16]
        0x2D. Tambourine Shake [17]
        0x2E. Tambourine Shake [18]
        0x2F. Tambourine Shake [19]
        0x30. Tambourine Shake [20]
        0x31. Tambourine Shake [21]
        0x32. Tambourine Shake [22]
        0x33. Tambourine Shake [23]
        0x34. Tambourine Shake [24]
        0x35. Tambourine Shake [25]
        0x36. Tambourine Shake [25*]
        0x37. Tambourine Shake [25*]
        0x38. Tambourine Shake [25*]
        0x39. Tambourine Shake [25*]
        0x3A. Tambourine Shake [25*]
        0x3B. Tambourine Shake [25*]
        0x3C. Tambourine Shake [25*]
        0x3D. Tambourine Shake [25*]
        0x3E. Tambourine Shake [25*]
        0x3F. Tambourine Shake [25*]
        ```

    ??? audiobank "Audiobank 0x09 (Harp & Strings)"

        Sequences that use this audiobank are listed below:
        
        * `0x28: Great Fairy's Fountain`
        * `0x29: Zelda's Theme`
        * `0x3A: Temple of Time`
        * `0x3D: Fanfare: Learned a Song!`
        * `0x4B: Deku Tree's Theme`
        * `0x4F: Sheik's Theme`
        * `0x57: Ptr to Great Fairy's Fountain (File Select)`
        * `0x66: Ending Cutscene ~Ocarina of Time~`
        * `0x6A: End Credits & Staff Roll [4]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x09`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Harp
        0x01. Harp
        0x02. Harp
        0x03. Harp ALT (Mid Only)
        0x04. Strings ALT (Attack Time: 32)
        0x05. Ocarina
        0x06. Male Choir
        0x07. Male Choir
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x09`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x0A (Fire Temple)"

        This audiobank entry contains data not only for Ocarina of Time version `1.0`, but also version `1.2` of the game where the chants have been "removed" (the sequence has been changed, and the audiobank expanded instead of actually removing the data [needs confirmation]).

        Sequences that use this audiobank are listed below:
        
        * `0x2A: Fire Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        !!! warning "Version Difference"
            Version `1.2` has `14` instruments for the `NUM_INST` variable instead of `10`; the audiobank was expanded in subsequent versions of the game. [needs confirmation]

        ## Instruments (Program Name: 0x00 to 0x0D)
        Below is a list of the instruments inside of audiobank `0x0A`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0D (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Chant 1 & 2
        0x01. Chant 3
        0x02. Chant 3
        0x03. Bass Marimba
        0x04. ⛔ (nullptr)
        0x05. Wind
        0x06. Metal Bell
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ⚠️ Below are for Version 1.2 Only ⚠️
        0x0A. Male Choir
        0x0B. Male Choir
        0x0C. Female Choir
        0x0D. Female Choir
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x0A`. This percussion set is referred to as "Lute & Tambourine Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Lute & Tambourine Low: `A1 (21)` to `C♯3 (37)`
        - Lute & Tambourine High: `D3 (38)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Lute & Tambourine Low [1]
        0x01. Lute & Tambourine Low [2]
        0x02. Lute & Tambourine Low [3]
        0x03. Lute & Tambourine Low [4]
        0x04. Lute & Tambourine Low [5]
        0x05. Lute & Tambourine Low [6]
        0x06. Lute & Tambourine Low [7]
        0x07. Lute & Tambourine Low [8]
        0x08. Lute & Tambourine Low [9]
        0x09. Lute & Tambourine Low [10]
        0x0A. Lute & Tambourine Low [11]
        0x0B. Lute & Tambourine Low [12]
        0x0C. Lute & Tambourine Low [13]
        0x0D. Lute & Tambourine Low [14]
        0x0E. Lute & Tambourine Low [15]
        0x0F. Lute & Tambourine Low [16]
        0x10. Lute & Tambourine Low [17]
        0x11. Lute & Tambourine High [1]
        0x12. Lute & Tambourine High [2]
        0x13. Lute & Tambourine High [3]
        0x14. Lute & Tambourine High [4]
        0x15. Lute & Tambourine High [5]
        0x16. Lute & Tambourine High [6]
        0x17. Lute & Tambourine High [7]
        0x18. Lute & Tambourine High [8]
        0x19. Lute & Tambourine High [9]
        0x1A. Lute & Tambourine High [10]
        0x1B. Lute & Tambourine High [11]
        0x1C. Lute & Tambourine High [12]
        0x1D. Lute & Tambourine High [13]
        0x1E. Lute & Tambourine High [14]
        0x1F. Lute & Tambourine High [15]
        0x20. Lute & Tambourine High [16]
        0x21. Lute & Tambourine High [17]
        0x22. Lute & Tambourine High [18]
        0x23. Lute & Tambourine High [19]
        0x24. Lute & Tambourine High [20]
        0x25. Lute & Tambourine High [21]
        0x26. Lute & Tambourine High [22]
        0x27. Lute & Tambourine High [23]
        0x28. Lute & Tambourine High [24]
        0x29. Lute & Tambourine High [25]
        0x2A. Lute & Tambourine High [26]
        0x2B. Lute & Tambourine High [27]
        0x2C. Lute & Tambourine High [28]
        0x2D. Lute & Tambourine High [29]
        0x2E. Lute & Tambourine High [30]
        0x2F. Lute & Tambourine High [31]
        0x30. Lute & Tambourine High [32]
        0x31. Lute & Tambourine High [33]
        0x32. Lute & Tambourine High [34]
        0x33. Lute & Tambourine High [35]
        0x34. Lute & Tambourine High [36]
        0x35. Lute & Tambourine High [37]
        0x36. Lute & Tambourine High [38]
        0x37. Lute & Tambourine High [39]
        0x38. Lute & Tambourine High [40]
        0x39. Lute & Tambourine High [41]
        0x3A. Lute & Tambourine High [42]
        0x3B. Lute & Tambourine High [43]
        0x3C. Lute & Tambourine High [44]
        0x3D. Lute & Tambourine High [45]
        0x3E. Lute & Tambourine High [46]
        0x3F. Lute & Tambourine High [47]
        ```

    ??? audiobank "Audiobank 0x0B (Dodongo's Cavern)"

        Sequences that use this audiobank are listed below:
        
        * `0x18: Dodongo's Cavern`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 4`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x03)
        Below is a list of the instruments inside of audiobank `0x0B`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x03 (3)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Wind Roar
        0x01. Lore Drone
        0x02. Metal Grind
        0x03. Spaceosphere
        ```

    ??? audiobank "Audiobank 0x0C (Forest Temple)"

        Sequences that use this audiobank are listed below:
        
        * `0x2C: Forest Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 3`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x02)
        Below is a list of the instruments inside of audiobank `0x0C`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x02 (2)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Digi Pad 04
        0x01. Flute Chant
        0x02. Bamboo Chimes
        ```

    ??? audiobank "Audiobank 0x0D (Lon Lon Ranch)"

        Sequences that use this audiobank are listed below:
        
        * `0x2F: Lon Lon Ranch`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x0D`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Malon Voice (Release: 248)
        0x01. Malon Voice (Release: 247)
        0x02. Sustain Guitar
        0x03. Sustain Guitar ALT
        0x04. Sustain Guitar ALT
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. Strings
        0x0C. Strings
        0x0D. Fiddle
        0x0E. Fiddle
        0x0F. Carillon Bell (Unused in Sequence)
        ```

    ??? audiobank "Audiobank 0x0E (Goron City)"

        Audiobank `0x0E` is a bit of a special audiobank, it uses a different audiotable than other audiobanks and the offsets reference data later in the audiotable causing the ADPCM data for their samples to be split; however, `SEQ64` will automatically update their sample location upon importing.

        Sequences that use this audiobank are listed below:
        
        * `0x30: Goron City`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 5`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 5`

        ## Instruments (Program Name: 0x00 to 0x04)
        Below is a list of the instruments inside of audiobank `0x0E`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x04 (4)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bent Drum
        0x01. Conga & Slap
        0x02. Cuica
        0x03. Bass Marimba
        0x04. Bass Marimba
        ```

    ??? audiobank "Audiobank 0x0F (Kokiri Forest)"

        Sequences that use this audiobank are listed below:
        
        * `0x3C: Kokiri Forest`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x0F`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Oboe
        0x02. Clarinet
        0x03. Bassoon
        0x04. French Horn
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. Harpsichord
        0x0E. Harp
        0x0F. Marimba
        ```

    ??? audiobank "Audiobank 0x10 (Spirit Temple)"

        Audiobank `0x10` is a bit of a special audiobank, it uses a different audiotable than other audiobanks and the offsets reference data later in the audiotable causing the ADPCM data for their samples to be split; however, `SEQ64` will automatically update their sample location upon importing.

        Sequences that use this audiobank are listed below:
        
        * `0x3F: Spirit Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 6`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x10`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Digi Pad 04 ALT
        0x01. Synth Strings
        0x02. Duduk ALT
        0x03. Conga & Slap
        0x04. Synth Strings
        0x05. Duduk
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ##Drums
        Below is a list of the drums inside of audiobank `0x10`. This percussion set is referred to as "Gong & Chimes Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Gong: `A1 (21)` to `F♯4 (54)`
        - Chimes: `G4 (55)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Gong [1]
        0x01. Gong [2]
        0x02. Gong [3]
        0x03. Gong [4]
        0x04. Gong [5]
        0x05. Gong [6]
        0x06. Gong [7]
        0x07. Gong [8]
        0x08. Gong [9]
        0x09. Gong [10]
        0x0A. Gong [11]
        0x0B. Gong [12]
        0x0C. Gong [13]
        0x0D. Gong [14]
        0x0E. Gong [15]
        0x0F. Gong [16]
        0x10. Gong [17]
        0x11. Gong [18]
        0x12. Gong [19]
        0x13. Gong [20]
        0x14. Gong [21]
        0x15. Gong [22]
        0x16. Gong [23]
        0x17. Gong [24]
        0x18. Gong [25]
        0x19. Gong [26]
        0x1A. Gong [27]
        0x1B. Gong [28]
        0x1C. Gong [29]
        0x1D. Gong [30]
        0x1E. Gong [31]
        0x1F. Gong [32]
        0x20. Gong [33]
        0x21. Gong [34]
        0x22. Chimes [1]
        0x23. Chimes [2]
        0x24. Chimes [3]
        0x25. Chimes [4]
        0x26. Chimes [5]
        0x27. Chimes [6]
        0x28. Chimes [7]
        0x29. Chimes [8]
        0x2A. Chimes [9]
        0x2B. Chimes [10]
        0x2C. Chimes [11]
        0x2D. Chimes [12]
        0x2E. Chimes [13]
        0x2F. Chimes [14]
        0x30. Chimes [15]
        0x31. Chimes [16]
        0x32. Chimes [17]
        0x33. Chimes [18]
        0x34. Chimes [19]
        0x35. Chimes [20]
        0x36. Chimes [21]
        0x37. Chimes [22]
        0x38. Chimes [23]
        0x39. Chimes [24]
        0x3A. Chimes [25]
        0x3B. Chimes [26]
        0x3C. Chimes [27]
        0x3D. Chimes [28]
        0x3E. Chimes [29]
        0x3F. Chimes [30]
        ```

    ??? audiobank "Audiobank 0x11 (Horse Race)"

        Sequences that use this audiobank are listed below:
        
        * `0x40: Horse Race`
        * `0x41: Fanfare: Horse Race Victory!`
        * `0x42: Ingo's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x11`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Banjo
        0x01. Banjo
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. Pizz. Double Bass
        0x06. Harmonica
        0x07. Nylon Guitar
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. ⛔ (nullptr)
        0x0D. Fiddle
        0x0E. Fiddle
        ```

    ??? audiobank "Audiobank 0x12 (Warp Songs)"

        Sequences that use this audiobank are listed below:
        
        * `0x25: Warp Song: "Prelude of Light"`
        * `0x33: Warp Song: "Bolero of Fire"`
        * `0x34: Warp Song: "Minuet of Forest"`
        * `0x35: Warp Song: "Serenade of Water"`
        * `0x36: Warp Song: "Requiem of Spirit"`
        * `0x37: Warp Song: "Nocturne of Shadow"`
        * `0x59: Fanfare: Open the Door of Time!`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x12`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Harp
        0x01. Harp
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. Strings ALT (Attack Time: 32)
        0x05. Ocarina
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x12`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x13 (Chamber of the Sages)"

        Sequences that use this audiobank are listed below:
        
        * `0x4D: Chamber of the Sages`
        * `0x56: Legend of Hyrule (Short Version)`
        * `0x5D: Fanfare: Bridge of the Six Sages!`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 4`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x03)
        Below is a list of the instruments inside of audiobank `0x13`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x03 (3)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Female Choir
        0x01. Female Choir
        0x02. Harp
        0x03. Glockenspiel
        ```

    ??? audiobank "Audiobank 0x14 (Minigame Shop)"

        Sequences that use this audiobank are listed below:
        
        * `0x4E: Minigame Shop`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x14`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Clarinet
        0x02. Clarinet
        0x03. Accordion
        0x04. Glockenspiel
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x14`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x15 (Zora's Domain)"

        Sequences that use this audiobank are listed below:
        
        * `0x50: Zora's Domain`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x15`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Steel Drum
        0x01. Digi Pad 04
        0x02. Nylon Guitar
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x15`. This percussion set is referred to as "Conga & Shaker Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Conga Closed: `A1 (21)` to `F3 (41)`
        - Conga Open: `F♯3 (42)` to `C5 (60)`
        - Conga Slap: `C♯5 (61)` to `G♯6 (80)`
        - Shaker: `A6 (81)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Conga Closed [1]
        0x01. Conga Closed [2]
        0x02. Conga Closed [3]
        0x03. Conga Closed [4]
        0x04. Conga Closed [5]
        0x05. Conga Closed [6]
        0x06. Conga Closed [7]
        0x07. Conga Closed [8]
        0x08. Conga Closed [9]
        0x09. Conga Closed [10]
        0x0A. Conga Closed [11]
        0x0B. Conga Closed [12]
        0x0C. Conga Closed [13]
        0x0D. Conga Closed [14]
        0x0E. Conga Closed [15]
        0x0F. Conga Closed [16]
        0x10. Conga Closed [17]
        0x11. Conga Closed [18]
        0x12. Conga Closed [19]
        0x13. Conga Closed [20]
        0x14. Conga Closed [21]
        0x15. Conga Open [1]
        0x16. Conga Open [2]
        0x17. Conga Open [3]
        0x18. Conga Open [4]
        0x19. Conga Open [5]
        0x1A. Conga Open [6]
        0x1B. Conga Open [7]
        0x1C. Conga Open [8]
        0x1D. Conga Open [9]
        0x1E. Conga Open [10]
        0x1F. Conga Open [11]
        0x20. Conga Open [12]
        0x21. Conga Open [13]
        0x22. Conga Open [14]
        0x23. Conga Open [15]
        0x24. Conga Open [16]
        0x25. Conga Open [17]
        0x26. Conga Open [18]
        0x27. Conga Open [19]
        0x28. Conga Slap [1]
        0x29. Conga Slap [2]
        0x2A. Conga Slap [3]
        0x2B. Conga Slap [4]
        0x2C. Conga Slap [5]
        0x2D. Conga Slap [6]
        0x2E. Conga Slap [7]
        0x2F. Conga Slap [8]
        0x30. Conga Slap [9]
        0x31. Conga Slap [10]
        0x32. Conga Slap [11]
        0x33. Conga Slap [12]
        0x34. Conga Slap [13]
        0x35. Conga Slap [14]
        0x36. Conga Slap [15]
        0x37. Conga Slap [16]
        0x38. Conga Slap [17]
        0x39. Conga Slap [18]
        0x3A. Conga Slap [19]
        0x3B. Conga Slap [20]
        0x3C. Shaker [1]
        0x3D. Shaker [2]
        0x3E. Shaker [3]
        0x3F. Shaker [4]
        ```

    ??? audiobank "Audiobank 0x16 (Item Shop)"

        Sequences that use this audiobank are listed below:
        
        * `0x55: Item Shop`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 11`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0A)
        Below is a list of the instruments inside of audiobank `0x16`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0A (10)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Nylon Guitar
        0x01. Accordion
        0x02. Pizz. Double Bass
        0x03. Trombone
        0x04. Trumpet
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Cowbell
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x16`. This percussion set is referred to as "Conga & Shaker Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Conga Closed: `A1 (21)` to `F3 (41)`
        - Conga Open: `F♯3 (42)` to `C5 (60)`
        - Conga Slap: `C♯5 (61)` to `G♯6 (80)`
        - Shaker: `A6 (81)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Conga Closed [1]
        0x01. Conga Closed [2]
        0x02. Conga Closed [3]
        0x03. Conga Closed [4]
        0x04. Conga Closed [5]
        0x05. Conga Closed [6]
        0x06. Conga Closed [7]
        0x07. Conga Closed [8]
        0x08. Conga Closed [9]
        0x09. Conga Closed [10]
        0x0A. Conga Closed [11]
        0x0B. Conga Closed [12]
        0x0C. Conga Closed [13]
        0x0D. Conga Closed [14]
        0x0E. Conga Closed [15]
        0x0F. Conga Closed [16]
        0x10. Conga Closed [17]
        0x11. Conga Closed [18]
        0x12. Conga Closed [19]
        0x13. Conga Closed [20]
        0x14. Conga Closed [21]
        0x15. Conga Open [1]
        0x16. Conga Open [2]
        0x17. Conga Open [3]
        0x18. Conga Open [4]
        0x19. Conga Open [5]
        0x1A. Conga Open [6]
        0x1B. Conga Open [7]
        0x1C. Conga Open [8]
        0x1D. Conga Open [9]
        0x1E. Conga Open [10]
        0x1F. Conga Open [11]
        0x20. Conga Open [12]
        0x21. Conga Open [13]
        0x22. Conga Open [14]
        0x23. Conga Open [15]
        0x24. Conga Open [16]
        0x25. Conga Open [17]
        0x26. Conga Open [18]
        0x27. Conga Open [19]
        0x28. Conga Slap [1]
        0x29. Conga Slap [2]
        0x2A. Conga Slap [3]
        0x2B. Conga Slap [4]
        0x2C. Conga Slap [5]
        0x2D. Conga Slap [6]
        0x2E. Conga Slap [7]
        0x2F. Conga Slap [8]
        0x30. Conga Slap [9]
        0x31. Conga Slap [10]
        0x32. Conga Slap [11]
        0x33. Conga Slap [12]
        0x34. Conga Slap [13]
        0x35. Conga Slap [14]
        0x36. Conga Slap [15]
        0x37. Conga Slap [16]
        0x38. Conga Slap [17]
        0x39. Conga Slap [18]
        0x3A. Conga Slap [19]
        0x3B. Conga Slap [20]
        0x3C. Shaker [1]
        0x3D. Shaker [2]
        0x3E. Shaker [3]
        0x3F. Shaker [4]
        ```

    ??? audiobank "Audiobank 0x17 (Ice Cavern)"

        Sequences that use this audiobank are listed below:
        
        * `0x58: Ice Cavern`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 4`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x03)
        Below is a list of the instruments inside of audiobank `0x17`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x03 (3)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Fantasia
        0x01. Fantasia ALT
        0x02. Wind
        0x03. Fantasia ALT
        ```

    ??? audiobank "Audiobank 0x18 (Shadow Temple)"

        Sequences that use this audiobank are listed below:
        
        * `0x5B: Shadow Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 9`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x08)
        Below is a list of the instruments inside of audiobank `0x18`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x08 (8)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Djembe
        0x01. Wind Roar
        0x02. Lore Drone & Shine
        0x03. Male Choir
        0x04. Female Choir
        0x05. ⛔ (nullptr)
        0x06. Chant 3
        0x07. Spaceosphere
        0x08. Harpsichord
        ```

    ??? audiobank "Audiobank 0x19 (Water Temple)"

        Sequences that use this audiobank are listed below:
        
        * `0x5C: Water Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 8`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x07)
        Below is a list of the instruments inside of audiobank `0x19`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x07 (7)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Gong & Chimes
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. Fantasia
        0x05. Bamboo Chimes
        0x06. Digi Pad 04
        0x07. Bouzouki
        ```

    ??? audiobank "Audiobank 0x1A (Piano (Unused))"

        This audiobank is not used anywhere in-game.

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x1A`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. ⛔ (nullptr)
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. ⛔ (nullptr)
        0x0D. Piano ALT (Splits: 22 & 44, Release: 93)
        0x0E. Piano ALT (Splits: 22 & 44, Release: 93)
        ```

    ??? audiobank "Audiobank 0x1B (Gerudo Valley)"

        Sequences that use this audiobank are listed below:
        
        * `0x5F: Gerudo Valley`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 12`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0B)
        Below is a list of the instruments inside of audiobank `0x1B`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0B (11)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Trumpet
        0x01. Trombone
        0x02. Nylon Guitar (Release: 233)
        0x03. Nylon Guitar (Release: 219)
        0x04. ⛔ (nullptr)
        0x05. Pizz. Double Bass
        0x06. ⛔ (nullptr)
        0x07. Nylon Guitar (Release: 234)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Clap
        0x0B. Clap
        ```

    ??? audiobank "Audiobank 0x1C (Potion Shop)"

        Sequences that use this audiobank are listed below:
        
        * `0x60: Potion Shop`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 5`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x04)
        Below is a list of the instruments inside of audiobank `0x1C`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x04 (4)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Djembe
        0x02. ⛔ (nullptr)
        0x03. Bent Drum
        0x04. Gong & Chimes
        ```

    ??? audiobank "Audiobank 0x1D (Koume & Kotake's Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x61: Koume & Kotake's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 12`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0B)
        Below is a list of the instruments inside of audiobank `0x1D`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0B (11)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Djembe
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. Piccolo
        0x06. ⛔ (nullptr)
        0x07. Piccolo
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x1D`. This percussion set is referred to as "Gong & Chimes Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Gong: `A1 (21)` to `F♯4 (54)`
        - Chimes: `G4 (55)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Gong [1]
        0x01. Gong [2]
        0x02. Gong [3]
        0x03. Gong [4]
        0x04. Gong [5]
        0x05. Gong [6]
        0x06. Gong [7]
        0x07. Gong [8]
        0x08. Gong [9]
        0x09. Gong [10]
        0x0A. Gong [11]
        0x0B. Gong [12]
        0x0C. Gong [13]
        0x0D. Gong [14]
        0x0E. Gong [15]
        0x0F. Gong [16]
        0x10. Gong [17]
        0x11. Gong [18]
        0x12. Gong [19]
        0x13. Gong [20]
        0x14. Gong [21]
        0x15. Gong [22]
        0x16. Gong [23]
        0x17. Gong [24]
        0x18. Gong [25]
        0x19. Gong [26]
        0x1A. Gong [27]
        0x1B. Gong [28]
        0x1C. Gong [29]
        0x1D. Gong [30]
        0x1E. Gong [31]
        0x1F. Gong [32]
        0x20. Gong [33]
        0x21. Gong [34]
        0x22. Chimes [1]
        0x23. Chimes [2]
        0x24. Chimes [3]
        0x25. Chimes [4]
        0x26. Chimes [5]
        0x27. Chimes [6]
        0x28. Chimes [7]
        0x29. Chimes [8]
        0x2A. Chimes [9]
        0x2B. Chimes [10]
        0x2C. Chimes [11]
        0x2D. Chimes [12]
        0x2E. Chimes [13]
        0x2F. Chimes [14]
        0x30. Chimes [15]
        0x31. Chimes [16]
        0x32. Chimes [17]
        0x33. Chimes [18]
        0x34. Chimes [19]
        0x35. Chimes [20]
        0x36. Chimes [21]
        0x37. Chimes [22]
        0x38. Chimes [23]
        0x39. Chimes [24]
        0x3A. Chimes [25]
        0x3B. Chimes [26]
        0x3C. Chimes [27]
        0x3D. Chimes [28]
        0x3E. Chimes [29]
        0x3F. Chimes [30]
        ```

    ??? audiobank "Audiobank 0x1E (Ganondorf's Organ)"

        Sequences that use this audiobank are listed below:
        
        * `0x2E: Ganon's Tower`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 5`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x04)
        Below is a list of the instruments inside of audiobank `0x1E`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x04 (4)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Pipe Organ
        0x01. Pipe Organ
        0x02. Pipe Organ
        0x03. ⛔ (nullptr)
        0x04. French Horn
        ```

    ??? audiobank "Audiobank 0x1F (Inside Ganon's Castle)"

        Sequences that use this audiobank are listed below:
        
        * `0x63: Inside Ganon's Castle`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 8`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x07)
        Below is a list of the instruments inside of audiobank `0x1F`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x07 (7)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Wind Roar
        0x02. Lore Drone & Shine
        0x03. Male Choir
        0x04. Piano
        0x05. Piano ALT 3 (Splits: 22 &amp; 44, Release Rate: 93)
        0x06. ⛔ (nullptr)
        0x07. Spaceosphere
        ```

    ??? audiobank "Audiobank 0x20 (Adversarial Orchestra)"

        Sequences that use this audiobank are listed below:
        
        * `0x5E: Fanfare: Seal of the Six Sages!`
        * `0x64: Battle: Great Evil King, Ganondorf`
        * `0x65: Battle: Ganon`
        * `0x6B: Battle: Boss [2]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x20`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Female Choir
        0x02. Male Choir
        0x03. ⛔ (nullptr)
        0x04. French Horn
        0x05. Trumpet
        0x06. Trombone
        0x07. Tuba
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. ⛔ (nullptr)
        0x0D. Piano
        0x0E. ⛔ (nullptr)
        0x0F. Marimba
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x20`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x21 (Ending Orchestra [1])"
  
        Sequences that use this audiobank are listed below:
        
        * `0x67: End Credits & Staff Roll [1]`
        * `0x69: End Credits & Staff Roll [3]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x21`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Malon Voice (Release: 248)
        0x01. Malon Voice (Release: 247)
        0x02. Clarinet
        0x03. ⛔ (nullptr)
        0x04. French Horn
        0x05. Oboe
        0x06. Harp
        0x07. Fiddle
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. ⛔ (nullptr)
        0x0D. Carillon Bell
        0x0E. Harp
        0x0F. Female Choir
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x21`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x22 (Ending Orchestra [2])"

        Sequences that use this audiobank are listed below:
        
        * `0x68: End Credits & Staff Roll [2]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x22`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Ocarina
        0x02. Bassoon
        0x03. Oboe
        0x04. Female Choir
        0x05. Tambourine
        0x06. Harp
        0x07. Glockenspiel
        0x08. Malon Voice (Release: 248)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. French Horn
        0x0E. Male Choir
        0x0F. Cuica
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x22`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x23 (Fanfare Orchestra)"

        Sequences that use this audiobank are listed below:
        
        * `0x20: Fanfare: Game Over!`
        * `0x22: Fanfare: Get an Item!`
        * `0x24: Fanfare: Get a Heart Container!`
        * `0x39: Fanfare: Get a Heart Piece!`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x23`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. ⛔ (nullptr)
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. Trumpet
        0x06. Trombone
        0x07. Tuba
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. ⛔ (nullptr)
        0x0D. ⛔ (nullptr)
        0x0E. Harp
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x23`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Orchestra Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Orchestra Bass Drum [1]
        0x01. Orchestra Bass Drum [2]
        0x02. Orchestra Bass Drum [3]
        0x03. Orchestra Bass Drum [4]
        0x04. Orchestra Bass Drum [5]
        0x05. Orchestra Bass Drum [6]
        0x06. Orchestra Bass Drum [7]
        0x07. Orchestra Bass Drum [8]
        0x08. Orchestra Bass Drum [9]
        0x09. Orchestra Bass Drum [10]
        0x0A. Orchestra Bass Drum [11]
        0x0B. Orchestra Bass Drum [12]
        0x0C. Orchestra Bass Drum [13]
        0x0D. Orchestra Bass Drum [14]
        0x0E. Orchestra Bass Drum [15]
        0x0F. Orchestra Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x24 (Kaepora Gaebora's Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x5A: Kaepora Gaebora's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x24`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Oboe
        0x02. ⛔ (nullptr)
        0x03. Bassoon
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. ⛔ (nullptr)
        0x0E. Harp
        ```

    ??? audiobank "Audiobank 0x25 (Unused Bank)"

        Audiobank `0x25` only contains instruments with bad pointers and broken samples. This audiobank is not used anywhere in-game, it's most likely leftover data from the development cycle; however, since it is unused that means it can be used for *anything*. Do not import the instruments from this audiobank, they will only place garbage data.

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 2`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 0`

        ## Instruments (Program Name: 0x00 to 0x01)
        Below is a list of the instruments inside of audiobank `0x25`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x01 (1)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Junk [1]
        0x01. Junk [2]
        ```

=== "Majora's Mask Audiobanks"

    !!! info "Instrument Names"
        Some instruments are named after the closest instrument known by the community, though some are named after the name of the sample that was used to create the instrument (e.g. ELVES, PIT HIT 1, OMINOUSITY, EERIE WIND, TUNNEL RAIN, Mystic Pad, ICELAND 1, Fantasia, DANGER).

    ??? audiobank "Audiobank 0x00 (SFX Bank)"

        Audiobank `0x00` is the first of the two main SFX audiobanks. It's mostly guesswork for what most of the sound effects are as mapping them out is done completely by listening to the samples themselves in `N64 Soundlist Tool` (for which many samples are pitched up or down in-game, so the pitches are "off" when being played back) and figuring out what sound is used where in the game.

        Sequences that use this audiobank are listed below:
        
        * `0x00: Master Sequence`
        * `0x32: Ocarina Song: "Epona's Song"`
        * `0x33: Ocarina Song: "Sun's Song"`
        * `0x34: Ocarina Song: "Song of Time"`
        * `0x35: Ocarina Song: "Song of Storms"`
        * `0x47: Ocarina Song: "Song of Soaring"`
        * `0x48: Ocarina Song: "Song of Healing"`
        * `0x49: Ocarina Song: "Song of Inverted Time"`
        * `0x4A: Ocarina Song: "Song of Double Time"`
        * `0x51: Ocarina Song: "Lullaby Intro"`
        * `0x5A: Don Gero's Theme ("Frog Acapella")`
        * `0x5B: Ocarina Song: "Sonata of Awakening"`
        * `0x5C: Ocarina Song: "Goron Lullaby"`
        * `0x5D: Ocarina Song: "New Wave Bossa Nova"`
        * `0x5E: Ocarina Song: "Elegy of Emptiness"`
        * `0x5F: Ocarina Song: "Oath to Order"`
        * `0x61: Ptr to Ocarina Song: "Lullaby Intro"`
        * `0x7A: Music Box House (Silence)?`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 122`
        * `NUM_DRUM: 16`
        * `NUM_SFX: 197`
        * `ATnum: 0`

        ## Instruments (Program Number: 0x00 to 0x79)
        Below is a list of the "instruments" inside of audiobank `0x00`. These work exactly as regular instruments do, you can even import them into a custom audiobank as an instrument and use it in a sequence just like any regular instrument; and this is a common structure for the sound effects within the game.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x79 (121)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Some sound effects using the instrument structure have multiple samples, the sound effects using multiple samples indicate which region contains which sound effect sample (e.g. `0x00: Low: SFX name, Mid: SFX Name, High: SFX Name`). Any sound effects without multiple regions use the mid (primary) sample.

        **Instrument List:**
        ```
        0x00. Dirt Footstep SFX
        0x01. Sand Footstep SFX
        0x02. Stone Footstep SFX?
        0x03. Water Footstep SFX
        0x04. Splash Footstep SFX
        0x05. Dirt Footstep SFX 2?
        0x06. Wood Footstep SFX?
        0x07. Grass Footstep SFX?
        0x08. Chest reveal SFX, Ice Switch SFX, and Skull Kid Spotlight SFX
        0x09. Snow Footstep SFX?
        0x0A. Unknown SFX (Rock related?)
        0x0B. Unknown SFX (Footstep?)
        0x0C. Splash SFX 1
        0x0D. Splash SFX 2
        0x0E. Unknown Sand SFX 1
        0x0F. Mid: Egg Hatch SFX 1, High: Wind SFX
        0x10. Unknown Sand SFX 2
        0x11. Unknown White Noise SFX 1
        0x12. Unknown White Noise SFX 2
        0x13. Splash SFX 3
        0x14. Swimming SFX
        0x15. Mid: Drum SFX?, High: Gunshot SFX
        0x16. Wood Footstep SFX 2?
        0x17. Snow Footstep SFX 2?
        0x18. Mid: Fairy Flying SFX 1?, High: Fairy Bell SFX 1
        0x19. Stone Footstep SFX 2?
        0x1A. Mid: Sword Clink SFX 1, High: Sword Clink SFX 2
        0x1B. Scratch SFX?
        0x1C. Link Sword Sheathe SFX
        0x1D. Link Sword Unsheathe SFX
        0x1E. Whoosh SFX
        0x1F. Unknown Whoosh SFX
        0x20. Metal Clang SFX
        0x21. Mid: Bow Draw SFX, High: Bow Twang SFX
        0x22. Mid: Hookshot Chain SFX, High: Bat Noise SFX?
        0x23. Mid: Bombchu Fuse SFX, High: Bombchu Moving SFX
        0x24. Bank Stamp SFX (OOT Megaton Hammer)
        0x25. Like Like SFX?
        0x26. Arrow Hitting Wood/Festival Hammer SFX
        0x27. Whoosh SFX 2 (Boomerang?)
        0x28. Unknown SFX (Rock related?)
        0x29. Mid: Pop SFX, High: Cursor SFX?
        0x2A. Robotic Buzzing SFX
        0x2B. Mid: Unknown SFX, High: Song of Double Time Tick SFX
        0x2C. Mid: Lens of Truth SFX, High: Whoosh SFX 3
        0x2D. Mid: Door Open SFX, High: Door Close SFX
        0x2E. Mid: Digi Pad 04 SFX?, High: Squeaking SFX?
        0x2F. Explosion SFX
        0x30. Horse Gallop SFX
        0x32. Mid: Horse Whinny SFX, High: Horse Snort SFX
        0x31. ⛔ (nullptr)
        0x33. Mid: Running Water SFX, High: White Noise SFX 1 (Waterfall)
        0x34. Ocarina SFX 1 (Special Effect)
        0x35. Ocarina SFX 2
        0x36. Mid: Stone Moving on Stone SFX, High: Metal Door Closing SFX
        0x37. Rock Rolling SFX?
        0x38. Mid: Lava Bubbling SFX, High: Soup Bubbling SFX
        0x39. Chain Pulley SFX
        0x3A. Chicken Cluck SFX
        0x3B. Door Thud SFX
        0x3C. Wind SFX
        0x3D. Mid: Rooster Crow SFX, High: Wolf Howl SFX
        0x3E. Light Splash SFX (Fish?)
        0x3F. Mid: Spider House Portrait Fall SFX, High: Stick Clack SFX
        0x40. Fairy Flying SFX 2? (Fairy Related)
        0x41. Dawn of the First Day SFX
        0x42. Mid: Door Creak SFX, High: Door Creak Low SFX
        0x43. Unknown SFX
        0x44. Glass Hum SFX
        0x45. Fairy Flying SFX 3? (Fairy Related)
        0x46. Mid: Electric SFX, High: Pot Break SFX
        0x47. Water Drip SFX
        0x48. Water Bubbling SFX (Gyorg Cutscene?)
        0x49. Mid: Fire Crackle SFX, High: Cow Moo SFX
        0x4A. Mid: Balloon Inflate SFX, High: Thunder SFX
        0x4B. Unknown SFX
        0x4C. Unknown SFX
        0x4D. Mid: Wind SFX?, High: Revving SFX
        0x4E. Mid: Cloth Flutter SFX, High: Wing Flap SFX
        0x4F. Mid: Carpenters and Soldiers Arguing SFX, High: Glass Shatter SFX (Ice?)
        0x50. Scratch SFX 2?
        0x51. Mid: Dodongo Roar SFX, High: Dog Bark SFX
        0x52. Woodwind Noise SFX
        0x53. Bandoneon SFX
        0x54. Piano/Harp SFX?
        0x55. Lulu's Voice SFX
        0x56. Fairy Bell SFX 2
        0x57. Mid: Wrong Note SFX, High: Unknown Metal Sound SFX
        0x58. Bird Chirp SFX
        0x59. Harp SFX
        0x5A. Mid: Camera Alignment SFX, High: Lock-on SFX
        0x5B. Metal Chain SFX
        0x5C. Rawhide Drum SFX (Goron)
        0x5D. Steel Str. Guitar SFX (Zora)
        0x5E. Trumpet (B3) SFX (Deku)
        0x5F. Frog Ribbit SFX
        0x60. Goron Elder's Son Voice SFX
        0x61. Mid: Beaver Talk SFX, High: Bird Tweet SFX
        0x62. Cuckoo Clock SFX
        0x63. Mid: Ocean Wave SFX, High: Same as Mid
        0x64. Carillon Bell SFX
        0x65. Eagle(?) SFX
        0x66. Orchestral Timpani SFX
        0x67. Mid: Glass Shatter SFX, High: Click SFX
        0x68. Snow Footstep SFX 3?
        0x69. Arwing Laser SFX
        0x6A. Mid: Wooden Clack/Pop/Clap/Slap SFX?, High: Gulp SFX
        0x6B. Mid: Monkey Noise SFX, Monkey Shriek SFX
        0x6C. Mid: Same as High Pitched Lower?, High: Insect Buzz Sfx?
        0x6D. Low: Dog Yelp SFX, Mid: Dog Growl SFX, High: Dog Calm Whine(?) SFX
        0x6E. Mid: Crowd Cheer SFX, High: Link Gulp? SFX
        0x6F. Goron Burnout/Skid SFX
        0x70. Egg Hatch SFX 2
        0x71. Bent Conga SFX
        0x72. Giant Voice SFX
        0x73. Piano SFX
        0x74. Fretless Bass SFX (Zora/Japas?)
        0x75. Chinese Gong SFX
        0x76. Creaking SFX
        0x77. Piccolo SFX
        0x78. Igos Du Ikana Voice SFX (Elegy)
        0x79. Grass Rustle SFX
        ```

        ## Sound Effects (Program Number: 7E)
        Below is a list of the "sound effects" inside of audiobank `0x00`. These work nearly identical to how percussion sets work except for how they are structured, they cannot be imported into audiobanks because their structure is built directly into a pointer array within `<absfxlist>`.

        You can access these sound effects when using this audiobank using MIDI program number(s): `0x7E (126)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Sound effects can only have one sample per sound effect, but some sound effect indexes point to the same sample in the audiobank. The indexes that use the same sample as another index are marked: `[Same sample as (index value)]`

        **Sound Effect List:**
        ```
        0x00. Link Voice (Attack 1)
        0x01. Link Voice (Attack 2)
        0x02. Link Voice (Attack 3)
        0x03. Link Voice (Attack 4)
        0x04. Link Voice (Attack 5)
        0x05. Link Voice (Attack 6)
        0x06. Goron Link Voice (Damage 1)
        0x07. Goron Link Voice (Damage 2?)
        0x08. Goron Link Voice (Damage 3)
        0x09. Link Voice (Damage 1)
        0x0A. Link Voice (Damage 2)
        0x0B. Link Voice (Damage 3)
        0x0C. Link Voice (Damage 4)
        0x0D. Zora Link Voice (Damage 1)
        0x0E. Link Voice (Damage 5)
        0x0F. Link Voice (Scream 1)
        0x10. Link Voice (Scream 2)
        0x11. Link Voice (Scream 2) [Same sample as 10]
        0x12. Goron Link Voice (Critical Health?)
        0x13. Zora Link Voice (Critical Health?)
        0x14. Link Voice (Grunt 1)
        0x15. Igos Du Ikana (Elegy)
        0x16. Igos Du Ikana (Elegy)
        0x17. Link Voice (Critical Health 1)
        0x18. Goron Link Voice (Fall Damage)
        0x19. Goron Link Voice (Push & Grab)
        0x1A. Link Voice (Grunt 2)
        0x1B. Link Voice (Grunt 3)
        0x1C. Link Voice ("Hup" 1)
        0x1D. Link Voice ("Ha!" 1)
        0x1E. Link Voice ("Hup" 2)
        0x1F. Link Voice ("Hup" 3)
        0x20. Link Voice ("Hyah!")
        0x21. Link Voice (Attack 7)
        0x22. Link Voice (Ledge Related?)
        0x23. Link Voice (Grab & Push 1?)
        0x24. Link Voice (Grab & Push 2?)
        0x25. Deku Link Voice (Damage 1)
        0x26. Deku Link Voice (Damage 2)
        0x27. Link Voice (Grunt 2) [Same sample as 1A]
        0x28. Link Voice (Damage 6)
        0x29. Zora Link Voice (Damage 2)
        0x2A. Link Voice (Fall Damage 1)
        0x2B. Link Voice (Fall Scream 1)
        0x2C. Link Voice (Fall Scream 2)
        0x2D. Link Voice (Fall Start 1)
        0x2E. Link Voice (Fall Start 2)
        0x2F. Link Voice (Critical Health 2)
        0x30. Link Voice (Critical Health 3)
        0x31. Link Voice (Fall Damage 2)
        0x32. Link Voice (Sliding)
        0x33. Link Voice (Drink 1)
        0x34. Link Voice (Drink 2)
        0x35. Link Voice ("Hup" 4)
        0x36. Link Voice ("Hup" 5)
        0x37. Goron Link Voice (Fall Damage) [Same sample as 18]
        0x38. Goron Link Voice (Fall Damage) [Same sample as 18]
        0x39. ⛔ (nullptr)
        0x3A. ⛔ (nullptr)
        0x3B. ⛔ (nullptr)
        0x3C. Goron Link Voice (Fall Damage) [Same sample as 18]
        0x3D. Goron Link Voice (Fall Damage) [Same sample as 18]
        0x3E. Link Voice (Ledge Climb?)
        0x3F. Link Voice (Attack 8)
        0x40. Link Voice (Grunt 1) [Same sample as 14]
        0x41. Unknown Sound [1]
        0x42. Link Voice (Damage 6?)
        0x43. Link Voice (Shiver)
        0x44. ⛔ (nullptr)
        0x45. Link Voice (Sneeze)
        0x46. Link Voice? (Sneeze 2?)
        0x47. Link Voice? (Stretch 1?)
        0x48. Link Voice (Stretch 2)
        0x49. Link Voice (Stretch 3)
        0x4A. Link Voice (Stretch 4)
        0x4B. Link Voice (Stretch 5)
        0x4C. Link Voice (Stretch 6)
        0x4D. Link Voice (Damage 7?)
        0x4E. Unknown Sound [2]
        0x4F. Unknown Sound [3]
        0x50. Unknown Sound [3]
        0x51. Unknown Sound [3]
        0x52. Unknown Sound [3]
        0x53. Unknown Sound [3]
        0x54. Unknown Sound [3]
        0x55. Unknown Sound [3]
        0x56. Unknown Sound [3]
        0x57. Unknown Sound [3]
        0x58. Unknown Sound [3]
        0x59. ⛔ (nullptr)
        0x5A. ⛔ (nullptr)
        0x5B. ⛔ (nullptr)
        0x5C. ⛔ (nullptr)
        0x5D. Gorman Bros. ("Uwahh!")
        0x5E. Sword School Instructor ("Kaaah!")
        0x5F. Gorman Bros.? (???)
        0x60. Gorman Bros. ("Ha!")
        0x61. Great Fairy (Laugh 1)
        0x62. Great Fairy (Laugh 2)
        0x63. Ikana Castle Stalfos (Laugh)
        0x64. Ikana Castle Stalfos (Damage)
        0x65. Igos Du Ikana (Gasp)
        0x66. Ikana Castle Stalfos ("Rawr")
        0x67. Ikana Castle Stalfos ("Rawr") [Same sample as 66]
        0x68. ⛔ (nullptr)
        0x69. ⛔ (nullptr)
        0x6A. ⛔ (nullptr)
        0x6B. ⛔ (nullptr)
        0x6C. ⛔ (nullptr)
        0x6D. ⛔ (nullptr)
        0x6E. ⛔ (nullptr)
        0x6F. ⛔ (nullptr)
        0x70. ⛔ (nullptr)
        0x71. ⛔ (nullptr)
        0x72. ⛔ (nullptr)
        0x73. ⛔ (nullptr)
        0x74. ⛔ (nullptr)
        0x75. ⛔ (nullptr)
        0x76. ⛔ (nullptr)
        0x77. ⛔ (nullptr)
        0x78. ⛔ (nullptr)
        0x79. ⛔ (nullptr)
        0x7A. ⛔ (nullptr)
        0x7B. ⛔ (nullptr)
        0x7C. ⛔ (nullptr)
        0x7D. ⛔ (nullptr)
        0x7E. ⛔ (nullptr)
        0x7F. ⛔ (nullptr)
        0x80. ⛔ (nullptr)
        0x81. Great Fairy (Giggle 1)
        0x82. Great Fairy (Giggle 2)
        0x83. ⛔ (nullptr)
        0x84. ⛔ (nullptr)
        0x85. Unknown Laugh
        0x86. Unknown Laugh [Same sample as 85]
        0x87. Unknown Laugh [Same sample as 85]
        0x88. Unknown Laugh [Same sample as 85]
        0x89. Goron Voice? ("Awww...")
        0x8A. Deku Link Voice (Gasp)
        0x8B. Link Voice? ("Ha!" 2)
        0x8C. Link Voice? ("Ha!" 3)
        0x8D. Traveling Goron Voice? (Exhale 1)
        0x8E. Traveling Goron Voice? (Exhale 2)
        0x8F. Traveling Goron Voice? (Exhale 3)
        0x90. Traveling Goron Voice? (Exhale 4)
        0x91. ⛔ (nullptr)
        0x92. ⛔ (nullptr)
        0x93. ⛔ (nullptr)
        0x94. ⛔ (nullptr)
        0x95. ⛔ (nullptr)
        0x96. ⛔ (nullptr)
        0x97. ⛔ (nullptr)
        0x98. ⛔ (nullptr)
        0x99. ⛔ (nullptr)
        0x9A. ⛔ (nullptr)
        0x9B. ⛔ (nullptr)
        0x9C. ⛔ (nullptr)
        0x9D. ⛔ (nullptr)
        0x9E. ⛔ (nullptr)
        0x9F. ⛔ (nullptr)
        0xA0. ⛔ (nullptr)
        0xA1. ⛔ (nullptr)
        0xA2. ⛔ (nullptr)
        0xA3. ⛔ (nullptr)
        0xA4. ⛔ (nullptr)
        0xA5. ⛔ (nullptr)
        0xA6. ⛔ (nullptr)
        0xA7. ⛔ (nullptr)
        0xA8. ⛔ (nullptr)
        0xA9. ⛔ (nullptr)
        0xAA. ⛔ (nullptr)
        0xAB. ⛔ (nullptr)
        0xAC. ⛔ (nullptr)
        0xAD. ⛔ (nullptr)
        0xAE. ⛔ (nullptr)
        0xAF. ⛔ (nullptr)
        0xB0. ⛔ (nullptr)
        0xB1. ⛔ (nullptr)
        0xB2. ⛔ (nullptr)
        0xB3. ⛔ (nullptr)
        0xB4. ⛔ (nullptr)
        0xB5. ⛔ (nullptr)
        0xB6. ⛔ (nullptr)
        0xB7. ⛔ (nullptr)
        0xB8. ⛔ (nullptr)
        0xB9. ⛔ (nullptr)
        0xBA. ⛔ (nullptr)
        0xBB. ⛔ (nullptr)
        0xBC. ⛔ (nullptr)
        0xBD. ⛔ (nullptr)
        0xBE. ⛔ (nullptr)
        0xBF. ⛔ (nullptr)
        0xC0. ⛔ (nullptr)
        0xC1. Link Voice ("Hup" 1) [Same sample as 1C]
        0xC2. Link Voice ("Ha!" 1) [Same sample as 1D]
        0xC3. Link Voice ("Hup" 2) [Same sample as 1E]
        0xC4. Link Voice ("Hup" 3) [Same sample as 1F]
        0xC5. Link Voice ("Hyah!") [Same sample as 20]
        ```

        ## Drums (Program Number: 7F)
        Below is a list of the "drums" inside of audiobank `0x00`. Unlike instrument index pointers, percussion index pointers represent a MIDI note instead of a program number.

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        **Drum List:**
        ```
        0x00. Tambourine
        0x01. Sand Footstep SFX
        0x02. Garbage Data
        0x03. Garbage Data
        0x04. Link Voice? (Ledge Related)
        0x05. Link Voice (Fall Start)
        0x06. Link Voice (Fall Scream)
        0x07. Goron Link Voice (Damage?)
        0x08. Garbage Data
        0x09. Kaching SFX (Clock Town Mailbox)
        0x0A. Clap SFX [1]
        0x0B. Clap SFX [2]
        0x0C. Clap SFX [3]
        0x0D. Clap SFX [4]
        0x0E. Clap SFX [5]
        0x0F. Clap SFX [6]
        ```

    ??? audiobank "Audiobank 0x01 (Actor Sounds)"

        Audiobank `0x01` is the second of the two main SFX audiobanks. It's mostly guesswork for what most of the sound effects are as mapping them out is done completely by listening to the samples themselves in `N64 Soundlist Tool` (for which many samples are pitched up or down in-game, so the pitches are "off" when being played back) and figuring out what sound is used where in the game.

        Sequences that use this audiobank are listed below:
        
        * `0x00: Master Sequence`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 126`
        * `NUM_DRUM: 1`
        * `NUM_SFX: 88`
        * `ATnum: 0`

        ## Instruments (Program Number: 0x00 to 0x7D)
        Below is a list of the "instruments" inside of audiobank `0x01`. These work exactly as regular instruments do, you can even import them into a custom audiobank as an instrument and use it in a sequence just like any regular instrument; and this is a common structure for the sound effects within the game.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x7D (125)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Some sound effects using the instrument structure have multiple samples, the sound effects using multiple samples indicate which region contains which sound effect sample (e.g. `0x00: Low: SFX name, Mid: SFX Name, High: SFX Name`). Any sound effects without multiple regions use the mid (primary) sample.

        **Instrument List:**
        ```
        0x00. Balloon Inflating SFX 1
        0x01. Wallmaster Rising SFX
        0x02. Balloon Inflating SFX 2
        0x03. Mid: Buzz SFX, High: Deku Baba Attack SFX
        0x04. Mid: Metal Clink SFX, High: White Noise SFX
        0x05. Hookshot Related SFX? (Unsure)
        0x06. Long Explosion SFX
        0x07. Mid: Real Bombchu Pur SFX, High: Real Bombchu Passive SFX
        0x08. Pop/Thud SFX
        0x09. Dodongo Roar SFX
        0x0A. Doom Monster Roar SFX
        0x0B. Skulltula Skitter SFX
        0x0C. Spider Egg Hatch SFX
        0x0D. Rock Explosion SFX
        0x0E. Buzz SFX (Frog Croak?)
        0x0F. Clicking SFX (Keese Attack?)
        0x10. Wing Flap SFX
        0x11. Volvagia Pained Roar SFX
        0x12. Scratch/Electric SFX (Skulltula Related?)
        0x13. "Ah" SFX (Frog Croak?)
        0x14. Dinolfos Laughing SFX (SM64 Boo)
        0x15. Low: Dinolfos SFX, High: Dinolfos Footstep SFX
        0x16. Deku Scrub Voice SFX
        0x17. Glass Break SFX (Ice?)
        0x18. Gulp SFX 1
        0x19. Deku Baba Beak Snap SFX
        0x1A. Wind SFX
        0x1B. Crow/Eagle/Bat SFX
        0x1C. Igos Du Ikana Sword Swing SFX
        0x1D. Stalchild Laughing SFX
        0x1E. Stalfos Laughing SFX
        0x1F. Garo Appearing SFX
        0x20. Thunder SFX (Deku Baba Death?)
        0x21. Electric SFX (OOT Ganon Summoning Orb)
        0x22. Whoosh SFX
        0x23. Armos Awakening SFX
        0x24. Splash SFX (Link/Octorok/etc)
        0x25. Splish SFX (Footsteps on Watery Surfaces)
        0x26. Boulder Explosion SFX
        0x27. Mid: Pamela's Father SFX, High: Goron Falling Asleep SFX
        0x28. Poe/Garo Laugh SFX (SM64 Boo Sample)
        0x29. Bubbling SFX (Gyorg Cutscene)
        0x2A. Poe Defeat Shriek SFX
        0x2B. Mid: Goron "Hmm?" SFX, High: Goron "Ooooh..." SFX
        0x2C. Mid: Wolfos Howl SFX, High: Crow Caw SFX
        0x2D. Phantom Ganon "Ha!" SFX
        0x2E. ⛔ (nullptr)
        0x2F. Deku Scrub SFX
        0x30. Wizzrobe Defeat SFX
        0x31. Thud/Impact SFX
        0x32. Thud SFX
        0x33. Unknown Growl SFX
        0x34. Synth SFX
        0x35. Explosion SFX
        0x36. Moon Speaking/Moving SFX
        0x37. Twinmold Damage SFX
        0x38. Laughing SFX 1 (SM64 Boo Sample)
        0x39. Real Bombchu SFX
        0x3A. Bomb Fuse SFX
        0x3B. Odolwa Calling Bugs SFX
        0x3C. Odolwa Passive Taunt SFX
        0x3D. Odolwa Calling Moths SFX
        0x3E. Laughing SFX 2 (SM64 Boo Sample)
        0x3F. Majora's Incarnation Head SFX
        0x40. Gomess Shout SFX
        0x41. SM64 Bowser Defeat SFX
        0x42. Laughing SFX 3 (SM64 Boo Sample)
        0x43. Hiploop Charge Footstep SFX
        0x44. Wizzrobe Initiating Attack SFX
        0x45. Wizzrobe Afterimage SFX
        0x46. Thunder SFX
        0x47. Pop/Slap SFX
        0x48. White Noise SFX (Water Noise)
        0x49. Synth SFX (Death Armos?)
        0x4A. Garo Warp Attack SFX
        0x4B. Garo Warp Away SFX
        0x4C. Rumble SFX
        0x4D. Sword Unsheathe SFX
        0x4E. Nejiron Grunt SFX
        0x4F. Chuchu Jumping SFX
        0x50. Chuchu Landing SFX
        0x51. Chuchu Jiggle SFX
        0x52. Mid: Goron Snore Inhale SFX, High: Goron Snore Exhale SFX
        0x53. Mad Jelly SFX
        0x54. Wizzrobe Casts Spell SFX
        0x55. Wizzrobe Damage SFX
        0x56. Witch Shriek SFX
        0x57. Crunchy Footstep SFX
        0x58. Witch "Hmm" SFX
        0x59. Gulp SFX 2
        0x5A. Majora's Incarnation Voice SFX
        0x5B. Wizzrobe Laughing SFX
        0x5C. Snapper Idle SFX
        0x5D. Snapper Overturned SFX
        0x5E. Unknown Chip SFX
        0x5F. Unknown Chip SFX
        0x60. Whoosh SFX
        0x61. Deku Bubble Pop/Jim Peashooter SFX
        0x62. Poe Hovering SFX (Unsure)
        0x63. Bombchu Growl SFX
        0x64. Majora's Wrath Spinners SFX (Unsure)
        0x65. Majora's Incarnation Clucking SFX 1
        0x66. Majora's Incarnation Clucking SFX 2
        0x67. Bird Chirp SFX
        0x68. Bird Chitter SFX
        0x69. Bird Trill SFX
        0x6A. Bio Deku Baba Screech SFX
        0x6B. Blue Warp Pad SFX
        0x6C. Orchestral Timpani
        0x6D. Majora's Wrath Whip SFX 1
        0x6E. Majora's Wrath Whip SFX 2
        0x6F. Majora's Wrath Whip SFX 3
        0x70. Boss Remains Awaken SFX
        0x71. Majora's Wrath Whip SFX 4
        0x72. Majora's Wrath Whip SFX 5
        0x73. Goron Elder's Son Crying SFX
        0x74. Beamos Laser SFX (Unsure)
        0x75. Static/Glass Break Noise SFX (Unsure)
        0x76. Drum SFX? (Unsure)
        0x77. Eeno SFX
        0x78. Adult Link Falling SFX
        0x79. Gekko Calling Snapper SFX
        0x7A. Gekko Damage SFX
        0x7B. Gekko Climing Walls SFX
        0x7C. Ice Shattering SFX
        0x7D. Fairy Flying SFX
        ```

        ## Sound Effects (Program Number: 7E)
        Below is a list of the "sound effects" inside of audiobank `0x01`. These work nearly identical to how percussion sets work except for how they are structured, they cannot be imported into audiobanks because their structure is built directly into a pointer array within `<absfxlist>`.

        You can access these sound effects when using this audiobank using MIDI program number(s): `0x7E (126)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`  
        !!! info "Data Structure"
            Sound effects can only have one sample per sound effect, but some sound effect indexes point to the same sample in the audiobank. The indexes that use the same sample as another index are marked: `[Same sample as (index value)]`

        **Sound Effect List:**
        ```
        0x00. Link Voice? (Damage Voice?)
        0x01. Link Voice? (Damage Scream?)
        0x02. Link Voice? (Attack Voice 1?)
        0x03. Link Voice? (Attack Voice 2?)
        0x04. Link Voice? (Attack Voice 3?)
        0x05. Redead Shriek?
        0x06. Deku Baba Damage
        0x07. Unknown Gasp
        0x08. Unknown Scream
        0x09. Unknown "Ha" Sound
        0x0A. Unknown "Yah!" Sound
        0x0B. Witch Shriek?
        0x0C. Link Voice? (Breath Sound 1)
        0x0D. Link Voice? (Breath Sound 2)
        0x0E. Goron Voice ("Aww...")
        0x0F. Unknown Synth Sound
        0x10. Unknown Monster Sound?
        0x11. Baby Goron Voice (Cry 1)
        0x12. Baby Goron Voice (Hiccup)
        0x13. Baby Goron Voice (Cry 2?)
        0x14. Unknown "Hmph" Sound
        0x15. Unknown "Eheh" Sound
        0x16. Unknown Laugh Sound 1
        0x17. Unknown Laugh Sound 2
        0x18. Unknown "Ahah" Sound
        0x19. Unknown Laugh Sound 3
        0x1A. Unknown "Rawr" Sound
        0x1B. Unknown Honk Sound
        0x1C. Unknown Laugh Sound 4
        0x1D. Unknown Sound 1
        0x1E. Unknown Damage Sound 1
        0x1F. Unknown Damage Sound 2
        0x20. Unknown Yell Sound
        0x21. Unknown Damage Sound 3
        0x22. Unknown Attack Sound
        0x23. Unknown "AHHH" Sound
        0x24. Majora's Wrath Attack Sound 1
        0x25. Majora's Wrath Attack Sound 2
        0x26. Majora's Wrath Attack Sound 3
        0x27. Majora's Wrath Shriek Sound 1
        0x28. Majora's Wrath Laugh Sound
        0x29. Majora's Wrath Attack Sound 4
        0x2A. Majora's Wrath Shriek Sound 2
        0x2B. Majora's Wrath Death Scream Sound
        0x2C. Majora's Incarnation Humming Sound
        0x2D. Majora's Incarnation Intro Sound 1?
        0x2E. Majora's Incarnation Intro Sound 2?
        0x2F. Majora's Incarnation Intro Sound 3?
        0x30. Unknown Majora's Incarnation Sound
        0x31. Majora's Incarnation Shriek Sound
        0x32. Majora's Incarnation Death Scream Sound
        0x33. Unknown Laugh Sound 5
        0x34. Skull Kid Laugh Sound 1?
        0x35. Unknown Skull Kid Sound [1]
        0x36. Skull Kid Gasp Sound
        0x37. Skull Kid "Ha" Sound
        0x38. Skull Kid Laugh Sound 2
        0x39. Skull Kid Laugh Sound 3
        0x3A. Skull Kid Laugh Sound 4
        0x3B. Skull Kid "Hmph" Sound
        0x3C. Unknown Skull Kid Sound [2]
        0x3D. Unknown Skull Kid Sound [3]
        0x3E. Unknown Skull Kid Sound [4]
        0x3F. Unknown Skull Kid Sound [5]
        0x40. Skull Kid Calls Moon Sound
        0x41. Skull Kid Laugh Sound 5
        0x42. Skull Kid Laugh Sound 6
        0x43. Skull Kid Laugh Sound 7
        0x44. Unknown Skull Kid Sound [6]
        0x45. Odolwa Drum Sound
        0x46. Skull Kid Laugh Sound 7
        0x47. Skull Kid Calls Moon Sound [Same sample as 40]
        0x48. Unknown Laugh Sound 4
        0x49. Unknown Sound 1 [Same sample as 1D]
        0x4A. Unknown Yell Sound [Same sample as 20]
        0x4B. Unknown "AHHH" Sound [Same sample as 23]
        0x4C. Unknown Honk Sound [Same sample as 1B]
        0x4D. Unknown Grunt Sound
        0x4E. Goron "Huh" Sound
        0x4F. Goron Voice ("Aww...") [Same sample as 0E]
        0x50. Goron "Huh" Sound [Same sample as 0x4E]
        0x51. Goron "Ahh" Sound
        0x52. Goron "Hmm" & Witch "Hmm" Sound
        0x53. Unknown Static Sound
        0x54. Unknown Sound 2
        0x55. Unknown Sound 3
        0x56. Unknown Laugh Sound 6
        0x57. Unknown Sound 4
        ```

        ## Drums (Program Number: 7F)
        Below is a list of the "drums" inside of audiobank `0x00`. There's one single drum pointer, but it's just a null pointer value with no sample being pointed to.

        **Drum List:**
        ```
        0x00. ⛔ (nullptr)
        ```

    ??? audiobank "Audiobank 0x02 (Ambient Sounds)"

        Audiobank `0x02` is used pretty much for basically every ambient sound in the game. It's mostly guesswork for what most of the sound effects are as mapping them out is done completely by listening to the samples themselves in `N64 Soundlist Tool` (for which many samples are pitched up or down in-game, so the pitches are "off" when being played back) and figuring out what sound is used where in the game.

        Sequences that use this audiobank are listed below:
        
        * `0x01: Nature Ambience`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 21`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 0`

        !!! info
            This audiobank has no drums or sound effects.

        ## Instruments (Program Name: 0x00 to 0x14)
        Below is a list of the "instruments" inside of audiobank `0x02`. These work exactly as regular instruments do, you can even import them into a custom audiobank as an instrument and use it in a sequence just like any regular instrument; and this is a common structure for the sound effects within the game.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x14 (20)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Bird Chirp SFX 1
        0x02. Bird Chitter SFX
        0x03. Bird Trill SFX
        0x04. Bird Song SFX
        0x05. Bird Chirp SFX 2
        0x06. Crow Caw SFX
        0x07. Swamp Bird SFX (Some type of honking bird)
        0x08. Peacock SFX?
        0x09. Bird Twitter SFX
        0x0A. Rooster Crow SFX
        0x0B. Owl Hoot SFX
        0x0C. Loon Call SFX (Tremolo)
        0x0D. Bird Chirp SFX 3
        0x0E. Guay Caw SFX
        0x0F. White Noise SFX (Waterfall)
        0x10. Wind SFX (Haunted Wasteland Sandstorm)
        0x11. Wind SFX 2 (Haunted Wasteland Sandstorm)
        0x12. Rain SFX
        0x13. Thunder SFX
        0x14. Thunder SFX 2
        ```

    ??? audiobank "Audiobank 0x03 (Main Orchestra)"

        Audiobank `0x03` is one of the largest regular audiobanks which makes it the best candidate to overwrite when making a custom audiobank.

        Sequences that use this audiobank are listed below:
        
        * `0x02: Termina Field`
        * `0x03: Pursuit Theme`
        * `0x08: Fanfare: Event Failure [1]`
        * `0x09: Fanfare: Event Failure [2]`
        * `0x0F: Sharp's Curse: "Melody of Darkness"`
        * `0x14: Pirates' Fortress`
        * `0x19: Fanfare: Event Success!`
        * `0x1A: Battle: Regular Enemy`
        * `0x1B: Battle: Dungeon Boss`
        * `0x1D: Termina Field Morning Theme`
        * `0x1F: Inside a House`
        * `0x21: Fanfare: Boss Defeated!`
        * `0x25: Timed Minigame`
        * `0x2B: Fanfare: Open a Treasure Chest!`
        * `0x31: Mayor Dotour's Office`
        * `0x38: Battle: Miniboss`
        * `0x3D: Fanfare: The Truth Revealed`
        * `0x75: Intro Cutscene: ~Lost in a Dark Wood~ [2]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x03`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Oboe
        0x02. Clarinet
        0x03. Bassoon
        0x04. French Horn
        0x05. Trumpet (C5)
        0x06. Trumpet (G4)
        0x07. Tuba
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. Piano
        0x0E. Harp
        0x0F. Marimba
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x03`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x04 (Woods of Mystery)"

        Sequences that use this audiobank are listed below:
        
        * `0x3E: Woods of Mystery`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x04`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Ocarina
        0x02. Bassoon
        0x03. Oboe
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. Pizz. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x04`. This percussion set is referred to as "Tambourine Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Tambourine Slap: `A1 (21)` to `B3 (47)`
        - Tambourine Tap: `C4 (48)` to `C♯4 (49)`
        - Tambourine Shake: `D4 (50)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Tambourine Slap [1]
        0x01. Tambourine Slap [2]
        0x02. Tambourine Slap [3]
        0x03. Tambourine Slap [4]
        0x04. Tambourine Slap [5]
        0x05. Tambourine Slap [6]
        0x06. Tambourine Slap [7]
        0x07. Tambourine Slap [8]
        0x08. Tambourine Slap [9]
        0x09. Tambourine Slap [10]
        0x0A. Tambourine Slap [11]
        0x0B. Tambourine Slap [12]
        0x0C. Tambourine Slap [13]
        0x0D. Tambourine Slap [14]
        0x0E. Tambourine Slap [15]
        0x0F. Tambourine Slap [16]
        0x10. Tambourine Slap [17]
        0x11. Tambourine Slap [18]
        0x12. Tambourine Slap [19]
        0x13. Tambourine Slap [20]
        0x14. Tambourine Slap [21]
        0x15. Tambourine Slap [22]
        0x16. Tambourine Slap [23]
        0x17. Tambourine Slap [24]
        0x18. Tambourine Slap [25]
        0x19. Tambourine Slap [26]
        0x1A. Tambourine Slap [27]
        0x1B. Tambourine Tap [1]
        0x1C. Tambourine Tap [2]
        0x1D. Tambourine Shake [1]
        0x1E. Tambourine Shake [2]
        0x1F. Tambourine Shake [3]
        0x20. Tambourine Shake [4]
        0x21. Tambourine Shake [5]
        0x22. Tambourine Shake [6]
        0x23. Tambourine Shake [7]
        0x24. Tambourine Shake [8]
        0x25. Tambourine Shake [9]
        0x26. Tambourine Shake [10]
        0x27. Tambourine Shake [11]
        0x28. Tambourine Shake [12]
        0x29. Tambourine Shake [13]
        0x2A. Tambourine Shake [14]
        0x2B. Tambourine Shake [15]
        0x2C. Tambourine Shake [16]
        0x2D. Tambourine Shake [17]
        0x2E. Tambourine Shake [18]
        0x2F. Tambourine Shake [19]
        0x30. Tambourine Shake [20]
        0x31. Tambourine Shake [21]
        0x32. Tambourine Shake [22]
        0x33. Tambourine Shake [23]
        0x34. Tambourine Shake [24]
        0x35. Tambourine Shake [25]
        0x36. Tambourine Shake [25*]
        0x37. Tambourine Shake [25*]
        0x38. Tambourine Shake [25*]
        0x39. Tambourine Shake [25*]
        0x3A. Tambourine Shake [25*]
        0x3B. Tambourine Shake [25*]
        0x3C. Tambourine Shake [25*]
        0x3D. Tambourine Shake [25*]
        0x3E. Tambourine Shake [25*]
        0x3F. Tambourine Shake [25*]
        ```

    ??? audiobank "Audiobank 0x05 (Music Box House & Guru-Guru)"

        Sequences that use this audiobank are listed below:
        
        * `0x0E: Old Koume's Boat Cruise`
        * `0x27: Music Box House: "Farewell to Gibdo"`
        * `0x2E: Guru-Guru's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x05`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (09)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Harmonica
        0x01. Nylon Str. Guitar
        0x02. Nylon Str. Guitar
        0x03. Ocarina
        0x04. Glockenspiel
        0x05. Bandoneon
        0x06. Bandoneon
        0x07. Tuba
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x05`. This percussion set is referred to as "Tambourine Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Tambourine Slap: `A1 (21)` to `B3 (47)`
        - Tambourine Tap: `C4 (48)` to `C♯4 (49)`
        - Tambourine Shake: `D4 (50)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Tambourine Slap [1]
        0x01. Tambourine Slap [2]
        0x02. Tambourine Slap [3]
        0x03. Tambourine Slap [4]
        0x04. Tambourine Slap [5]
        0x05. Tambourine Slap [6]
        0x06. Tambourine Slap [7]
        0x07. Tambourine Slap [8]
        0x08. Tambourine Slap [9]
        0x09. Tambourine Slap [10]
        0x0A. Tambourine Slap [11]
        0x0B. Tambourine Slap [12]
        0x0C. Tambourine Slap [13]
        0x0D. Tambourine Slap [14]
        0x0E. Tambourine Slap [15]
        0x0F. Tambourine Slap [16]
        0x10. Tambourine Slap [17]
        0x11. Tambourine Slap [18]
        0x12. Tambourine Slap [19]
        0x13. Tambourine Slap [20]
        0x14. Tambourine Slap [21]
        0x15. Tambourine Slap [22]
        0x16. Tambourine Slap [23]
        0x17. Tambourine Slap [24]
        0x18. Tambourine Slap [25]
        0x19. Tambourine Slap [26]
        0x1A. Tambourine Slap [27]
        0x1B. Tambourine Tap [1]
        0x1C. Tambourine Tap [2]
        0x1D. Tambourine Shake [1]
        0x1E. Tambourine Shake [2]
        0x1F. Tambourine Shake [3]
        0x20. Tambourine Shake [4]
        0x21. Tambourine Shake [5]
        0x22. Tambourine Shake [6]
        0x23. Tambourine Shake [7]
        0x24. Tambourine Shake [8]
        0x25. Tambourine Shake [9]
        0x26. Tambourine Shake [10]
        0x27. Tambourine Shake [11]
        0x28. Tambourine Shake [12]
        0x29. Tambourine Shake [13]
        0x2A. Tambourine Shake [14]
        0x2B. Tambourine Shake [15]
        0x2C. Tambourine Shake [16]
        0x2D. Tambourine Shake [17]
        0x2E. Tambourine Shake [18]
        0x2F. Tambourine Shake [19]
        0x30. Tambourine Shake [20]
        0x31. Tambourine Shake [21]
        0x32. Tambourine Shake [22]
        0x33. Tambourine Shake [23]
        0x34. Tambourine Shake [24]
        0x35. Tambourine Shake [25]
        0x36. Tambourine Shake [25*]
        0x37. Tambourine Shake [25*]
        0x38. Tambourine Shake [25*]
        0x39. Tambourine Shake [25*]
        0x3A. Tambourine Shake [25*]
        0x3B. Tambourine Shake [25*]
        0x3C. Tambourine Shake [25*]
        0x3D. Tambourine Shake [25*]
        0x3E. Tambourine Shake [25*]
        0x3F. Tambourine Shake [25*]
        ```

    ??? audiobank "Audiobank 0x06 (Fairy's Fountain)"

        Sequences that use this audiobank are listed below:
        
        * `0x18: File Select`
        * `0x28: Ptr to File Select`
        * `0x29: Zelda's Theme`
        * `0x52: Fanfare: Learned a Song!`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x06`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Harp
        0x01. Harp
        0x02. Harp
        0x03. Harp ALT (Mid Only)
        0x04. Strings ALT (Attack Time: 32)
        0x05. Ocarina
        0x06. Male Choir
        0x07. Male Choir
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x06`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x07 (Romani Ranch)"

        Sequences that use this audiobank are listed below:
        
        * `0x2F: Romani Ranch`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x07`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Lulu's Voice (Release: 248)
        0x01. Lulu's Voice (Release: 247)
        0x02. Sustain E. Guitar
        0x03. Sustain E. Guitar ALT (Attack Time: 32)
        0x04. Sustain E. Guitar ALT (Attack Time: 32)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. Strings
        0x0C. Strings
        0x0D. Solo Violin
        0x0E. Solo Violin
        0x0F. Carillon Bell (Release: 248, Non-looping) (Unused in sequence)
        ```

    ??? audiobank "Audiobank 0x08 (Gorman Brothers' Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x40: Horse Race`
        * `0x41: Fanfare: Horse Race Victory!`
        * `0x42: Gorman Brothers' Theme`
        * `0x72: Cremia's Carriage`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x08`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Banjo
        0x01. Banjo
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. Pizz. Double Bass
        0x06. Harmonica
        0x07. Nylon Str. Guitar
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. ⛔ (nullptr)
        0x0D. Solo Violin
        0x0E. Solo Violin
        ```

    ??? audiobank "Audiobank 0x09 (Bremen March)"

        Sequences that use this audiobank are listed below:
        
        * `0x53: Bremen March`
        * `0x55: Song of Soaring`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x09`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Harp
        0x01. Harp
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. Strings ALT (Attack Time: 32)
        0x05. Ocarina
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x09`. This percussion set is referred to as "Orchestra Kit", however, audiobank `0x09` uses a variant with 20 less "Timpani" drums making it a partial "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `E5 (64)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. ⛔ (nullptr)
        0x2C. ⛔ (nullptr)
        0x2D. ⛔ (nullptr)
        0x2E. ⛔ (nullptr)
        0x2F. ⛔ (nullptr)
        0x30. ⛔ (nullptr)
        0x31. ⛔ (nullptr)
        0x32. ⛔ (nullptr)
        0x33. ⛔ (nullptr)
        0x34. ⛔ (nullptr)
        0x35. ⛔ (nullptr)
        0x36. ⛔ (nullptr)
        0x37. ⛔ (nullptr)
        0x38. ⛔ (nullptr)
        0x39. ⛔ (nullptr)
        0x3A. ⛔ (nullptr)
        0x3B. ⛔ (nullptr)
        0x3C. ⛔ (nullptr)
        0x3D. ⛔ (nullptr)
        0x3E. ⛔ (nullptr)
        0x3F. ⛔ (nullptr)
        ```

    ??? audiobank "Audiobank 0x0A (Minigame Shop)"

        Sequences that use this audiobank are listed below:
        
        * `0x46: Minigame Shop Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x0A`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Clarinet
        0x02. Clarinet
        0x03. Bandoneon
        0x04. Glockenspiel
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x0A`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x0B (Zora Hall)"

        Sequences that use this audiobank are listed below:
        
        * `0x36: Zora Hall`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x0B`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Steel Drum
        0x01. Digi Pad 04
        0x02. Nylon Str. Guitar
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x0B`. This percussion set is referred to as "Conga & Shaker Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Conga Closed: `A1 (21)` to `F3 (41)`
        - Conga Open: `F♯3 (42)` to `C5 (60)`
        - Conga Slap: `C♯5 (61)` to `G♯6 (80)`
        - Shaker: `A6 (81)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Conga Closed [1]
        0x01. Conga Closed [2]
        0x02. Conga Closed [3]
        0x03. Conga Closed [4]
        0x04. Conga Closed [5]
        0x05. Conga Closed [6]
        0x06. Conga Closed [7]
        0x07. Conga Closed [8]
        0x08. Conga Closed [9]
        0x09. Conga Closed [10]
        0x0A. Conga Closed [11]
        0x0B. Conga Closed [12]
        0x0C. Conga Closed [13]
        0x0D. Conga Closed [14]
        0x0E. Conga Closed [15]
        0x0F. Conga Closed [16]
        0x10. Conga Closed [17]
        0x11. Conga Closed [18]
        0x12. Conga Closed [19]
        0x13. Conga Closed [20]
        0x14. Conga Closed [21]
        0x15. Conga Open [1]
        0x16. Conga Open [2]
        0x17. Conga Open [3]
        0x18. Conga Open [4]
        0x19. Conga Open [5]
        0x1A. Conga Open [6]
        0x1B. Conga Open [7]
        0x1C. Conga Open [8]
        0x1D. Conga Open [9]
        0x1E. Conga Open [10]
        0x1F. Conga Open [11]
        0x20. Conga Open [12]
        0x21. Conga Open [13]
        0x22. Conga Open [14]
        0x23. Conga Open [15]
        0x24. Conga Open [16]
        0x25. Conga Open [17]
        0x26. Conga Open [18]
        0x27. Conga Open [19]
        0x28. Conga Slap [1]
        0x29. Conga Slap [2]
        0x2A. Conga Slap [3]
        0x2B. Conga Slap [4]
        0x2C. Conga Slap [5]
        0x2D. Conga Slap [6]
        0x2E. Conga Slap [7]
        0x2F. Conga Slap [8]
        0x30. Conga Slap [9]
        0x31. Conga Slap [10]
        0x32. Conga Slap [11]
        0x33. Conga Slap [12]
        0x34. Conga Slap [13]
        0x35. Conga Slap [14]
        0x36. Conga Slap [15]
        0x37. Conga Slap [16]
        0x38. Conga Slap [17]
        0x39. Conga Slap [18]
        0x3A. Conga Slap [19]
        0x3B. Conga Slap [20]
        0x3C. Shaker [1]
        0x3D. Shaker [2]
        0x3E. Shaker [3]
        0x3F. Shaker [4]
        ```

    ??? audiobank "Audiobank 0x0C (Item Shop)"

        Sequences that use this audiobank are listed below:
        
        * `0x44: Item Shop`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 11`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0A)
        Below is a list of the instruments inside of audiobank `0x0C`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0A (10)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Nylon Str. Guitar
        0x01. Bandoneon
        0x02. Pizz. Double Bass
        0x03. Trumpet (G4)
        0x04. Trumpet (C5)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Cowbell
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x0C`. This percussion set is referred to as "Conga & Shaker Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Conga Closed: `A1 (21)` to `F3 (41)`
        - Conga Open: `F♯3 (42)` to `C5 (60)`
        - Conga Slap: `C♯5 (61)` to `G♯6 (80)`
        - Shaker: `A6 (81)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Conga Closed [1]
        0x01. Conga Closed [2]
        0x02. Conga Closed [3]
        0x03. Conga Closed [4]
        0x04. Conga Closed [5]
        0x05. Conga Closed [6]
        0x06. Conga Closed [7]
        0x07. Conga Closed [8]
        0x08. Conga Closed [9]
        0x09. Conga Closed [10]
        0x0A. Conga Closed [11]
        0x0B. Conga Closed [12]
        0x0C. Conga Closed [13]
        0x0D. Conga Closed [14]
        0x0E. Conga Closed [15]
        0x0F. Conga Closed [16]
        0x10. Conga Closed [17]
        0x11. Conga Closed [18]
        0x12. Conga Closed [19]
        0x13. Conga Closed [20]
        0x14. Conga Closed [21]
        0x15. Conga Open [1]
        0x16. Conga Open [2]
        0x17. Conga Open [3]
        0x18. Conga Open [4]
        0x19. Conga Open [5]
        0x1A. Conga Open [6]
        0x1B. Conga Open [7]
        0x1C. Conga Open [8]
        0x1D. Conga Open [9]
        0x1E. Conga Open [10]
        0x1F. Conga Open [11]
        0x20. Conga Open [12]
        0x21. Conga Open [13]
        0x22. Conga Open [14]
        0x23. Conga Open [15]
        0x24. Conga Open [16]
        0x25. Conga Open [17]
        0x26. Conga Open [18]
        0x27. Conga Open [19]
        0x28. Conga Slap [1]
        0x29. Conga Slap [2]
        0x2A. Conga Slap [3]
        0x2B. Conga Slap [4]
        0x2C. Conga Slap [5]
        0x2D. Conga Slap [6]
        0x2E. Conga Slap [7]
        0x2F. Conga Slap [8]
        0x30. Conga Slap [9]
        0x31. Conga Slap [10]
        0x32. Conga Slap [11]
        0x33. Conga Slap [12]
        0x34. Conga Slap [13]
        0x35. Conga Slap [14]
        0x36. Conga Slap [15]
        0x37. Conga Slap [16]
        0x38. Conga Slap [17]
        0x39. Conga Slap [18]
        0x3A. Conga Slap [19]
        0x3B. Conga Slap [20]
        0x3C. Shaker [1]
        0x3D. Shaker [2]
        0x3E. Shaker [3]
        0x3F. Shaker [4]
        ```

    ??? audiobank "Audiobank 0x0D (Curiosity Shop)"

        Sequences that use this audiobank are listed below:
        
        * `0x2C: Marine Research Lab & Curiosity Shop`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 5`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x04)
        Below is a list of the instruments inside of audiobank `0x0D`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x04 (4)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Djembe
        0x02. ⛔ (nullptr)
        0x03. Bent Conga
        0x04. Gong & Chimes
        ```

    ??? audiobank "Audiobank 0x0E (Koume & Kotake's Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x43: Koume & Kotake's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 12`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0B)
        Below is a list of the instruments inside of audiobank `0x0E`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0B (11)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Djembe
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. Piccolo
        0x06. ⛔ (nullptr)
        0x07. Piccolo
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x0E`. This percussion set is referred to as "Gong & Chimes Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Gong: `A1 (21)` to `F♯4 (54)`
        - Chimes: `G4 (55)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Gong [1]
        0x01. Gong [2]
        0x02. Gong [3]
        0x03. Gong [4]
        0x04. Gong [5]
        0x05. Gong [6]
        0x06. Gong [7]
        0x07. Gong [8]
        0x08. Gong [9]
        0x09. Gong [10]
        0x0A. Gong [11]
        0x0B. Gong [12]
        0x0C. Gong [13]
        0x0D. Gong [14]
        0x0E. Gong [15]
        0x0F. Gong [16]
        0x10. Gong [17]
        0x11. Gong [18]
        0x12. Gong [19]
        0x13. Gong [20]
        0x14. Gong [21]
        0x15. Gong [22]
        0x16. Gong [23]
        0x17. Gong [24]
        0x18. Gong [25]
        0x19. Gong [26]
        0x1A. Gong [27]
        0x1B. Gong [28]
        0x1C. Gong [29]
        0x1D. Gong [30]
        0x1E. Gong [31]
        0x1F. Gong [32]
        0x20. Gong [33]
        0x21. Gong [34]
        0x22. Chimes [1]
        0x23. Chimes [2]
        0x24. Chimes [3]
        0x25. Chimes [4]
        0x26. Chimes [5]
        0x27. Chimes [6]
        0x28. Chimes [7]
        0x29. Chimes [8]
        0x2A. Chimes [9]
        0x2B. Chimes [10]
        0x2C. Chimes [11]
        0x2D. Chimes [12]
        0x2E. Chimes [13]
        0x2F. Chimes [14]
        0x30. Chimes [15]
        0x31. Chimes [16]
        0x32. Chimes [17]
        0x33. Chimes [18]
        0x34. Chimes [19]
        0x35. Chimes [20]
        0x36. Chimes [21]
        0x37. Chimes [22]
        0x38. Chimes [23]
        0x39. Chimes [24]
        0x3A. Chimes [25]
        0x3B. Chimes [26]
        0x3C. Chimes [27]
        0x3D. Chimes [28]
        0x3E. Chimes [29]
        0x3F. Chimes [30]
        ```

    ??? audiobank "Audiobank 0x0F (Fanfare Orchestra)"

        Sequences that use this audiobank are listed below:
        
        * `0x20: Fanfare: Game Over!`
        * `0x22: Fanfare: Get an Item!`
        * `0x24: Fanfare: Get a Heart Container!`
        * `0x37: Fanfare: Get a Mask!`
        * `0x39: Fanfare: Get a Heart Piece!`
        * `0x77: Fanfare: Temple Appears!`
        * `0x78: Fanfare: Temple Clear! (Short) [1]`
        * `0x79: Fanfare: Temple Clear! (Long) [2]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x0F`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. ⛔ (nullptr)
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. Trumpet (C5)
        0x06. Trumpet (G4)
        0x07. Tuba
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. ⛔ (nullptr)
        0x0D. ⛔ (nullptr)
        0x0E. Harp
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x0F`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x10 (Kaepora Gaebora's Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x45: Kaepora Gaebora's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x10`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Oboe
        0x02. ⛔ (nullptr)
        0x03. Bassooon
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. ⛔ (nullptr)
        0x0E. Harp
        ```

    ??? audiobank "Audiobank 0x11 (Skull Kid's Band)"

        Sequences that use this audiobank are listed below:
        
        * `0x04: Majora's Theme`
        * `0x1E: Intro Cutscene ~Lost in a Dark Wood~ [1]`
        * `0x69: Battle: Majora's Wrath`
        * `0x6A: Battle: Majora's Incarnation`
        * `0x6B: Battle: Majora's Mask`
        * `0x7B: The Moon Enraged`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x11`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Chinese Gong
        0x01. Shehnai
        0x02. ⛔ (nullptr)
        0x03. Nylon Str. Guitar ALT
        0x04. Bandoneon
        0x05. Trumpet (C5)
        0x06. Trumpet (G4)
        0x07. Tuba
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Marimba
        0x0D. Synth Strings
        0x0E. Harp
        0x0F. Piano
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x11`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x12 (Giants' Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x2D: Giants' Theme`
        * `0x4B: Sonata of Awakening`
        * `0x4C: Goron Lullaby`
        * `0x4E: Elegy of Emptiness`
        * `0x4F: Oath to Order`
        * `0x54: Milk Bar Band: "Ballad of the Wind Fish"`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x12`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Ocarina
        0x01. Trumpet (B3)
        0x02. Steel Str. Guitar
        0x03. Rawhide Drum
        0x04. Strings
        0x05. Strings
        0x06. Pizz. Strings
        0x07. Harp
        0x08. Goron Elder Son's Voice
        0x09. ⛔ (nullptr)
        0x0A. Male Choir
        0x0B. Female Choir
        0x0C. Giants' Voice
        ```

    ??? audiobank "Audiobank 0x13 (The Indigo-Gos)"

        Sequences that use this audiobank are listed below:
        
        * `0x4D: New Wave Bossa Nova (Lulu's Voice Returns) [1]`
        * `0x58: Mikau's Cry (Song Loop) [1]`
        * `0x59: Mikau's Cry (Song Ends) [2]`
        * `0x62: Song-Writing: Jam Session with Japas`
        * `0x63: Song-Writing: Evan's Piano Solo`
        * `0x64: Song-Writing: The Indigo-Gos Rehearsal`
        * `0x67: New Wave Bossa Nova (Zora Eggs Hatch) [2]`
        * `0x68: New Wave Bossa Nova (Lulu's Voice Returns) [3]`
        * `0x6C: Band-Practice: Japas' Bass (Zelda 1 "Dungeon")`
        * `0x6D: Band-Practice: Tijo's Drum (ALttP "Cave")`
        * `0x6E: Band-Practice: Evan's Piano (Zelda 1 "Continue?")`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x13`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Fretless Bass
        0x01. Tenor Saxophone
        0x02. Muted E. Guitar
        0x03. Steel Str. Guitar
        0x04. E. Rhodes Piano
        0x05. Bent Conga
        0x06. Piano
        0x07. Steel Str. Guitar ALT (Mid/High Split: 127)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Cowbell
        0x0B. Piano ALT (Split: 29 & 44, Release: 93)
        0x0C. Piano ALT (Split: 22 & 44, Release: 93)
        0x0D. Lulu's Voice (Release: 248)
        0x0E. Lulu's Voice (Release: 247)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x13`. This percussion set is referred to as "Drum Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Drum Kit Shaker: `C♯3 (37)` to `D3 (38)`
        - Drum Kit Snare: `D♯3 (39)` to `G3 (43)`
        - Open Hi-Hat: `G♯3 (44)` to `A3 (45)`
        - Ride Cymbal: `A♯4 (46)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Drum Kit Shaker [1]
        0x11. Drum Kit Shaker [2]
        0x12. Drum Kit Snare [1]
        0x13. Drum Kit Snare [2]
        0x14. Drum Kit Snare [3]
        0x15. Drum Kit Snare [4]
        0x16. Drum Kit Snare [5]
        0x17. Open Hi-Hat [1]
        0x18. Open Hi-Hat [2]
        0x19. Ride Cymbal [1]
        0x1A. Ride Cymbal [2]
        0x1B. Ride Cymbal [3]
        0x1C. Ride Cymbal [4]
        0x1D. Ride Cymbal [5]
        0x1E. Ride Cymbal [6]
        0x1F. Ride Cymbal [7]
        0x20. Ride Cymbal [8]
        0x21. Ride Cymbal [9]
        0x22. Ride Cymbal [10]
        0x23. Ride Cymbal [11]
        0x24. Ride Cymbal [12]
        0x25. Ride Cymbal [13]
        0x26. Ride Cymbal [14]
        0x27. Ride Cymbal [15]
        0x28. Ride Cymbal [16]
        0x29. Ride Cymbal [17]
        0x2A. Ride Cymbal [18]
        0x2B. Ride Cymbal [19]
        0x2C. Ride Cymbal [20]
        0x2D. Ride Cymbal [21]
        0x2E. Ride Cymbal [22]
        0x2F. Ride Cymbal [23]
        0x30. Ride Cymbal [24]
        0x31. Ride Cymbal [25]
        0x32. Ride Cymbal [26]
        0x33. Ride Cymbal [27]
        0x34. Ride Cymbal [28]
        0x35. Ride Cymbal [29]
        0x36. Ride Cymbal [30]
        0x37. Ride Cymbal [31]
        0x38. Ride Cymbal [32]
        0x39. Ride Cymbal [33]
        0x3A. Ride Cymbal [34]
        0x3B. Ride Cymbal [35]
        0x3C. Ride Cymbal [36]
        0x3D. Ride Cymbal [37]
        0x3E. Ride Cymbal [38]
        0x3F. Ride Cymbal [39]
        ```

    ??? audiobank "Audiobank 0x14 (Woodfall Temple)"

        Sequences that use this audiobank are listed below:
        
        * `0x1C: Woodfall Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 6`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x05)
        Below is a list of the instruments inside of audiobank `0x14`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x05 (5)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Tabla
        0x01. Bongo & Slap
        0x02. Surdo
        0x03. Leaves Brush
        0x04. Awk Bird
        0x05. African Singer
        ```

    ??? audiobank "Audiobank 0x15 (Snowhead Temple)"

        Sequences that use this audiobank are listed below:
        
        * `0x13: Snowhead`
        * `0x65: Snowhead Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 13`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0C)
        Below is a list of the instruments inside of audiobank `0x15`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0C (12)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Fantasia
        0x01. ⛔ (nullptr)
        0x02. EERIE WIND
        0x03. E. Rhodes Piano ALT
        0x04. OMINOUSITY
        0x05. ⛔ (nullptr)
        0x06. Hi-Hat Noise
        0x07. E. Rhodes Piano ALT
        0x08. E. Rhodes Piano
        0x09. ⛔ (nullptr)
        0x0A. PIT HIT 1
        0x0B. Muted E. Guitar
        0x0C. Female Choir
        ```

    ??? audiobank "Audiobank 0x16 (Aliens & Great Bay Temple)"

        Sequences that use this audiobank are listed below:
        
        * `0x0D: Aliens' Theme`
        * `0x66: Great Bay Temple`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 8`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x08)
        Below is a list of the instruments inside of audiobank `0x16`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x08 (8)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. TUNNEL RAIN
        0x01. Metal Bang
        0x02. Metal Knock
        0x03. Chip SFX
        0x04. Electric Organ
        0x05. Electric Organ
        0x06. Mystic Pad
        0x07. Velocity
        ```

    ??? audiobank "Audiobank 0x17 (Astral Observatory & Final Hours)"

        Sequences that use this audiobank are listed below:
        
        * `0x05: Clock Tower`
        * `0x0B: Song of Healing`
        * `0x3A: Astral Observatory`
        * `0x57: Final Hours`
        * `0x60: Ptr to Final Hours`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 14`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0D)
        Below is a list of the instruments inside of audiobank `0x17`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0D (13)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Synth Strings
        0x01. Synth Strings ALT (Release: 235)
        0x02. ICELAND 1
        0x03. Harpsichord
        0x04. Hi-Hat Noise
        0x05. Strings
        0x06. Fantasia
        0x07. Female Choir
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. Piano
        0x0D. Piano ALT (Split: 24 & 44, Release: 186)
        ```

    ??? audiobank "Audiobank 0x18 (Swordsman's School)"

        Sequences that use this audiobank are listed below:
        
        * `0x50: Swordsman's School`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 11`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0A)
        Below is a list of the instruments inside of audiobank `0x18`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0A (10)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. ⛔ (nullptr)
        0x02. ⛔ (nullptr)
        0x03. ⛔ (nullptr)
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Kagura Suzu
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x18`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x19 (Termina Troupe)"

        Sequences that use this audiobank are listed below:
        
        * `0x06: Stone Tower Temple`
        * `0x07: Stone Tower Temple (Inverted)`
        * `0x12: Deku palace`
        * `0x15: Clock Town (Day 1)`
        * `0x16: Clock Town (Day 2)`
        * `0x17: Clock Town (Day 3)`
        * `0x23: Ptr to Clock Town (Day 2)`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x19`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. Ocarina
        0x02. Bassoon ALT (Splits: 42 & 127)
        0x03. Oboe
        0x04. Solo Violin
        0x05. Harmonica
        0x06. Piccolo
        0x07. ⛔ (nullptr)
        0x08. Steel Str. Guitar
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Female Choir
        0x0D. Male Choir
        0x0E. ELVES
        0x0F. EERIE WIND
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x19`. This percussion set is referred to as "Tambourine Percussion".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Tambourine Slap: `A1 (21)` to `B3 (47)`
        - Tambourine Tap: `C4 (48)` to `C♯4 (49)`
        - Tambourine Shake: `D4 (50)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Tambourine Slap [1]
        0x01. Tambourine Slap [2]
        0x02. Tambourine Slap [3]
        0x03. Tambourine Slap [4]
        0x04. Tambourine Slap [5]
        0x05. Tambourine Slap [6]
        0x06. Tambourine Slap [7]
        0x07. Tambourine Slap [8]
        0x08. Tambourine Slap [9]
        0x09. Tambourine Slap [10]
        0x0A. Tambourine Slap [11]
        0x0B. Tambourine Slap [12]
        0x0C. Tambourine Slap [13]
        0x0D. Tambourine Slap [14]
        0x0E. Tambourine Slap [15]
        0x0F. Tambourine Slap [16]
        0x10. Tambourine Slap [17]
        0x11. Tambourine Slap [18]
        0x12. Tambourine Slap [19]
        0x13. Tambourine Slap [20]
        0x14. Tambourine Slap [21]
        0x15. Tambourine Slap [22]
        0x16. Tambourine Slap [23]
        0x17. Tambourine Slap [24]
        0x18. Tambourine Slap [25]
        0x19. Tambourine Slap [26]
        0x1A. Tambourine Slap [27]
        0x1B. Tambourine Tap [1]
        0x1C. Tambourine Tap [2]
        0x1D. Tambourine Shake [1]
        0x1E. Tambourine Shake [2]
        0x1F. Tambourine Shake [3]
        0x20. Tambourine Shake [4]
        0x21. Tambourine Shake [5]
        0x22. Tambourine Shake [6]
        0x23. Tambourine Shake [7]
        0x24. Tambourine Shake [8]
        0x25. Tambourine Shake [9]
        0x26. Tambourine Shake [10]
        0x27. Tambourine Shake [11]
        0x28. Tambourine Shake [12]
        0x29. Tambourine Shake [13]
        0x2A. Tambourine Shake [14]
        0x2B. Tambourine Shake [15]
        0x2C. Tambourine Shake [16]
        0x2D. Tambourine Shake [17]
        0x2E. Tambourine Shake [18]
        0x2F. Tambourine Shake [19]
        0x30. Tambourine Shake [20]
        0x31. Tambourine Shake [21]
        0x32. Tambourine Shake [22]
        0x33. Tambourine Shake [23]
        0x34. Tambourine Shake [24]
        0x35. Tambourine Shake [25]
        0x36. Tambourine Shake [25*]
        0x37. Tambourine Shake [25*]
        0x38. Tambourine Shake [25*]
        0x39. Tambourine Shake [25*]
        0x3A. Tambourine Shake [25*]
        0x3B. Tambourine Shake [25*]
        0x3C. Tambourine Shake [25*]
        0x3D. Tambourine Shake [25*]
        0x3E. Tambourine Shake [25*]
        0x3F. Tambourine Shake [25*]
        ```

    ??? audiobank "Audiobank 0x1A (Cave)"

        Sequences that use this audiobank are listed below:
        
        * `0x06: Inside a Cave`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 4`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x03)
        Below is a list of the instruments inside of audiobank `0x1A`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x03 (3)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. OMINOUSITY
        0x01. PIT HIT 1
        0x02. Hi-Hat Noise ALT
        0x03. DANGER
        ```

    ??? audiobank "Audiobank 0x1B (Happy Mask Salesman)"

        Sequences that use this audiobank are listed below:
        
        * `0x0A: Happy Mask Salesman's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 10`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x09)
        Below is a list of the instruments inside of audiobank `0x1B`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x09 (9)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Kagura Suzu
        0x01. Shehnai
        0x02. Metal Knock
        0x03. Banjo
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x1B`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x1C (Southern Swamp)"

        Sequences that use this audiobank are listed below:
        
        * `0x0C: Southern Swamp`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 12`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0B)
        Below is a list of the instruments inside of audiobank `0x1C`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0B (11)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bouzouki
        0x01. ⛔ (nullptr)
        0x02. Bassoon ALT (Splits: 42 & 127)
        0x03. Oboe
        0x04. ⛔ (nullptr)
        0x05. ⛔ (nullptr)
        0x06. Piccolo
        0x07. French Horn
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        ```

    ??? audiobank "Audiobank 0x1D (Great Bay Coast)"

        Sequences that use this audiobank are listed below:
        
        * `0x10: Great Bay Coast`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 11`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0A)
        Below is a list of the instruments inside of audiobank `0x1D`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0A (10)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Sustain E. Guitar ALT (Attack Time: 32)
        0x01. ⛔ (nullptr)
        0x02. ⛔ (nullptr)
        0x03. Steel Drum
        0x04. Fretless Bass ALT (Decay Time: 511)
        0x05. Sitar
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        ```

    ??? audiobank "Audiobank 0x1E (Ikana Canyon)"

        Sequences that use this audiobank are listed below:
        
        * `0x11: Ikana Canyon`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 9`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x08)
        Below is a list of the instruments inside of audiobank `0x1E`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x08 (8)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. OMINOUSITY
        0x01. Piano
        0x02. DANGER
        0x03. Synth Strings
        0x04. Electric Organ
        0x05. Male Choir
        0x06. Piccolo
        0x07. Lulu's Voice (Release: 248)
        0x08. Lulu's Voice (Release: 247)
        ```

    ??? audiobank "Audiobank 0x1F (Rosa Sisters)"

        Sequences that use this audiobank are listed below:
        
        * `0x2A: Rosa Sisters' Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 8`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x07)
        Below is a list of the instruments inside of audiobank `0x1F`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x07 (7)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Djembe
        0x02. Shehnai
        0x03. ⛔ (nullptr)
        0x04. Kagura Suzu
        0x05. Surdo
        0x06. Bandoneon
        0x07. Sitar
        ```

    ??? audiobank "Audiobank 0x20 (Milk Bar)"

        Sequences that use this audiobank are listed below:
        
        * `0x3C: Milk Bar`
        * `0x56: Ptr to Milk Bar`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x20`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Fretless Bass
        0x01. Tenor Saxophone
        0x02. ⛔ (nullptr)
        0x03. Steel Str. Guitar
        0x04. E. Rhodes Piano
        0x05. ⛔ (nullptr)
        0x06. ⛔ (nullptr)
        0x07. ⛔ (nullptr)
        0x08. Electric Organ
        0x09. ⛔ (nullptr)
        0x0A. ⛔ (nullptr)
        0x0B. ⛔ (nullptr)
        0x0C. Harpsichord
        0x0D. ⛔ (nullptr)
        0x0E. Glockenspiel
        0x0F. Tambourine
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x20`. This percussion set is referred to as "Drum Kit ALT", the only difference between the "Drum Kit" and this percussion kit is a different bass drum sample.

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Kick Drum: `A1 (21)` to `C3 (36)`
        - Drum Kit Shaker: `C♯3 (37)` to `D3 (38)`
        - Drum Kit Snare: `D♯3 (39)` to `G3 (43)`
        - Open Hi-Hat: `G♯3 (44)` to `A3 (45)`
        - Ride Cymbal: `A♯4 (46)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Kick Drum [1]
        0x01. Kick Drum [2]
        0x02. Kick Drum [3]
        0x03. Kick Drum [4]
        0x04. Kick Drum [5]
        0x05. Kick Drum [6]
        0x06. Kick Drum [7]
        0x07. Kick Drum [8]
        0x08. Kick Drum [9]
        0x09. Kick Drum [10]
        0x0A. Kick Drum [11]
        0x0B. Kick Drum [12]
        0x0C. Kick Drum [13]
        0x0D. Kick Drum [14]
        0x0E. Kick Drum [15]
        0x0F. Kick Drum [16]
        0x10. Drum Kit Shaker [1]
        0x11. Drum Kit Shaker [2]
        0x12. Drum Kit Snare [1]
        0x13. Drum Kit Snare [2]
        0x14. Drum Kit Snare [3]
        0x15. Drum Kit Snare [4]
        0x16. Drum Kit Snare [5]
        0x17. Open Hi-Hat [1]
        0x18. Open Hi-Hat [2]
        0x19. Ride Cymbal [1]
        0x1A. Ride Cymbal [2]
        0x1B. Ride Cymbal [3]
        0x1C. Ride Cymbal [4]
        0x1D. Ride Cymbal [5]
        0x1E. Ride Cymbal [6]
        0x1F. Ride Cymbal [7]
        0x20. Ride Cymbal [8]
        0x21. Ride Cymbal [9]
        0x22. Ride Cymbal [10]
        0x23. Ride Cymbal [11]
        0x24. Ride Cymbal [12]
        0x25. Ride Cymbal [13]
        0x26. Ride Cymbal [14]
        0x27. Ride Cymbal [15]
        0x28. Ride Cymbal [16]
        0x29. Ride Cymbal [17]
        0x2A. Ride Cymbal [18]
        0x2B. Ride Cymbal [19]
        0x2C. Ride Cymbal [20]
        0x2D. Ride Cymbal [21]
        0x2E. Ride Cymbal [22]
        0x2F. Ride Cymbal [23]
        0x30. Ride Cymbal [24]
        0x31. Ride Cymbal [25]
        0x32. Ride Cymbal [26]
        0x33. Ride Cymbal [27]
        0x34. Ride Cymbal [28]
        0x35. Ride Cymbal [29]
        0x36. Ride Cymbal [30]
        0x37. Ride Cymbal [31]
        0x38. Ride Cymbal [32]
        0x39. Ride Cymbal [33]
        0x3A. Ride Cymbal [34]
        0x3B. Ride Cymbal [35]
        0x3C. Ride Cymbal [36]
        0x3D. Ride Cymbal [37]
        0x3E. Ride Cymbal [38]
        0x3F. Ride Cymbal [39]
        ```

    ??? audiobank "Audiobank 0x21 (Epic Orchestra)"

        Sequences that use this audiobank are listed below:
        
        * `0x6F: Ancient Castle of Ikana`
        * `0x70: Giants' Theme`
        * `0x7C: The Giants' Farewell`
        * `0x7D: Tatl & Tael Reunited (Generic Reunited Theme)`
        * `0x7E: The Moon Destroyed`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x21`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Oboe
        0x02. Female Choir
        0x03. Bassoon ALT (Split: 42 & 127)
        0x04. French Horn
        0x05. Trumpet (C5)
        0x06. Trumpet (G4)
        0x07. Tuba
        0x08. Glockenspiel
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. Giant Voice
        0x0E. Harp
        0x0F. Male Choir
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x21`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x22 (Kamaro's Theme)"

        Sequences that use this audiobank are listed below:
        
        * `0x71: Kamaro's Theme`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 1`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00)
        Below is a list of the instruments inside of audiobank `0x22`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        ```

    ??? audiobank "Audiobank 0x23 (Title Screen)"

        Sequences that use this audiobank are listed below:
        
        * `0x76: Title Screen`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 16`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0F)
        Below is a list of the instruments inside of audiobank `0x23`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0F (15)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Oboe
        0x02. Clarinet
        0x03. Bassoon ALT (Split: 42 & 127)
        0x04. French Horn
        0x05. Trumpet (C5)
        0x06. Trumpet (G4)
        0x07. Tuba
        0x08. ⛔ (nullptr)
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Pizz. Strings
        0x0D. Shehnai
        0x0E. Harp
        0x0F. Chinese Gong
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x23`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x24 (Ending Orchestra [1])"

        Sequences that use this audiobank are listed below:
        
        * `0x74: End Credits & Staff Roll [1]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x24`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Fretless Bass
        0x02. Tenor Saxophone
        0x03. Steel Str. Guitar
        0x04. Tambourine
        0x05. Trumpet (G4)
        0x06. Piano
        0x07. Bandoneon
        0x08. Solo Violin
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. ⛔ (nullptr)
        0x0D. Lulu's Voice (Release: 248)
        0x0E. Lulu's Voice (Release: 247)
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x24`. This percussion set is referred to as "Drum Kit ALT", the only difference between the "Drum Kit" and this percussion kit is a different bass drum sample.

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Kick Drum: `A1 (21)` to `C3 (36)`
        - Drum Kit Shaker: `C♯3 (37)` to `D3 (38)`
        - Drum Kit Snare: `D♯3 (39)` to `G3 (43)`
        - Open Hi-Hat: `G♯3 (44)` to `A3 (45)`
        - Ride Cymbal: `A♯4 (46)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Kick Drum [1]
        0x01. Kick Drum [2]
        0x02. Kick Drum [3]
        0x03. Kick Drum [4]
        0x04. Kick Drum [5]
        0x05. Kick Drum [6]
        0x06. Kick Drum [7]
        0x07. Kick Drum [8]
        0x08. Kick Drum [9]
        0x09. Kick Drum [10]
        0x0A. Kick Drum [11]
        0x0B. Kick Drum [12]
        0x0C. Kick Drum [13]
        0x0D. Kick Drum [14]
        0x0E. Kick Drum [15]
        0x0F. Kick Drum [16]
        0x10. Drum Kit Shaker [1]
        0x11. Drum Kit Shaker [2]
        0x12. Drum Kit Snare [1]
        0x13. Drum Kit Snare [2]
        0x14. Drum Kit Snare [3]
        0x15. Drum Kit Snare [4]
        0x16. Drum Kit Snare [5]
        0x17. Open Hi-Hat [1]
        0x18. Open Hi-Hat [2]
        0x19. Ride Cymbal [1]
        0x1A. Ride Cymbal [2]
        0x1B. Ride Cymbal [3]
        0x1C. Ride Cymbal [4]
        0x1D. Ride Cymbal [5]
        0x1E. Ride Cymbal [6]
        0x1F. Ride Cymbal [7]
        0x20. Ride Cymbal [8]
        0x21. Ride Cymbal [9]
        0x22. Ride Cymbal [10]
        0x23. Ride Cymbal [11]
        0x24. Ride Cymbal [12]
        0x25. Ride Cymbal [13]
        0x26. Ride Cymbal [14]
        0x27. Ride Cymbal [15]
        0x28. Ride Cymbal [16]
        0x29. Ride Cymbal [17]
        0x2A. Ride Cymbal [18]
        0x2B. Ride Cymbal [19]
        0x2C. Ride Cymbal [20]
        0x2D. Ride Cymbal [21]
        0x2E. Ride Cymbal [22]
        0x2F. Ride Cymbal [23]
        0x30. Ride Cymbal [24]
        0x31. Ride Cymbal [25]
        0x32. Ride Cymbal [26]
        0x33. Ride Cymbal [27]
        0x34. Ride Cymbal [28]
        0x35. Ride Cymbal [29]
        0x36. Ride Cymbal [30]
        0x37. Ride Cymbal [31]
        0x38. Ride Cymbal [32]
        0x39. Ride Cymbal [33]
        0x3A. Ride Cymbal [34]
        0x3B. Ride Cymbal [35]
        0x3C. Ride Cymbal [36]
        0x3D. Ride Cymbal [37]
        0x3E. Ride Cymbal [38]
        0x3F. Ride Cymbal [39]
        ```

    ??? audiobank "Audiobank 0x25 (Ending Orchestra [2])"

        Sequences that use this audiobank are listed below:
        
        * `0x7F: End Credits & Staff Roll [2]`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 15`
        * `NUM_DRUM: 64`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x0E)
        Below is a list of the instruments inside of audiobank `0x25`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x0E (14)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Piccolo
        0x01. Oboe
        0x02. French Horn
        0x03. Steel Str. Guitar
        0x04. Tambourine
        0x05. Trumpet (G4)
        0x06. Piano
        0x07. Bandoneon
        0x08. Solo Violin
        0x09. ⛔ (nullptr)
        0x0A. Strings
        0x0B. Strings
        0x0C. Female Choir
        0x0D. ⛔ (nullptr)
        0x0E. Harp
        ```

        ## Drums (Program Name: 0x7F)
        Below is a list of the drums inside of audiobank `0x25`. This percussion set is referred to as "Orchestra Kit".

        You can access these drums when using this audiobank using MIDI program number(s): `0x7F (127)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        Here is a list of note ranges for the drums:
        - Concert Bass Drum: `A1 (21)` to `C3 (36)`
        - Orchestra Snare Low: `C♯3 (37)` to `D3 (38)`
        - Orchestra Snare High: `D♯3 (39)` to `F3 (41)`
        - Crash Cymbal: `F♯3 (42)` to `F4 (53)`
        - Timpani: `F♯4 (54)` to `C7 (84)`

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Drum List:**
        ```
        0x00. Concert Bass Drum [1]
        0x01. Concert Bass Drum [2]
        0x02. Concert Bass Drum [3]
        0x03. Concert Bass Drum [4]
        0x04. Concert Bass Drum [5]
        0x05. Concert Bass Drum [6]
        0x06. Concert Bass Drum [7]
        0x07. Concert Bass Drum [8]
        0x08. Concert Bass Drum [9]
        0x09. Concert Bass Drum [10]
        0x0A. Concert Bass Drum [11]
        0x0B. Concert Bass Drum [12]
        0x0C. Concert Bass Drum [13]
        0x0D. Concert Bass Drum [14]
        0x0E. Concert Bass Drum [15]
        0x0F. Concert Bass Drum [16]
        0x10. Orchestra Snare Low [1]
        0x11. Orchestra Snare Low [2]
        0x12. Orchestra Snare High [1]
        0x13. Orchestra Snare High [2]
        0x14. Orchestra Snare High [3]
        0x15. Crash Cymbal [1]
        0x16. Crash Cymbal [2]
        0x17. Crash Cymbal [3]
        0x18. Crash Cymbal [4]
        0x19. Crash Cymbal [5]
        0x1A. Crash Cymbal [6]
        0x1B. Crash Cymbal [7]
        0x1C. Crash Cymbal [8]
        0x1D. Crash Cymbal [9]
        0x1E. Crash Cymbal [10]
        0x1F. Crash Cymbal [11]
        0x20. Crash Cymbal [12]
        0x21. Timpani [1]
        0x22. Timpani [2]
        0x23. Timpani [3]
        0x24. Timpani [4]
        0x25. Timpani [5]
        0x26. Timpani [6]
        0x27. Timpani [7]
        0x28. Timpani [8]
        0x29. Timpani [9]
        0x2A. Timpani [10]
        0x2B. Timpani [11]
        0x2C. Timpani [12]
        0x2D. Timpani [13]
        0x2E. Timpani [14]
        0x2F. Timpani [15]
        0x30. Timpani [16]
        0x31. Timpani [17]
        0x32. Timpani [18]
        0x33. Timpani [19]
        0x34. Timpani [20]
        0x35. Timpani [21]
        0x36. Timpani [22]
        0x37. Timpani [23]
        0x38. Timpani [24]
        0x39. Timpani [25]
        0x3A. Timpani [26]
        0x3B. Timpani [27]
        0x3C. Timpani [28]
        0x3D. Timpani [29]
        0x3E. Timpani [30]
        0x3F. Timpani [31]
        ```

    ??? audiobank "Audiobank 0x26 (Goron's Theme)"

        Audiobank `0x26` is a bit of a special audiobank, it uses a different audiotable than other audiobanks and the offsets reference data later in the audiotable causing the ADPCM data for their samples to be split; however, `SEQ64` will automatically update their sample location upon importing.

        Sequences that use this audiobank are listed below:
        
        * `0x26: Goron Race`
        * `0x30: Goron Village`
        * `0x3F: Fanfare: Goron Race Victory!`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 5`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 2`

        ## Instruments (Program Name: 0x00 to 0x04)
        Below is a list of the instruments inside of audiobank `0x26`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x04 (4)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Bent Conga
        0x01. Conga & Slap
        0x02. Cuica
        0x03. Bass Marimba
        0x04. Bass Marimba
        ```

    ??? audiobank "Audiobank 0x27 (Keaton's Quiz)"

        Sequences that use this audiobank are listed below:
        
        * `0x73: Keaton's Quiz`

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 8`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 1`

        ## Instruments (Program Name: 0x00 to 0x07)
        Below is a list of the instruments inside of audiobank `0x27`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x07 (7)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. ⛔ (nullptr)
        0x01. Djembe
        0x02. Shehnai
        0x03. ⛔ (nullptr)
        0x04. Kagura Suzu
        0x05. Surdo
        0x06. Bandoneon
        0x07. Sitar
        ```

    ??? audiobank "Audiobank 0x28 (Unused Bank)"

        Audiobank `0x28` only contains instruments with bad pointers and broken samples. This audiobank is not used anywhere in-game, it's most likely leftover data from the development cycle; however, since it is unused that means it can be used for *anything*. Do not import the instruments from this audiobank, they will only place garbage data.

        The number of instruments, drum, and sound effects, as well as the audiotable the audiobank uses, are listed below:
        
        * `NUM_INST: 5`
        * `NUM_DRUM: 0`
        * `NUM_SFX: 0`
        * `ATnum: 0`

        ## Instruments (Program Name: 0x00 to 0x04)
        Below is a list of the instruments inside of audiobank `0x28`.

        You can access these instruments when using this audiobank using MIDI program number(s): `0x00 (0)` to `0x04 (4)`  
        !!! info "Program Numbers"
            Some DAWs start with program number `0`, and others start with program number `1`; because of this you may need to offset your program number assignment by a value of `1`.

        The list is structured and named like so: `Pointer index in HEX: Name of SFX`

        **Instrument List:**
        ```
        0x00. Junk [1]
        0x01. Junk [2]
        0x02. Junk [3]
        0x03. Junk [4]
        0x04. Junk [5]
        ```

=== "Waveform Instruments"

    The waveform instruments are a collection of synth waves available at all times for all audiobanks. These instruments cannot be assigned via a MIDI program name as they go over the 7-Bit data value limit of `127 (0x7F)` (they are accessed using `128 (0x80)` and above), so they must be assigned inside the sequence.

    !!! warning "Instrument 0x87 and Above"
        "Waveforms" above `0x87` are not actual instruments with actual sample data like `0x80` to `0x87`, they instead use compiled assembly code and interpret it as if it were sample data. The starting address uses the audio thread and adds a random offset between `0x0000` and `0xFFF0`; this is volatile and may cause issues so it is recommended to avoid using them.

    **List of Waveforms:**
    ```
    0x80. Sawtooth Wave
    0x81. Triangle Wave
    0x82. Sine Wave
    0x83. Square Wave
    0x84. White Noise
    0x85. D_801D4790
    0x86. Pulse Wave (Duty Cycle: 12.5%)
    0x87. Pulse Wave (Duty Cycle: 25%)
    ```

-----