---
tags:
  - Advanced
---

!!! alert "This page pertains to a feature only available in the Majora's Mask Randomizer"

# Using Formmask
This page details how to use the **Formmask** feature added in version 1.15.0.21 of the *Majora's Mask* randomizer. Formmask is the ability to enable and disable specific sequence channels depending on Link's current form or state; this allows you to create more dynamic sequences than is normally possible in the vanilla game.

A form refers to Link's different physical forms with the following being available with Formmask: Hylian, Deku, Goron, and Zora; a state refers to the different game states with the following being available with Formmask: swimming, combat, Goron spike rolling, and riding Epona.

!!! warning "Non-Useable Categories"
    At the time of writing this, Formmask does not currently work with fanfares or combat music. If you use formmask with them, then the randomizer will just play all available channels instead. Because of this, it is discouraged to use formmask with any of the following categories:

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
A `.formmask` file is just a `.json` (or `.txt`) file with its filename extension changed to `.formmask`. Inside the file is a single JSON array that contains all the necessary data for which channels to enable and disable when the conditions to do so are met. This file is packed into the root of an `.mmrs` file.

!!! info "Filename"
    The filename itself uses the same naming as a sequence or audiobank file (e.g. A sequence using audiobank 0x03 will be named `0x03.seq` with the corresponding formmask file being named `0x03.formmask`).

### JSON Array Formatting
The formatting for a JSON array is as follows:

=== ":material-code-json: &nbsp;Template"
    <div class="annotate" markdown>
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
    </div>

=== ":material-code-json: &nbsp;Example 1"
    <div class="annotate" markdown>
    ``` yaml
    [
        "All",#(1)!
        "All",
        "All",
        "All",
        "All",
        "All",
        "All",
        "Swim",#(2)!
        "Swim",
        "All",
        "Combat",#(3)!
        "Combat",
        "Combat",
        "Swim",
        "All",
        "All",
        "Epona, SpikeRolling"#(4)!
    ]
    ```
    </div>

    1. Channels 0, 1, 2, 3, 4, 5, 6, 9, 14, and 15 are enabled when Link is in any form (Hylian, Deku, Goron, or Zora), and all other channels will be disabled.
    2. Channels 7, 8, and 13 are enabled when Link is swimming and all other channels will be disabled.
    3. Channels 10, 11, and 12 are enabled when Link is in combat and all other channels will be disabled.
    4. When Link is in the Epona or SpikeRolling state, all currently enabled channels will stay enabled; no new channels will be enabled or disabled as no channel depends on these states to be enabled.

=== ":material-code-json: &nbsp;Example 2"
    <div class="annotate" markdown>
    ``` yaml
    [
        "All",#(1)!
        "All",
        "All",
        "All",
        "All",
        "All",
        "All",
        "All",
        "All",
        "All",
        "All",
        "Swim",#(2)!
        "All",
        "Combat",
        "All",
        "All",
        "Epona, SpikeRolling, Combat"#(3)!
    ]
    ```
    </div>

    1. Channels 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 14 and 15 are enabled when Link is in any form (Hylian, Deku, Goron, or Zora), and all other channels will be disabled.
    2. Channel 11 is enabled when Link is swimming and all other channels will be disabled.
    3. When Link is in the Epona, SpikeRolling, or Combat states, all currently enabled channels will stay enabled; if Link is in combat, then channel 13 will be enabled alongside any other enabled channels.

The first 16 array values are for the channels of your sequence, and the 17th array value is for *cumulative* states. Cumulative states applied to a sequence will cause the channels with cumulative states to continue playing with already playing channels; if a form or state is non-cumulative, it will only play when Link is in that form or state.

!!! info "Assigning Multiple Values"
    You can specify a channel and cumulative states to have multiple values. To do this, simply add the values you want to use separated by a comma while still being contained within quotation marks (e.g. `"state1, state2, state3"`). These comma-separated values do not need to have spaces between them.

### Allowed Form & State Values
Below is a list of the forms and states available to be assigned via Formmask.

=== "Forms"
    | Form | Description |
    | --- | --- |
    | `Human` | The assigned channel will be enabled while Link is a Hylian |
    | `Deku` | The assigned channel will be enabled whil Link is a Deku |
    | `Goron` | The assigned channel will be enabled while Link is a Goron |
    | `Zora` | The assigned channel will be enabled while Link is a Zora |
    | `All` | The assigned channel will be enabled for all of Link's different forms |

=== "States"
    | State | Description |
    | --- | --- |
    | `Swim` | The assigned channel will be enabled while Link is swimming in the water |
    | `Combat` | The assigned channel will be enabled while Link is near or fighting an enemy |
    | `Epona` | The assigned channel will be enabled while Link is riding Epona |
    | `SpikeRolling` | The assigned channel will be enabled while Goron Link is rolling with spikes |

## Testing a Formmask Sequence
To test Formmask when testing your song, you must be on the file select screen of the game and use a seed created by the randomizer. To cycle through non-cumulative states, you can use D-Pad Up and D-Pad Down, and to cycle through cumulative states you can use D-Pad Left and D-Pad Right.

!!! info "Info <small>needs confirmation</small>"
    For non-cumulative forms and states, the cycle is: Human, then Goron, then Zora, then Deku, then Swim, then Combat, then Epona, then SpikeRolling.

    For cumulative states, the cycle is: None, then Swim, then Combat, then Epona, then SpikeRolling.

-----