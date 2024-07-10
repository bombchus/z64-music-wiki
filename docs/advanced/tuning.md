# Sample Tuning

<div class="grid cards" markdown>

-   <img style="width:58.5px; height:auto; vertical-align: middle;" src="../../assets/images/carpenters.png"> <b>&nbsp;&nbsp;THIS PAGE IS A WIP</b>
  
    ---

    This page is a work in progress and requires further editing.

</div>

This page details how sample tuning works in great detail for instruments, drums, and sound effects in *Ocarina of Time* and *Majora's Mask* so that sample files will be properly tuned.

## Types of Tuning
In *Ocarina of Time* and *Majora's Mask* there are two different types of tuning, **Channel-Based tuning** and **Key-Based tuning**. All instruments use Channel-Based tuning, with all drums and sound effects using Key-Based tuning. The differences between these two types of tuning are explained in greater detail below.

### Channel-Based Tuning
!!! warning "Attention"
    **Only Instruments use Channel-Based tuning**

Channel-Based tuning or Range-Based tuning, also known to some as "relative" tuning, means that the sample's root key is tuned in relation to the tuning float of note 60 (C5) at 32000 Hz. This means that the lower the tuning float value the higher the note speed will be, and by extension the higher the note's perceived pitch will be; the higher the tuning float value the lower the note speed will be, and by extension the lower the note's perceived will be.

So to get our sample's root key to the correct note speed we need to use the following calculation:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$1 \div Float = Note\hspace{1 mm}Speed$

As an example if our sample has a root key of 72 (C6) with a sample rate of 32000 Hz and we want it to play 60 (C5) then we need to achieve a note speed of 2 for our sample to be tuned to the correct pitch; to do this we divide 1 by 0.5, with 0.5 being the tuning float value for 72 (C6).

!!! info
    For Channel-Based tuning, note speeds are automatically calculated, as every instrument has a sample assigned to a range of specific notes, where the tuning float determines the sample root key's note speed in relation to 60 (C5).


### Key-Based Tuning
!!! warning "Attention"
    **Only Drums and Sound Effects use Key-Based tuning**

Key-Based tuning, also known to some as "absolute" tuning, means that the sample's root key is tuned as if it is always 60 (C5) at 32000 Hz. This means that the lower the tuning float value the lower the note speed will be, and by extension the lower the note's perceived pitch will be; the hight the tuning float value the higher the note speed will be, and by extension the higher the note's perceived pitch will be.

So to get our sample's root key to the correct note speed we need to use the following calculation:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$1 \times Float = Note\hspace{1 mm}Speed$

As an example if our sample has a root key of 72 (C6) with a sample rate of 32000 Hz and we want it to play 60 (C5) then we need to achieve a note speed of 0.5 for our sample to be tuned to the correct pitch; to do this we multiply 1 by 0.5, with 0.5 being the tuning float we would use as with — tuning the note speed is equal to the tuning float value.

!!! info
    For Key-Based tuning note speeds are manually caculated per key, as every drum and sound effect has a single sample assigned to a single specific key on the MIDI keyboard, where the tuning float is equal to the note speed, as the note speed of the sample's root key is always assumed to be equal to 60 (C5)'s note speed.

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

*Ocarina of Time* and *Majora's Mask* have a master sample rate, also known as hardware rate, of 32000 Hz that affects how all samples in the game are played. The games will always play samples as is they were sampled at the master sample rate which will affect the tuning of samples.

Shown in the images below is a visual representation of how a sample's speed will be affected. All the samples are assumed to be the same sound sample recorded at the same pitch, but are resampled at varying sample rates.

=== "Sample at 16000 Hz"
    ![](../assets/images/samples/waveform-16000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-16000hz-dark.png#only-dark)

    With a sample rate of 16000 Hz, half the master sample rate, and tuned to the root key without any form of sample rate correction the sample will end up playing at twice the note speed it should play therefore causing the pitch to be too high.

=== "Sample at 32000 Hz"
    ![](../assets/images/samples/waveform-32000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-32000hz-dark.png#only-dark)

    With a sample rate of 32000 Hz, matching the master sample rate, and tuned to the root key without any form of sample rate correction the sample will end up playing at the exact note speed it should play therefore causing the pitch to be unaltered.

=== "Sample at 64000 Hz"
    ![](../assets/images/samples/waveform-64000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-64000hz-dark.png#only-dark)

    With a sample rate of 64000 Hz, twice the master sample rate, and tuned to the root key without any form of sample rate correction the sample will end up playing at half the note speed it should play therefore causing the pitch to be too low.

The reason a sample with a sample rate of 64000 Hz will play at half the note speed when played back in-game is because it has twice the amount of samples per second, and vice versa for a sample with a sample rate of 16000 Hz as it has half the samples per second, so this means that the samples will take a longer or shorter amount of time to finish when played back at the master sample rate. With sample rate correction the sample's note speed is increased or decreased so that it matches the expected note speed of a sample at 32000 Hz.

-----