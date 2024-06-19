---
hide:
#icon: material/code-json
---

# Using Formmask
This page details how to use the Formmask feature added in `v1.15.0.21` of the *Majora's Mask* randomizer. Formmask is the ability to enable and disable specific sequence channels depending on Link's current form or state; this allows you to create more dynamic sequences than is normally possible in the vanilla game.

!!! warning "Non-Useable Categories"
    At the time of writing this Formmask does not currently work with fanfares or combat music, if you use formmask with them then the randomizer will just play all available channels instead, because of this it is discouraged to use formmask with any of the following categories:

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
    The filename itself uses the same naming as a sequence or audiobank file! e.g. `0x03.seq` will be `0x03.formmask`

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

=== ":material-code-json: &nbsp;Example 1"
    
    <div class="annotate">
    
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

    1. Channels 0, 1, 2, 3, 4, 5, 6, 9, 14, and 15 are enabled when Link is any form (Hylian, Deku, Goron, or Zora), and all other channels will be disabled.
    2. Channels 7, 8, and 13 are enabled when Link is swimming and all other channels will be disabled.
    3. Channels 10, 11, and 12 are enabled when Link is in combat and all other channels will be disabled.
    4. When Link is in the Epona or SpikeRolling state all currently enabled channels will stay enabled; no new channels will enabled or disabled as no channel depends on these states to be enabled.

=== ":material-code-json: &nbsp;Example 2"
    
    <div class="annotate">
    
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

    1. Channels 0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 14 and 15 are enabled when Link is any form (Hylian, Deku, Goron, or Zora), and all other channels will be disabled.
    2. Channel 11 is enabled when Link is swimming and all other channels will be disabled.
    3. When Link is in the Epona, SpikeRolling, or Combat states all currently enabled channels will stay enabled; if Link is in combat then channel 13 will be enabled alongside any other enabled channels.

The first 16 array values are for the channels of your sequence, and the 17th array value is for cumulative forms & states. Cumulative forms & states applied to channels will cause those channels to play on top of already playing channels; if a form or state is non-cumulative it will only play when Link is in that form or state.

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