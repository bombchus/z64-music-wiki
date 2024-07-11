# Sample Tuning

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details how sample tuning works in great detail for instruments, drums, and sound effects in *Ocarina of Time* and *Majora's Mask* so that sample files will be properly tuned.

## Types of Tuning
In *Ocarina of Time* and *Majora's Mask* there are two different types of tuning: **channel-based tuning** and **key-based tuning**. All instruments use channel-based tuning, with all drums and sound effects using key-based tuning. The differences between these two types of tuning are explained in greater detail below.

### Channel-Based Tuning
!!! warning "Attention"
    **Only instruments use channel-based tuning**

Channel-based tuning or range-based tuning, also known to some as "relative" tuning, tunes a sample relative to the tuning float value of MIDI note 60 (C5), or "Middle C", at 32000 Hz. Because of this, the lower the tuning float value, then the higher the note speed is, and by extension, the higher the sample's perceived pitch will be. The higher the tuning float value, then the lower the note speed will be, and by extension, the lower the sample's perceived pitch will be.

To find a sample's root key with the correct note speed use the following calculation:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$1 \div Float = Note\hspace{1 mm}Speed$

As an example, if a sample has a root key of 72 (C6) at a sample rate of 32000 Hz, and it needs to play MIDI note 60 (C5), then the note needs to achieve a note speed of 2 for the sample to be tuned to the correct pitch. To do this, divide 1 by 0.5, with 0.5 being the tuning float value for 72 (C6).

!!! info
    For channel-based tuning, note speed is automatically calculated. Every instrument that uses channel-based tuning has one sample assigned to a specific note range on the virtual MIDI keyboard. The tuning float determines the sample root key's note speed relative to MIDI note 60 (C5), or "Middle C", for the entire virtual MIDI keyboard.


### Key-Based Tuning
!!! warning "Attention"
    **Only drums and sound effects use key-based tuning**

Key-based tuning, also known to some as "absolute" tuning, tunes a sample as if the sample's root key is MIDI note 60 (C5), or "Middle C", at 32000 Hz. Because of this, the lower the tuning float value, then the lower the note speed is, and by extension, the lower the sample's perceived pitch will be. The higher the tuning float value, then the higher the note speed is, and by extension, the higher the sample's perceived pitch will be.

To find a sample's root key with the correct note speed use the following calculation:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$1 \times Float = Note\hspace{1 mm}Speed$

As an example, if a sample has a root key of 72 (C6) at a sample rate of 32000 Hz, and it needs to play MIDI note 60 (C5), then the note needs to achieve a note speed of 0.5 for the sample to be tuned to the correct pitch. To do this, multiply 1 by 0.5, with 0.5 being the tuning float value used because with key-based tuning the note speed is equal to the tuning float value.

!!! info
    For key-based tuning, note speed is manually calculated per key. Every instrument that uses key-based tuning has one sample assigned to a specific key on the virtual MIDI keyboard. The tuning float value determines the sample root key's exact note speed for that specific key on the virtual MIDI keyboard.

## Tuning Calculation

$(Root\hspace{1 mm}Key-Coarse\hspace{1 mm}Tune)-(\frac{Fine\hspace{1 mm}Tune}{100})=-24\log_4(Float)+60$

$x=(Root\hspace{1 mm}Key-Coarse\hspace{1 mm}Tune)-(\frac{Fine\hspace{1 mm}Tune}{100})$

$y=x-60$

$z=y\div-24$

$Float=4^z$

$Float=2^\frac{60-(Root\hspace{1 mm}Key-Coarse\hspace{1 mm}Tune)-(\frac{Fine\hspace{1 mm}Tune}{100})}{12}$

$1\div Float = Note\hspace{1 mm}Speed$

$1\times Float = Note\hspace{1 mm}Speed$

$\frac{1}{12}$

$\frac{1}{100}$

$\frac{44100}{48000}=\frac{441}{480}=\frac{147}{160}$

$\frac{L}{M}$

$f(x)=Float\times\frac{32000}{x}$

$f(x)=Float\div\frac{32000}{x}$

### Sample Rate Correction
All games on the Nintendo 64 have what is known as a hardware playback rate or master sample rate. The hardware playback rate determines the samples per second produced by the synthesizer. *Ocarina of Time* and *Majora's Mask* have a hardware playback rate of 32000 Hz. This means that all samples in-game will be played back by the audio engine as if they have a sample rate of 32000 Hz. This will affect the tuning of samples that have a sample rate that differs from the hardware playback rate.

Shown in the images below is a visual representation of how a sample's speed will change based on its sample rate compared to the hardware playback rate. All the samples are assumed to be the exact same sound at the exact same pitch, but all have sample rates.

=== "Sample at 16000 Hz"
    ![](../assets/images/samples/waveform-16000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-16000hz-dark.png#only-dark)

    !!! info
        A sample with a sample rate of 16000 Hz, half the hardware playback rate, tuned to its root key without any sample rate correction will end up playing twice the speed it should in-game. This will cause the perceived pitch of the sample to be too high when played back in-game.

=== "Sample at 32000 Hz"
    ![](../assets/images/samples/waveform-32000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-32000hz-dark.png#only-dark)

    !!! info
        A sample with a sample rate of 32000 Hz, matching the hardware playback rate, tuned to its root key without any sample rate correction will end up playing exactly how fast it should. This will cause the perceived pitch of the sample to be unaltered when played back in-game.

=== "Sample at 64000 Hz"
    ![](../assets/images/samples/waveform-64000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-64000hz-dark.png#only-dark)

    !!! info
        A sample with a sample rate of 64000 Hz, twice the hardware playback rate, tuned to its root key without any sample rate correction will end up playing half the speed it should in-game. This will cause the perceived pitch of the sample to be too low when played back in-game.

The reason for a sample with a sample rate of 64000 Hz playing half the speed it should in-game is because it has twice the number of samples as the hardware playback rate. For a sample with a sample rate of 16000 Hz, it has the opposite effect, because the sample has half the number of samples as the hardware playback rate. With sample rate correction, the sample's note speed will increase or decrease based on its sample rate. This will allow the sample to match the hardware playback rate without the need to resample it.

-----