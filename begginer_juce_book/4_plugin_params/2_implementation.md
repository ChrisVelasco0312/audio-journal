```cpp
juce::AudioProcessorValueTreeState::ParameterLayout
	DelayAudioProcessor::createParameterLayout()
{
	juce::AudioProcessorValueTreeState::ParameterLayout layout;
	
	layout.add(std::make_unique<juce::AudioParameterFloat>(
		juce::ParameterId { "gain", 1 },
		"Output Gain",
		juce::NormalisableRange<float> { -12.0f, 12.0f },
		0.0f
	));
	
	return layout;
}
```

the constructor for the `AudioParameterFloat`
takes 4 arguments:

Unique identifier `juce::ParameterID` object
we give the identifier "gain"
and 1 as a version hint.

Name of the param
it should be a human redable string
"Output Gain"

The range of the param as `juce::NormalisableRange` object
the `<float>` means range is expressed with float values

Final argument is default value of param
set to 0.0f since we want the output gain to be 0dB

both `juce::ParameterID`
and `juce::NormalisableRange`
are objects, we invoke constructors 
using the `{arguments}` syntax

### apply the parameter to `processBlock`
```cpp
float gainInDecibels = apvts.getRawParameterValue("gain")->load();
```

Now it reads the value from the gain parameter instead