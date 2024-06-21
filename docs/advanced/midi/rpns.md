# Registered Parameter Numbers

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details a specific type of MIDI control change messages.

## About RPNs
MIDI control changes include an **RPN**, which stands for Registered Parameter Numbers, which are extended. You can use RPNs in tandem with *Data Entry* messages to change various parameters in your `.mid` file. When using RPNs your first RPN (MIDI control change numbers 100 and 101; these can be sent in any order) should be sent in order to select the parameter you want to edit, then you send your Data Entry (MIDI control change numbers 6 and 38) message to set the value of the parameter. When your RPN messages are received, any Data Entry messages that are sent and received after in the same MIDI channel will change the parameter of your RPN messages; in order for your RPNs not to be changed by unwanted Data Entry messages you should send RPN Null messages so that the parameters won't be changed.

### Pitch Bend Sensitivity
This parameter allows you to change the pitch bend semitone range used in the channel the RPN and Data Entry messages have been sent to; it requires both Data Entry messages. The MIDI specification does not give information on the full range, meaning that it depends on the MIDI hardware or software you are using.

!!! info
    The default MIDI pitch bend sensitivity is ±2 semitones, *Ocarina of Time* and *Majora's Mask* have three different pitch bend ranges available assigned to different sequence commands: Command "0xDE" has a cutom range, command "0xD3" has a range of ±12 semitones, and command "0xEE" has a range of ±2 semitones; by default SEQ64 assigns pitch bends to 0xD3, however with SEQ64 `v2.X.X` you are able to change the sequence commands assigned to whatever MIDI control change you want in the ABI file.

    By using RPNs you can set the range in your `.mid` file to match the default pitch bend range set by SEQ64.

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
In the example below the channel's pitch bend range is being set to ±12 semitones of range instead of the default ±2 MIDI has normally. After the range is set RPN Null commands are sent to ensure the data won't receive unwanted changes.

| Measures:Beats:Ticks | Event Kind | Value 1 | Value 2 | Value 3 |
| :-: | --- | --- | --- | --- |
| 00000:00:000 | Control Change | 101-RPN MSB | 0 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 0 | — |
| 00000:00:000 | Control Change | 6-Data Entry MSB | 12 | — |
| 00000:00:000 | Control Change | 38-Data Entry LSB | 0 | — |
| 00000:00:000 | Control Change | 101-RPN MSB | 127 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 127 | — |

### Channel Fine Tuning
This parameter allows you to change the fine tune of programs in the channel the RPN and Data Entry messages have been sent to; it requires both Data Entry messages. If the 14 bit value of the Data Entry messages is 0x2000 (MSB of 64 and LSB of 0), then the tuning is central with A440 Hz. The full range gives a ±1 semitone range of tuning as 1 semitone is equal to 100 cents, and since the distance between the center of 0x2000 and each of the limits is 8192, a single increment is: $100 / 8192 \approx 0.0122 \space cents$.

#### Message Values
| RPN MSB | RPN LSB | Data Entry MSB | Data Entry LSB |
| --- | --- | --- | --- |
| `00H` | `01H` | `mmH` | `llH` |

#### Value Information
| MIDI CC | Value | Decription |
| --- | --- | --- |
| RPN MSB | `00H` | When set to a value of 0 alongside RPN LSB sets parameter to edit to Channel Fine Tuning |
| RPN LSB | `01H` | When set to a value of 1 alongside RPN MSB sets parameter to edit to Channel Fine Tuning |
| Data Entry MSB | `mmH` | MSB of the 14 bit value |
| Data Entry LSB | `llH` | LSB of the 14 bit value |

#### Example
In the example below the channel's fine tune is being set to have an increase of 50 cents. After the fine tune is set RPN Null commands are sent to ensure the data won't receive unwanted changes.

| Measures:Beats:Ticks | Event Kind | Value 1 | Value 2 | Value 3 |
| :-: | --- | --- | --- | --- |
| 00000:00:000 | Control Change | 101-RPN MSB | 0 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 1 | — |
| 00000:00:000 | Control Change | 6-Data Entry MSB | 96 | — |
| 00000:00:000 | Control Change | 38-Data Entry LSB | 0 | — |
| 00000:00:000 | Control Change | 101-RPN MSB | 127 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 127 | — |

### Channel Coarse Tuning
This parameter allows you to change the coarse tune of programs in the channel the RPN and Data Entry messages have been sent to; this only requires the Data Entry MSB message. If the 14 bit value of the Data Entry MSB message is 0x40 (64), then the tuning is central with A440 Hz. The full range gives a ±48 semitone range of tuning.

#### Message Values
| RPN MSB | RPN LSB | Data Entry MSB | Data Entry LSB |
| --- | --- | --- | --- |
| `00H` | `02H` | `mmH` | `llH` |

#### Value Information
| MIDI CC | Value | Decription |
| --- | --- | --- |
| RPN MSB | `00H` | When set to a value of 0 alongside RPN LSB sets parameter to edit to Channel Coarse Tuning |
| RPN LSB | `02H` | When set to a value of 2 alongside RPN MSB sets parameter to edit to Channel Coarse Tuning |
| Data Entry MSB | `mmH` | Number of semitones to increase or decrease the tuning by |
| Data Entry LSB | `llH` | Ignored and treated as a value of 0 |

#### Example
In the example below the channel's coarse tune is being set to have a decrease of one octave (12 semitones). After the coarse tune is set RPN Null commands are sent to ensure the data won't receive unwanted changes.

| Measures:Beats:Ticks | Event Kind | Value 1 | Value 2 | Value 3 |
| :-: | --- | --- | --- | --- |
| 00000:00:000 | Control Change | 101-RPN MSB | 0 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 1 | — |
| 00000:00:000 | Control Change | 6-Data Entry MSB | 52 | — |
| 00000:00:000 | Control Change | 38-Data Entry LSB | 0 | — |
| 00000:00:000 | Control Change | 101-RPN MSB | 127 | — |
| 00000:00:000 | Control Change | 100-RPN LSB | 127 | — |

-----