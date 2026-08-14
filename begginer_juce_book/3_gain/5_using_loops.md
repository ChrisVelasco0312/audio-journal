```cpp
void DelayAudioProcessor::processBlock (juce::AudioBuffer<float>& buffer,
										juce::MidiBuffer& midiMessages)
```

**two arguments**
`juce::AudioBuffer<float>& buffer`
The audio samples in the `AudioBuffer` are floating-point values
between `-1.0f` and `1.0f` 
If block size is 128 there are 128 float values in `AudioBuffer`
in stereo is two times which is 256 values

The job of `processBlock` is **overwrite** sample values inside `AudioBuffer`
with new ones. 
`buffer.applyGain(0.5f);` does that:
It multiplies the samples in the `AudioBuffer` with 0.5
making them less loud

## applying gain by hand
```cpp
for (int channel = 0; channel < totalNumInputChannels; ++channel) {
	auto* channelData = buffer.getWritePointer(channel);
	
	for (int sample = 0; sample < buffer.getNumSamples(); ++sample) {
		channelData[sample] = channelData[sample] * 0.5f;
	}
}
```

