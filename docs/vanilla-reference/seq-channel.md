# Sequencce Channel Commands

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

placeholder

### 0xF1: Reserve Notes
placeholder

### 0xF0: Unreserve Notes
placeholder

### 0xEE: Pitch Bend (±2 Semitones)
=== ":material-code-braces: &nbsp;C"
    ``` c
    f32 gBendPitchTwoSemitonesFrequencies[] = {
        0.890899f, 0.890899f, 0.89171f,  0.892521f, 0.893333f, 0.894146f,
        0.89496f,  0.895774f, 0.89659f,  0.897406f, 0.898222f, 0.89904f,
        0.899858f, 0.900677f, 0.901496f, 0.902317f, 0.903138f, 0.90396f,
        0.904783f, 0.905606f, 0.90643f,  0.907255f, 0.908081f, 0.908907f,
        0.909734f, 0.910562f, 0.911391f, 0.91222f,  0.91305f,  0.913881f,
        0.914713f, 0.915545f, 0.916379f, 0.917213f, 0.918047f, 0.918883f,
        0.919719f, 0.920556f, 0.921394f, 0.922232f, 0.923072f, 0.923912f,
        0.924752f, 0.925594f, 0.926436f, 0.927279f, 0.928123f, 0.928968f,
        0.929813f, 0.93066f,  0.931507f, 0.932354f, 0.933203f, 0.934052f,
        0.934902f, 0.935753f, 0.936604f, 0.937457f, 0.93831f,  0.939164f,
        0.940019f, 0.940874f, 0.94173f,  0.942587f, 0.943445f, 0.944304f,
        0.945163f, 0.946023f, 0.946884f, 0.947746f, 0.948608f, 0.949472f,
        0.950336f, 0.951201f, 0.952066f, 0.952933f, 0.9538f,   0.954668f,
        0.955537f, 0.956406f, 0.957277f, 0.958148f, 0.95902f,  0.959893f,
        0.960766f, 0.961641f, 0.962516f, 0.963392f, 0.964268f, 0.965146f,
        0.966024f, 0.966903f, 0.967783f, 0.968664f, 0.969546f, 0.970428f,
        0.971311f, 0.972195f, 0.97308f,  0.973965f, 0.974852f, 0.975739f,
        0.976627f, 0.977516f, 0.978405f, 0.979296f, 0.980187f, 0.981079f,
        0.981972f, 0.982865f, 0.98376f,  0.984655f, 0.985551f, 0.986448f,
        0.987346f, 0.988244f, 0.989144f, 0.990044f, 0.990945f, 0.991847f,
        0.992749f, 0.993653f, 0.994557f, 0.995462f, 0.996368f, 0.997275f,
        0.998182f, 0.999091f, 1.0f,      1.00091f,  1.001821f, 1.002733f,
        1.003645f, 1.004559f, 1.005473f, 1.006388f, 1.007304f, 1.00822f,
        1.009138f, 1.010056f, 1.010975f, 1.011896f, 1.012816f, 1.013738f,
        1.014661f, 1.015584f, 1.016508f, 1.017433f, 1.018359f, 1.019286f,
        1.020214f, 1.021142f, 1.022071f, 1.023002f, 1.023933f, 1.024864f,
        1.025797f, 1.026731f, 1.027665f, 1.0286f,   1.029536f, 1.030473f,
        1.031411f, 1.03235f,  1.033289f, 1.03423f,  1.035171f, 1.036113f,
        1.037056f, 1.038f,    1.038944f, 1.03989f,  1.040836f, 1.041783f,
        1.042731f, 1.04368f,  1.04463f,  1.045581f, 1.046532f, 1.047485f,
        1.048438f, 1.049392f, 1.050347f, 1.051303f, 1.05226f,  1.053217f,
        1.054176f, 1.055135f, 1.056095f, 1.057056f, 1.058018f, 1.058981f,
        1.059945f, 1.06091f,  1.061875f, 1.062842f, 1.063809f, 1.064777f,
        1.065746f, 1.066716f, 1.067687f, 1.068658f, 1.069631f, 1.070604f,
        1.071578f, 1.072554f, 1.07353f,  1.074507f, 1.075485f, 1.076463f,
        1.077443f, 1.078424f, 1.079405f, 1.080387f, 1.08137f,  1.082355f,
        1.08334f,  1.084325f, 1.085312f, 1.0863f,   1.087289f, 1.088278f,
        1.089268f, 1.09026f,  1.091252f, 1.092245f, 1.093239f, 1.094234f,
        1.09523f,  1.096226f, 1.097224f, 1.098223f, 1.099222f, 1.100222f,
        1.101224f, 1.102226f, 1.103229f, 1.104233f, 1.105238f, 1.106244f,
        1.10725f,  1.108258f, 1.109267f, 1.110276f, 1.111287f, 1.112298f,
        1.11331f,  1.114323f, 1.115337f, 1.116352f, 1.117368f, 1.118385f,
        1.119403f, 1.120422f, 1.121441f, 1.122462f,
    };
    ```

### 0xED: Set HiLo Gain
placeholder

### 0xEC: Reset Channel
placeholder

### 0xEB: Set Soundfont & Instrument
placeholder

### 0xEA: Stop Script
placeholder

### 0xE9: Set Note Priority
placeholder

### 0xE8: Set Channel Parameters
placeholder

### 0xE7: Load Channel Parameters
placeholder

### 0xE6: Set Codebook Offset
placeholder

### 0xE5: Set Reverb Index
placeholder

### 0xE4: Dyncall
placeholder

### 0xE3: Set Vibrato Delay
placeholder

### 0xE2: Set Vibrato Depth (Linear)
placeholder

### 0xE1: Set Vibrato Rate (Linear)
placeholder

### 0xE0: Set Volume Scale (Expression)
placeholder

### 0xDF: Set Volume
placeholder

### 0xDE: Set Freqscale
placeholder

### 0xDD: Set Pan
placeholder

### 0xDC: Set Pan Mix
Sets the proportion of panning that comes from the channel for key-based instruments.

- A value of 0x00 (0) will use only the key-based instrument pan values.
- A Value of 0x80 (128) will use only the channel pan value.

### 0xDB: Set Transposition (Channel)
placeholder

### 0xDA: Set Envelope
placeholder

address start value must be aligned to even numbers

### 0xD9: Set Decay Index
placeholder

### 0xD8: Set Vibrato Depth
placeholder

### 0xD7: Set Vibrato Rate
placeholder

### 0xD4: Set Reverb
placeholder

### 0xD3: Pitch Bend (±12 Semitones)
=== ":material-code-braces: &nbsp;C"
    ``` c
    f32 gBendPitchOneOctaveFrequencies[] = {
        0.5f,      0.5f,      0.502736f, 0.505488f, 0.508254f, 0.511036f,
        0.513833f, 0.516645f, 0.519472f, 0.522315f, 0.525174f, 0.528048f,
        0.530938f, 0.533843f, 0.536765f, 0.539702f, 0.542656f, 0.545626f,
        0.548612f, 0.551614f, 0.554633f, 0.557669f, 0.560721f, 0.563789f,
        0.566875f, 0.569977f, 0.573097f, 0.576233f, 0.579387f, 0.582558f,
        0.585746f, 0.588951f, 0.592175f, 0.595415f, 0.598674f, 0.60195f,
        0.605245f, 0.608557f, 0.611888f, 0.615236f, 0.618603f, 0.621989f,
        0.625393f, 0.628815f, 0.632257f, 0.635717f, 0.639196f, 0.642694f,
        0.646212f, 0.649748f, 0.653304f, 0.65688f,  0.660475f, 0.664089f,
        0.667724f, 0.671378f, 0.675052f, 0.678747f, 0.682461f, 0.686196f,
        0.689952f, 0.693727f, 0.697524f, 0.701341f, 0.70518f,  0.709039f,
        0.712919f, 0.716821f, 0.720744f, 0.724689f, 0.728655f, 0.732642f,
        0.736652f, 0.740684f, 0.744737f, 0.748813f, 0.752911f, 0.757031f,
        0.761175f, 0.76534f,  0.769529f, 0.77374f,  0.777975f, 0.782232f,
        0.786513f, 0.790818f, 0.795146f, 0.799497f, 0.803873f, 0.808272f,
        0.812696f, 0.817144f, 0.821616f, 0.826112f, 0.830633f, 0.835179f,
        0.83975f,  0.844346f, 0.848966f, 0.853613f, 0.858284f, 0.862982f,
        0.867704f, 0.872453f, 0.877228f, 0.882029f, 0.886856f, 0.891709f,
        0.89659f,  0.901496f, 0.90643f,  0.911391f, 0.916379f, 0.921394f,
        0.926436f, 0.931507f, 0.936604f, 0.94173f,  0.946884f, 0.952066f,
        0.957277f, 0.962516f, 0.967783f, 0.97308f,  0.978405f, 0.98376f,
        0.989144f, 0.994557f, 1.0f,      1.005473f, 1.010975f, 1.016508f,
        1.022071f, 1.027665f, 1.033289f, 1.038944f, 1.04463f,  1.050347f,
        1.056095f, 1.061875f, 1.067687f, 1.07353f,  1.079405f, 1.085312f,
        1.091252f, 1.097224f, 1.103229f, 1.109267f, 1.115337f, 1.121441f,
        1.127579f, 1.13375f,  1.139955f, 1.146193f, 1.152466f, 1.158773f,
        1.165115f, 1.171491f, 1.177903f, 1.184349f, 1.190831f, 1.197348f,
        1.203901f, 1.210489f, 1.217114f, 1.223775f, 1.230473f, 1.237207f,
        1.243978f, 1.250786f, 1.257631f, 1.264514f, 1.271434f, 1.278392f,
        1.285389f, 1.292423f, 1.299497f, 1.306608f, 1.313759f, 1.320949f,
        1.328178f, 1.335447f, 1.342756f, 1.350104f, 1.357493f, 1.364922f,
        1.372392f, 1.379903f, 1.387455f, 1.395048f, 1.402683f, 1.41036f,
        1.418078f, 1.425839f, 1.433642f, 1.441488f, 1.449377f, 1.457309f,
        1.465285f, 1.473304f, 1.481367f, 1.489474f, 1.497626f, 1.505822f,
        1.514063f, 1.522349f, 1.530681f, 1.539058f, 1.547481f, 1.55595f,
        1.564465f, 1.573027f, 1.581636f, 1.590292f, 1.598995f, 1.607746f,
        1.616545f, 1.625392f, 1.634287f, 1.643231f, 1.652224f, 1.661266f,
        1.670358f, 1.6795f,   1.688691f, 1.697933f, 1.707225f, 1.716569f,
        1.725963f, 1.735409f, 1.744906f, 1.754456f, 1.764058f, 1.773712f,
        1.783419f, 1.793179f, 1.802993f, 1.81286f,  1.822782f, 1.832757f,
        1.842788f, 1.852873f, 1.863013f, 1.873209f, 1.883461f, 1.893768f,
        1.904132f, 1.914553f, 1.925031f, 1.935567f, 1.946159f, 1.95681f,
        1.96752f,  1.978287f, 1.989114f, 2.0f,
    };
    ```

### 0xD2: Set Sustain
placeholder

### 0xD1: Set Note Allocation Policy
placeholder

### 0xD0: Set Stereo Headset Effect
placeholder

### 0xCF: Store Pointer
placeholder

### 0xCE: Unk_22
placeholder

### 0xCD: Disable Channel
placeholder

### 0xCC: [v] = Set Value
placeholder

### 0xCB: 
placeholder

### 0xCA: Set Mute Behavior
placeholder

### 0xC9: [v] &= Set Value
placeholder

### 0xC8: [v] -= Set Value
placeholder

### 0xC7:
placeholder

### 0xC6: Set Soundfont
placeholde

### 0xC5: Dyn Set Dyntable
placholder

### 0xC4: Large Notes On
placeholder

### 0xC3: Large Notes Off
placeholder

### 0xC1: Set Instrument
placeholder

### 0xBE:
placeholder

### 0xBD: Set Sample Start
placeholder
loop start

### 0xBC: [p] += cmdArg[0]
placeholder

### 0xBB: Set Comb Filter
placeholder

### 0xBA: Set Gatetime Humanization
bugged

### 0xB9: Set Velocity Humanization
placeholder

### 0xB8: [v] = Random Value
placeholder

### 0xB7:
placeholder

### 0xB6: Read Dyntable
placeholder

### 0xB5: Read Dyntable Large
placeholder

### 0xB4: Set Dyntable Large
placeholder

### 0xB3: Load Filter
placeholder

### 0xB2: Dynread Sequence Large
placeholder

### 0xB1: Clear Filter
placeholder

### 0xB0: Set Filter
placeholder

### 0xA8: Random Range Large
placeholder

### 0xA7:
placeholder

### 0xA6:
placeholder

### 0xA5: [v] += Channel Index
placeholder

### 0xA4: Set Surround Effect Index
placeholder

### 0xA3: sfxState[p] = [v]
placeholder

### 0xA2: sfxState[cmdArg[0]] = [v]
placeholder

### 0xA1: [v] = sfxState[p]
placeholder

### 0xA0: [v] = sfxState[cmdArg[0]]
placeholder

### 0x98: Dynset Layer
placeholder

### 0x90: Free Layer
placeholder

### 0x88: Set Layer (Absolute)
placeholder

### 0x80: Test Layer Finished
placeholder

### 0x78: Set Layer (Relative)
placeholder

### 0x70: IO[c] = [v]
placeholder

### 0x60: [v] = IO[c]
placeholder

### 0x50: [v] -= IO[c]
placeholder

### 0x40: IO Read Value 2
placeholder

### 0x30: IO Write Value 2
placeholder

### 0x20: Start Channel
placeholder

### 0x10: Load Sample
placeholder

### 0x00: Channel Delay
placeholder

-----