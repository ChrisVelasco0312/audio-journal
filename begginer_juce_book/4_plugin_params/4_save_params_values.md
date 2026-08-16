Audio processor has two functions to serialize (save) and deserialize(load)
the plug-in's state: `getStateInformation` `setStateInformation`

**PluginProcessor.cpp**
```cpp
void DelayAudioProcessor::getStateInformation (juce::MemoryBlock& destData)
{
	copyXmlToBinary(*apvts.copyState().createXml(), destData);
}

void DelayAudioProcessor::setStateInformation (const void* data, int sizeInBytes)
{
	std::unique_ptr<juce::XmlElement> xml(getXmlFromBinary(data, sizeInBytes));
	if (xml.get() != nullptr && xml->hasTagName(apvts.state.getType())) {
		apvts.replaceState(juce::ValueTree::fromXml(*xml));
	}
}
```
