Plug-in params are owned by `DelayAudioProcessor` object
We use a helper object
`juce::AudioProcessorValueTreeState` or APVTS

in `PluginsProcessor.h` after `private:` add
```cpp
juce::AudioProcessorValueTreeState apvts {
	*this, nullptr, "Parameters", createParameterLayout()
};

juce::AudioProcessorValueTreeState::ParameterLayout createParameterLayout();
```

This adds two things to `DelayAudioProcessor`
1 A variable named `apvts`: The `AudioProcessorValueTreeState` object
2 A new function named `createParameterLayout`
A helper function that creates the plug-in parameter objects added to APVTS

The code between {} are the arguments that get passed to the
constructor of `AudioProcessorValueTreeState`

A constructor makes room for the object in computer's memory
and then initializes it.

`*this` First argument connects APVTS to `DelayAudioProcessor`
`this` means "myself"

`nullptr` second argument allows to provide undo manager to APVTS
is used to tell APVTS we do not want an undo manager

`"Parameters"` a text string containing name of APVTS

`createParameterLayout()` is a list of the parameters the plug-in has

> {} braces in have different meaning than before
> for a constructor { } are used to differentiate between
> calling a function and using a constructor

## implementation

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