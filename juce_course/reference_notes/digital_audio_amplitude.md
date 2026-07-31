
## dB Measurements in digital audio

In DSP sound levels are calculated relative to maximum allowable digital amplitude
befor clipping (0 dBFS) 

**dBFS** is  **Decibels relative to full scale**

0 dBFS represents a maximum capacity (all bits set to 1)
all valid signal levels are expressed as negative values
$$
dBFS = 20log_{10}(\frac{A}{A_{max}})
$$
$A$ is the current sample amplitude
$A_{max}$ is the maximum achievable amplitude for the sample bit depth.
$-\infty dB$ represents complete silence 0
Every 6 dB reduction corresponds to approx half the signal amplitude.
$20log_{10}(0.5) = -6.02 dB$

