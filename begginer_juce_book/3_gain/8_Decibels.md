Human hearing is logarithmic in nature
We can hear differences between soft sounds
the louder the sound becomes, the less sensitive our ears are.

gain in decibels or dB follows a logarithmic scale

`processBlock`
```cpp
//1
float gainInDecibels = -6.0f;

float gain = juce::Decibels::decibelsToGain(gainInDecibels);

for (int channel = 0; channel < totalNumInputChannels; ++channel) {
	auto* channelData = buffer.getWritePointer(channel);
	
	for (int sample = 0; sample < buffer.getNumSamples(); ++sample) {
		channelData[sample] *= gain;
	}
}
```

1_Gain amount is placed in a new variable named `gainInDecibels`
it has the value -6.0f for -6 dB
2_`juce::Decibels::decibelsToGain()` converts it into linear units
for -6 dB the value of `gain` will be 0.5f
3_Instead of constant number 0.5f, use `gain` variable to
multiply the sample values by.

The formula of decibelsToGain() is:
$$
10^{\frac{gainInDecibels}{20}}
$$
