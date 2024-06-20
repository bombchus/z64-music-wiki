<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

-----

# SysEx Messages

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details MIDI universal **SysEx** messages.

## About SysEx Messages
MIDI comes with two different types of messages, channel messages and system messages. Channel messages handle everything that affect channels such as note on and offs, control changes, and so on. System messages include SysEx, clock, and so on. SysEx are system exclusive messages designed to provide information about specific functions inside MIDI hardware from different manufacturers; and SysEx messages are up to the product manufacturer to define themselves. Unlike regular MIDI messages, SysEx messages are sent in a string which makes them quite a bit more complicated to use than regular MIDI messages. However, if your MIDI hardware relies on it then it is very important to learn.

This page can't contain every single SysEx in existance, but it can provide information on universal SysEx messages that are the same between all different MIDI controllers. The only SysEx message that can be identified and used by SEQ64 is the SysEx for master volume, and it will ignore all other SysEx messages, however it could be beneficial to learn about the others as well just in case.

## Universal Realtime System Exclusive Messages
Below are the universal realtime SysEx messages and information about them. Despite being "exclusive" they are in fact *not* exclusive messages, every piece of MIDI hardware will recognize and use them in the exact same way, thus them being named as "universal" SysEx messages.

### Master Volume
This is the only SysEx that SEQ64 can recognize and will add a command for when importing a `.mid` file and converting it into a sequence file. This message controls the overall volume of every MIDI channel allowing you to increase or decrease volume across the board instead of individually.

#### Message String
| Status | 2nd Byte | 3rd Byte |
| --- | --- | --- |
| `F0H` | `7FH 7FH 04H 01H llH mmH` | `F7H` |

!!! info
    The only values you want to edit are the `llH` and `mmH` values which correspond to the LSB and MSB of the command itself.

#### String Value Information
| Byte | Decription |
| --- | --- |
| `F0H` | SysEx start |
| `7FH` | ID number (Universal realtime message) |
| `7FH` | Device ID (Broadcast) |
| `04H` | Sub ID#1 (Device Control) |
| `01H` | Sub ID#2 (Master Volume) |
| `llH` | Master Volume LSB |
| `mmH` | Master Volume MSB |
| `F7H` | SysEx end |

### Master Fine Tuning
This SysEx is not recognized by SEQ64 and will not have a command written into your sequence when importing a `.mid` file and converting it into a sequence file. This message controls the overall fine tuning of of every MIDI channel allowing you to achieve a master pitch bend.

#### Message String
| Status | 2nd Byte | 3rd Byte |
| --- | --- | --- |
| `F0H` | `7FH 7FH 04H 01H llH mmH` | `F7H` |

!!! info
    The only values you want to edit are the `llH` and `mmH` values which correspond to the LSB and MSB of the command itself.

#### String Value Information
| Byte | Decription |
| --- | --- |
| `F0H` | SysEx start |
| `7FH` | ID number (Universal realtime message) |
| `7FH` | Device ID (Broadcast) |
| `04H` | Sub ID#1 (Device Control) |
| `03H` | Sub ID#2 (Master Volume) |
| `llH` | Master Fine Tuning LSB |
| `mmH` | Master Fine Tuning MSB |
| `F7H` | SysEx end |

### Master Coarse Tuning
This SysEx is not recognized by SEQ64 and will not have a command written into your sequence when importing a `.mid` file and converting it into a sequence file. This message controls the overall coarse tuning of of every MIDI channel allowing you to achieve a master pitch bend.

#### Message String
| Status | 2nd Byte | 3rd Byte |
| --- | --- | --- |
| `F0H` | `7FH 7FH 04H 01H llH mmH` | `F7H` |

!!! info
    The only values you want to edit are the `llH` and `mmH` values which correspond to the LSB and MSB of the command itself.

#### String Value Information
| Byte | Decription |
| --- | --- |
| `F0H` | SysEx start |
| `7FH` | ID number (Universal realtime message) |
| `7FH` | Device ID (Broadcast) |
| `04H` | Sub ID#1 (Device Control) |
| `03H` | Sub ID#2 (Master Volume) |
| `llH` | Master Fine Tuning LSB |
| `mmH` | Master Fine Tuning MSB |
| `F7H` | SysEx end |

<style>
  /*
## Global Parameter Control
placeholder

### Scale Tuning Adjustment
placeholder

#### Message String
| Status | 2nd Byte | 3rd Byte |
| --- | --- | --- |
| `F0H` | `7FH 7FH 04H 01H llH mmH` | `F7H` |

#### String Value Information
| Byte | Decription |
| --- | --- |
| `F0H` | SysEx start |
| `7FH` | ID number (Universal realtime message) |
| `7FH` | Device ID (Broadcast) |
| `04H` | Sub ID#1 (Device Control) |
| `03H` | Sub ID#2 (Master Volume) |
| `llH` | Master Fine Tuning LSB |
| `mmH` | Master Fine Tuning MSB |
| `F7H` | SysEx end |

### Key-based Instrument Controllers
placeholder

#### Message String
| Status | 2nd Byte | 3rd Byte |
| --- | --- | --- |
| `F0H` | `7FH 7FH 04H 01H llH mmH` | `F7H` |

#### String Value Information
| Byte | Decription |
| --- | --- |
| `F0H` | SysEx start |
| `7FH` | ID number (Universal realtime message) |
| `7FH` | Device ID (Broadcast) |
| `04H` | Sub ID#1 (Device Control) |
| `03H` | Sub ID#2 (Master Volume) |
| `llH` | Master Fine Tuning LSB |
| `mmH` | Master Fine Tuning MSB |
| `F7H` | SysEx end |
*/
</style>

-----