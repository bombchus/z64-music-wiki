---
icon: material/code-json
---

# Using Formmask
Added in `v1.15.0.21` of the *Majora's Mask* randomizer is the ability to enable and disable specific sequence channels depending on Link's current form or state. This feature is known as "Formmask", and it allows you to have more dynamics with your sequences.

!!! warning "Non-Useable Categories"
    At the time of writing this Formmask does not currently work with fanfares or combat music, so you cannot use it with the following sequence categories:

    === "Group Categories"
        | Category | Group Name |
        | :-: | --- |
        | `5` | Action Cutscenes |
        | `7` | Combat & Boss Fights |
        | `8` | Item Get, Minigame Win, Soaring |
        | `9` | Game Over |
        | `10` | Area Cleared |

    === "Individual Categories"
        | Category | Sequence Name | Category | Sequence Name |
        | :-: | --- | :-: | --- |
        | `108` | Fanfare: Event Failure [1] | `13F` | Fanfare: Goron Race Victory! |
        | `109` | Fanfare: Event Failure [2] | `141` | Fanfare: Horse Race Victory! |
        | `119` | Fanfare: Event Success! | `152` | Fanfare: Learned a Song! |
        | `11A` | Battle: Regular Enemy | `155` | Fanfare: Song of Soaring |
        | `11B` | Battle: Dungeon Boss | `169` | Battle: Majora's Wrath |
        | `120` | Fanfare: Game Over! | `16A` | Battle: Majora's Incarnation |
        | `121` | Fanfare: Boss Defeated! | `16B` | Battle: Majora's Mask |
        | `122` | Fanfare: Get an Item! | `177` | Fanfare: Temple Appears! |
        | `124` | Fanfare: Get a Heart Container! | `178` | Fanfare: Temple Clear (Short) [1] |
        | `137` | Fanfare: Get a Mask! | `179` | Fanfare: Temple Clear (Long) [2] |
        | `138` | Battle: Miniboss | `17C` | Fanfare: The Giants' Farewell! |
        | `139` | Fanfare: Get a Heart Piece! | `17E` | Fanfare: The Moon Destroyed |
        | `13D` | Fanfare: The Truth Revealed! | — | — |

## Creating a Formmask File
A `.formmask` file is simply a `.json` (or plain text) file with its filename extension changed to `.formmask`. Inside the file is a single `.json` array that contains all the necessary data for which channels to enable and disable when the conditions to do so are met. This file is packed into the root of an `.mmrs` file.

!!! info "Filename"
    The filename itself uses the same naming as a sequence or audiobank file! e.g. `0x03.zseq` will be `0x03.formmask`

### JSON Array Formatting
The formatting for a `.json` array is as follows:

=== ":material-code-json: &nbsp;Template"
    ``` json
    [
        "Channel 0",
        "Channel 1",
        "Channel 2",
        "Channel 3",
        "Channel 4",
        "Channel 5",
        "Channel 6",
        "Channel 7",
        "Channel 8",
        "Channel 9",
        "Channel 10",
        "Channel 11",
        "Channel 12",
        "Channel 13",
        "Channel 14",
        "Channel 15",
        "Cumulative States"
    ]
    ```

=== ":material-code-json: &nbsp;Example"
    ``` json
    [
        "Human, Deku",
        "All",
        "All",
        "Human, Deku, Goron",
        "All",
        "Zora",
        "All",
        "Human, Goron",
        "All",
        "All",
        "All",
        "Human",
        "All",
        "Zora, Swim",
        "Epona",
        "SpikeRolling",
        "Epona, SpikeRolling, Swim"
    ]
    ```

The first 16 array values are for the channels of your sequence, and the 17th array value is for cumulative forms & states. Cumulative forms & states applied to channels will cause those channels to play on top of already playing channels; if a state is non-cumulative it will disable all other channels without the set form or state when that form or state is active.

!!! info
    You can specify a channel and cumulative forms & states to have multiple values. To do this simply add the values you want to use separated by a comma while still being contained within quotation marks (e.g. `"state1, state2, state3"`).

### Allowed Form & State Values
Below is a list of the forms & states available to be assigned via Formmask.

| Form or State | Description |
| --- | --- |
| `Human` | The channel will be enabled while Link is a Hylian |
| `Deku` | The channel will be enabled whil Link is a Deku |
| `Goron` | The channel will be enabled while Link is a Goron |
| `Zora` | The channel will be enabled while Link is a Zora |
| `All` | The Channel will be enabled for all of Link's different forms |
| `Swim` | The channel will be enabled while Link is swimming in the water |
| `Combat` | The channel will be enabled while Link is near or fighting an enemy |
| `Epona` | The channel will be enabled while Link is riding Epona |
| `SpikeRolling` | The channel will be enabled while Goron Link is rolling with spikes |

## Testing a Formmask Sequence
To test Formmask when testing your song you must be on the file select screen of the game using the randomizer. To cycle through non-cumulative states you can use *D-Pad up* and *D-Pad down*, and to cycle through cumulative states you can use *D-Pad left* and *D-Pad right*.

-----