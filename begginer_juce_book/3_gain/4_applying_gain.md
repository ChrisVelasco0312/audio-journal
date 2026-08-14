changing the level of an audio signal is a matter of doing a multiplication
multiply every sample in the signal by 0.5, the new amplitude is half as high
Amplitude is related to loudenss but they are not the same thing
the result is quieter than before

```cpp
void DelayAudioProcessor::processBlock (juce::AudioBuffer<float>& buffer,
juce::MidiBuffer& midiMessages)
{
	juce::ScopedNoDenormals noDenormals;
	auto totalNumInputChannels = getTotalNumInputChannels();
	auto totalNumOutputChannels = getTotalNumOutputChannels();
	
	for (auto i = totalNumInputChannels; i < totalNumOutputChannels; ++i) 
		buffer.clear (i, 0, buffer.getNumSamples());
		
	buffer.applyGain(0.5f);
}
```






