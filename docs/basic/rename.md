
<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

### Making a META File for Ocarina of Time

### Making a Categories File for Majora's Mask
To make a categories file for an `.mmrs` file all you need to do is create a text file with the name `categories.txt` and put whatever group and individual category values you want the area your song to play in inside the file separated by a dash (e.g. `1-2-3`).

There are two different types of categories: group categories, and individual categories. Group categories contain a number of sequences a song can be assigned to, and individual categories assign a song to a specific sequence.

=== "Group Categories (Simple)"
    Below is a list of grouped sequence category values, these values give your sequence a general area to be placed into when generating a seed.

    ??? dropdown "Categories"
        | Value | Group Name |
        | :-: | :-- |
        | `0` | Fields |
        | `1` | Towns |
        | `2` | Dungeons |
        | `3` | Indoors |
        | `4` | Minigames |
        | `5` | Action Cutscenes |
        | `6` | Calm Cutscenes & Character Themes |
        | `7` | Combat & Boss Fights |
        | `8` | Item Get, Minigame Win, Soaring |
        | `9` | Game Over |
        | `10` | Area Cleared |
        | `16` | Special |

    !!! warning "Issues With Looping Fanfares"
        Categories `8`, `9`, and `10` are fanfare categories, miscategorizing a looping sequence as any of these fanfare categories can cause various issues and possibly softlock a player in various areas (e.g. Doggy Racetrack).

    !!! info "Category 16"
        Category `16` contains two cutscene sequences which will cut your sequence short if it loops, so it is recommended to put non-looping songs in this category or to just use the individual category for these <br>sequences instead.

=== "Group Categories (Detailed)"
    Below is a list of grouped sequence category values and every sequence assigned to those groups by default, these values give your sequence a general area to be placed into when generating a seed.

    ??? dropdown "Categories"
        | Value | Group Name | Sequence Name |
        | :-: | :-- | :-- |
        | `0` | Fields | `Termina Field` `Snowhead` `Great Bay Coast` `Ikana Canyon` `Southern Swamp` `Romani Ranch` `Deku Palace` `Mystery Woods` |
        | `1` | Towns | `Great Bay Coast` `Ikana Canyon` `Southern Swamp` `Clock Town (Day 1)` `Clock Town (Day 2)` `Clock Town (Day 3)` `Goron Village` `Romani Ranch` `Zora Hall` `Deku Palace` `Fairy's Fountain` `Gorman Brothers' Theme` `Mystery Woods` `Zelda's Theme` |
        | `2` | Dungeons | `Inside a Cave` `Snowhead Temple` `Great Bay Temple` `Pirates' Fortress` `Ancient Castle of Ikana` `Stone Tower Temple` `Stone Tower Temple (Inverted)` `Woodfall Temple` |
        | `3` | Indoors | `Goron Village` `Zora Hall` `Clock Tower Interior` `Guru-Guru's Theme` `Milk Bar` `Inside a House` `Item Shop` `Minigame Shop` `Marine Research Lab & Curiosity Shop` `Astral Observatory` `Music Box House: "Farewell to Gibdo"` `Cremia's Carriage` `Old Koume's Boat Cruise` `Mayor Dotour's Office` `Swordsman's School` `Sharp's Curse: "Melody of Darkness"` `Fairy's Fountain` `File Select` `Koume & Kotake's Theme` `Mystery Woods` `Zelda's Theme` `Song of Healing Theme` `Giants' Theme` |
        | `4` | Minigames | `Milk Bar` `Minigame Shop` `Music Box House: "Farewell to Gibdo"` `Goron Race` `Timed Minigame` `Cremia's Carriage` `Old Koume's Boat Cruise` `Horse Race` `Swordsman's School` `Mystery Woods` `Battle: Regular Enemy` |
        | `5` | Action Cutscenes | `Timed Minigame` `Mayor Dotour's Office` `Aliens' Theme` `Swordsman's School` `Sharp's Curse: "Melody of Darkness"` `Pursuit Theme` `Mask Reveal` `Battle: Regular Enemy` |
        | `6` | Calm Cutscenes & Character Themes | `Clock Tower Interior` `Guru-Guru's Theme` `Marine Research Lab & Curiosity Shop` `Music Box House: "Farewell to Gibdo"` `Cremia's Carriage` `Old Koume's Boat Cruise` `Mayor Dotour's Office` `Aliens' Theme` `Sharp's Curse: "Melody of Darkness"` `Majora's Theme` `Fairy's Fountain` `File Select` `Keaton's Quiz` `Koume & Kotake's Theme` `Gorman Brothers' Theme` `Mystery Woods` `Zelda's Theme` `Tatl & Tael Reunited` `Song of Healing Theme` `Giants' Theme` |
        | `7` | Combat & Boss Fights | `Pursuit Theme` `Battle: Miniboss` `Battle: Dungeon Boss` `Battle: Majora's Mask` `Battle: Majora's Incarnation` `Battle: Majora's Wrath` |
        | `8` | Item Get, Minigame Win, and Soaring | `Fanfare: Event Success!` `Fanfare: Get an Item!` `Fanfare: Get a Heart Container!` `Fanfare: Get a Mask!` `Fanfare: Get a Heart Piece!` `Fanfare: The Truth Revealed!` `Fanfare: Goron Race Victory!` `Fanfare: Horse Race Victory!` `Fanfare: Learned a Song!` `Fanfare: Song of Soaring` `Fanfare: Temple Appears!` |
        | `9` | Game Over | `Fanfare: Event Failure [1]` `Fanfare: Event Failure [2]` `Fanfare: Game Over!` `Fanfare: Boss Defeated!` `Fanfare: Song of Soaring` `Fanfare: Temple Appears!` |
        | `10` | Area Cleared | `Fanfare: Boss Defeated!` `Fanfare: Temple Clear! (Short) [1]` `Fanfare: Temple Clear! (Long) [2]` `Fanfare: The Moon Destroyed!` `Fanfare: The Giants' Farewell!` |
        | `16` | Special | `Cutscene: Giants' Theme` `Cutscene: Title Screen` |

    !!! warning "Issues With Looping Fanfares"
        Categories `8`, `9`, and `10` are fanfare categories, miscategorizing a looping sequence as any of these fanfare categories can cause various issues and possibly softlock a player in various areas (e.g. Doggy Racetrack).

    !!! info "Category 16"
        Category `16` contains two cutscene sequences which will cut your sequence short if it loops, so it is recommended to put non-looping songs in this category or to just use the individual category for these <br>sequences instead.

=== "Individual Categories"
    Below is a list of individual sequence category values, these values give your sequence a specific area to be placed into when generating a seed.

    ??? dropdown "Categories"
        | Value | Sequence Name | Value | Sequence Name
        | :----: | :---- | :----: | :---- |
        | `102` | Termina Field | `136` | Zora Hall |
        | `103` | Pursuit Theme | `137` | Fanfare: Get a Mask! |
        | `104` | Majora's Theme | `138` | Battle: Miniboss |
        | `105` | Clock Tower Interior | `139` | Fanfare: Get a Heart Piece! |
        | `106` | Stone Tower Temple | `13A` | Astral Observatory |
        | `107` | Stone Tower Temple (Inverted) | `13B` | Inside a Cave |
        | `108` | Fanfare: Event Failure [1] | `13C` | Milk Bar |
        | `109` | Fanfare: Event Failure [2] | `13D` | Fanfare: The Truth Revealed! |
        | `10B` | Song of Healing Theme | `13E` | Woods of Mystery |
        | `10C` | Southern Swamp | `13F` | Fanfare: Goron Race Victory! |
        | `10D` | Aliens' Theme | `140` | Horse Race |
        | `10E` | Old Koume's Boat Cruise | `141` | Fanfare: Horse Race Victory! |
        | `10F` | Sharp's Curse: "Melody of Darkness" | `142` | Gorman Brothers' Theme |
        | `110` | Great Bay Coast | `143` | Koume & Kotake's Theme |
        | `111` | Ikana Canyon | `144` | Item Shop |
        | `112` | Deku Palace | `145` | Kaepora Gaebora's Theme |
        | `113` | Snowhead | `146` | Minigame Shop |
        | `114` | Pirates' Fortress | `150` | Swordsman's School |
        | `115` | Clock Town (Day 1) | `152` | Fanfare: Learned a Song! |
        | `116` | Clock Town (Day 2) | `155` | Fanfare: Song of Soaring |
        | `117` | Clock Town (Day 3) | `157` | Final Hours |
        | `118` | File Select | `165` | Snowhead Temple |
        | `119` | Fanfare: Event Success! | `166` | Great Bay Temple |
        | `11A` | Battle: Regular Enemy | `169` | Battle: Majora's Wrath |
        | `11B` | Battle: Dungeon Boss | `16A` | Battle: Majora's Incarnation |
        | `11C` | Woodfall Temple | `16B` | Battle: Majora's Mask |
        | `11F` | Inside a House | `16C` | Band-Practice: Japas' Bass Guitar (Zelda 1 "Dungeon") |
        | `120` | Fanfare: Game Over! | `16D` | Band-Practice: Tijo's Drum (ALttP "Cave") |
        | `121` | Fanfare: Boss Defeated! | `16E` | Band-Practice: Evan's Piano (Zelda 1 "Continue?") |
        | `122` | Fanfare: Get an Item! | `16F` | Ancient Castle of Ikana |
        | `124` | Fanfare: Get a Heart Container! | `170` | Cutscene: Giants' Theme |
        | `125` | Timed Minigame | `171` | Kamaro's Theme |
        | `126` | Goron Race | `172` | Cremia's Carriage |
        | `127` | Music Box House: "Farewell to Gibdo" | `173` | Keaton's Quiz |
        | `128` | Fairy's Fountain | `176` | Cutscene: Title Screen |
        | `129` | Zelda's Theme | `177` | Fanfare: Temple Appears! |
        | `12A` | Rosa Sisters' Theme | `178` | Fanfare: Temple Clear! (Short) [1] |
        | `12C` | Marine Research Lab & Curiosity Shop | `179` | Fanfare: Temple Clear! (Long) [2] |
        | `12D` | Giants' Theme | `17B` | The Moon Enraged |
        | `12E` | Guru-Guru's Theme | `17C` | Fanfare: The Giants' Farewell! |
        | `12F` | Romani Ranch | `17D` | Tatl & Tael Reunited (Generic Reunion Theme) |
        | `130` | Goron Village | `17E` | Fanfare: The Moon Destroyed! |
        | `131` | Mayor Dotour's Office | — | — |

    !!! warning "Issues With Looping Fanfares"
        Categories `108`, `109`, `119`, `120`, `121`, `122`, `124`, `137`, `139`, `13D`, `13F`, `141`, `152`, `155`, `177`, `178`, `179`, `17C`, and `17E` are fanfare categories, miscategorizing a looping sequence as any of these fanfare categories can cause various issues and possibly softlock a player in various areas (e.g. Doggy Racetrack).

    !!! info "Missing Sequences"
        Sequences that are missing from this list are normally just pointers to other sequences that have no real sequence assigned to them. These sequences have been omitted from the list.

-----