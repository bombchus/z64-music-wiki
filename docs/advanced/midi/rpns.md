# Registered Parameter Numbers

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details a specific type of MIDI control change messages.

## About RPNs
MIDI control changes include an **RPN**, which stands for Registered Parameter Numbers, which are extended. RPNs can be used in tandem with *Data Entry* messages to change various parameters within a `.mid` file. When using RPNs, the first RPN (MIDI control change numbers 100 and 101; these can be sent in any order) should be sent to select the parameter to edit, then Data Entry (MIDI control change numbers 6 and 38) messages should be sent to set the value of the parameter. When an RPN message is received, any Data Entry messages that are sent and received afterward in the same MIDI channel will change the parameters of an RPN message, for RPNs not to be changed by unwanted Data Entry messages. RPN Null messages should be sent so that the parameters will not be changed.

### Pitch Bend Sensitivity
This parameter allows the pitch bend semitone range used in the channel the RPN and Data Entry messages have been sent in to be changed; it requires both Data Entry messages. The MIDI specification does not give information on the full range, meaning that it depends on the MIDI hardware or software being used.

!!! info
    The default MIDI pitch bend sensitivity is ±2 semitones, *Ocarina of Time* and *Majora's Mask* have three different pitch bend ranges available and assigned using three different sequence commands: Command "0xDE" uses a custom range, command "0xD3" has a range of ±12 semitones, and command "0xEE" has a range of ±2 semitones; by default, SEQ64 assigns pitch bends to 0xD3, however, in SEQ64 versions 2.0 and above the sequence commands may be assigned to whatever MIDI control change is set in the ABI file.

    By using RPNs, the range within a `.mid` file can be set to match the default pitch bend range used by SEQ64.

#### Message Values
| RPN MSB | RPN LSB | Data Entry MSB | Data Entry LSB |
| --- | --- | --- | --- |
| `00H` | `00H` | `mmH` | `llH` |

#### Value Information
| MIDI CC | Value | Decription |
| --- | --- | --- |
| RPN MSB | `00H` | When set to a value of 0 alongside RPN LSB sets parameter to edit to Pitch Bend Sensitivity |
| RPN LSB | `00H` | When set to a value of 0 alongside RPN MSB sets parameter to edit to Pitch Bend Sensitivity |
| Data Entry MSB | `mmH` | Semitone range |
| Data Entry LSB | `llH` | Cent range |

#### Example
In the example below, the channel's pitch bend range is set to a range of ±12 semitones instead of the default MIDI range of ±2 semitones. After the range is set, RPN Null commands are sent to ensure the data will not receive unwanted changes.

| Measures:Beats:Ticks | Event Kind | Value 1 | Value 2 | Value 3 |
| :-: | --- | --- | --- | --- |
| 00000:00:000 | Control Change | 101-RPN MSB | 0 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 0 | — |
| 00000:00:000 | Control Change | 6-Data Entry MSB | 12 | — |
| 00000:00:000 | Control Change | 38-Data Entry LSB | 0 | — |
| 00000:00:000 | Control Change | 101-RPN MSB | 127 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 127 | — |

### Channel Fine-Tuning
This parameter allows the fine-tuning of programs in the channel the RPN and Data Entry messages have been sent in to be changed; it requires both Data Entry messages. If the 14 bit value of the Data Entry messages is 0x2000 (MSB of 64 and LSB of 0), then the tuning is central with A440 Hz. The full range gives a range of ±1 semitones of tuning, as 1 semitone is equal to 100 cents, and since the distance between the center of 0x2000 and each of the limits is 8192, a single increment is: $100 / 8192 \approx 0.0122 \space cents$.

#### Message Values
| RPN MSB | RPN LSB | Data Entry MSB | Data Entry LSB |
| --- | --- | --- | --- |
| `00H` | `01H` | `mmH` | `llH` |

#### Value Information
| MIDI CC | Value | Decription |
| --- | --- | --- |
| RPN MSB | `00H` | When set to a value of 0 alongside RPN LSB sets parameter to edit to Channel Fine-Tuning |
| RPN LSB | `01H` | When set to a value of 1 alongside RPN MSB sets parameter to edit to Channel Fine-Tuning |
| Data Entry MSB | `mmH` | MSB of the 14 bit value |
| Data Entry LSB | `llH` | LSB of the 14 bit value |

#### Example
In the example below, the channel's fine-tuning is being set to have an increase of 50 cents. After the fine-tuning is set, RPN Null commands are sent to ensure the data will not receive unwanted changes.

| Measures:Beats:Ticks | Event Kind | Value 1 | Value 2 | Value 3 |
| :-: | --- | --- | --- | --- |
| 00000:00:000 | Control Change | 101-RPN MSB | 0 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 1 | — |
| 00000:00:000 | Control Change | 6-Data Entry MSB | 96 | — |
| 00000:00:000 | Control Change | 38-Data Entry LSB | 0 | — |
| 00000:00:000 | Control Change | 101-RPN MSB | 127 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 127 | — |

### Channel Coarse-Tuning
This parameter allows the coarse-tuning of programs in the channel the RPN and Data Entry messages have been sent in to be changed; it only requires the Data Entry MSB message. If the 14 bit value of the Data Entry MSB message is 0x40 (64), then the tuning is central with A440 Hz. The full range gives a range of ±48 semitones of tuning.

#### Message Values
| RPN MSB | RPN LSB | Data Entry MSB | Data Entry LSB |
| --- | --- | --- | --- |
| `00H` | `02H` | `mmH` | `llH` |

#### Value Information
| MIDI CC | Value | Decription |
| --- | --- | --- |
| RPN MSB | `00H` | When set to a value of 0 alongside RPN LSB sets parameter to edit to Channel Coarse-Tuning |
| RPN LSB | `02H` | When set to a value of 2 alongside RPN MSB sets parameter to edit to Channel Coarse-Tuning |
| Data Entry MSB | `mmH` | Number of semitones to increase or decrease the tuning by |
| Data Entry LSB | `llH` | Ignored and treated as a value of 0 |

#### Example
In the example below the channel's coarse-tuning is being set to have a decrease of one octave (12 semitones). After the coarse-tuning is set, RPN Null commands are sent to ensure the data will not receive unwanted changes.

| Measures:Beats:Ticks | Event Kind | Value 1 | Value 2 | Value 3 |
| :-: | --- | --- | --- | --- |
| 00000:00:000 | Control Change | 101-RPN MSB | 0 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 1 | — |
| 00000:00:000 | Control Change | 6-Data Entry MSB | 52 | — |
| 00000:00:000 | Control Change | 38-Data Entry LSB | 0 | — |
| 00000:00:000 | Control Change | 101-RPN MSB | 127 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 127 | — |

-----