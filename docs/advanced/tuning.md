---
icon: material/waveform
---

# Sample Tuning

<div class="grid cards" markdown>

-   :material-file-document-edit:{ .lg } __&nbsp;THIS PAGE IS A WIP__
  
    ---

    This page is a work in progress and requires further editing.

</div>

## — Tuning (Modular)
!!! warning "Attention"
    **Only Instruments use — tuning**

— tuning means that the sample's root key is tuned in relation to the tuning float of note `60 (C5)` at 32000 Hz. This means that the lower the tuning float value the higher the note speed will be, and by extension the higher the note's perceived pitch will be; the higher the tuning float value the lower the note speed will be, and by extension the lower the note's perceived will be.

So to get our sample's root key to the correct note speed we need to use the following calculation:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$1\div Float = Note\hspace{1 mm}Speed$

As an example if our sample has a root key of `72 (C6)` with a sample rate of 32000 Hz and we want it to play `60 (C5)` then we need to achieve a note speed of `2` for our sample to be tuned to the correct pitch; to do this we divide `1` by `0.5`, with `0.5` being the tuning float value for `72 (C6)`.

!!! info
    For — tuning your note speeds are automatically calculated, as every instrument has a sample assigned to a range of specific notes, where the tuning float determines the sample root key's note speed in relation to `60 (C5)`


## — Tuning (Static)
!!! warning "Attention"
    **Only Drums and Sound Effects use — tuning**

— tuning means that the sample's root key is tuned as if it's always `60 (C5)` at 32000 Hz. This means that the lower the tuning float value the lower the note speed will be, and by extension the lower the note's perceived pitch will be; the hight the tuning float value the higher the note speed will be, and by extension the higher the note's perceived pitch will be.

So to get our sample's root key to the correct note speed we need to use the following calculation:

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;$1\times Float = Note\hspace{1 mm}Speed$

As an example if our sample has a root key of `72 (C6)` with a sample rate of 32000 Hz and we want it to play `60 (C5)` then we need to achieve a note speed of `0.5` for our sample to be tuned to the correct pitch; to do this we multiply `1` by `0.5`, with `0.5` being the tuning float we would use as with — tuning the note speed is equal to the tuning float value.

!!! info
    For — tuning your note speeds are manually caculated, as every drum and sound effect has a single sample assigned to a single specific note, where the tuning float is equal to the note speed, as the note speed of your sample's root key is always assumed to be equal to `60 (C5)`'s note speed.

## Tuning Calculation

### Sample Rate Correction

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


=== "16000Hz"
    ![](../assets/images/samples/waveform-16000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-16000hz-dark.png#only-dark)

=== "32000Hz"
    ![](../assets/images/samples/waveform-32000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-32000hz-dark.png#only-dark)

=== "64000Hz"
    ![](../assets/images/samples/waveform-64000hz-light.png#only-light)
    ![](../assets/images/samples/waveform-64000hz-dark.png#only-dark)

-----