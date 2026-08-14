```cpp
bool DelayAudioProcessor::isBusesLayoutSupported(const BusesLayout& layouts) const
{
	return layouts.getMainOutputChannelSet() == juce::AudioChannelSet::stereo();
}
```