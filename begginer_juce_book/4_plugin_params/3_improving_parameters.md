"gain" as identifier is error prone
it is better to define the parameter ID as constant
and from then on refer to it using that constant name

in **PluginProcessor.h** at the top below `#include`
```cpp
const juce::ParameterID gainParamId { "gain", 1 };
```
This declares a **constant** `gainParamID`
is a `juce::ParameterID` object

in **PluginProcessor.cpp**
in `createParameterLayout`

```cpp
layout.add(std::make_unique<juce::AudioParameterFloat>(
	gainParamID, // now uses the constant
	"Output Gain",
	juce::NormalisableRange<float> { -12.0f, 12.0f },
	0.0f
));
```

in `processBlock` update `gainInDecibels` code to
```cpp
float gainInDecibels = apvts.getRawParameterValue(gainParamID.getParamID()) -> load();
```

## A faster way to read param values

`apvts.getRawParameterValue()` is slow
There is a faster way to read param values

in **PluginProcessor.h** add in the `private:` section:
`juce::AudioParameterFloat* gainParam;`
This creates a `juce::AudioParameterFloat` object, named `gainParam`
`*` means this is **pointer** to the object

`gainParam` is not itself a `juce::AudioParameterFloat` obj
but will refer to one of the `juce::AudioParameterFloat` objects
from APVTS 

We will able to directly access **Output Gain** through the `gainParam` object

in **PluginProcessor.cpp** at the top is the `DelayAudioProcessor` constructor
```cpp
DelayAudioProcessor::DelayAudioProcessor()
#ifndef JucePlugin_PreferredChannelConfigurations
	: AudioProcessor (BusesProperties()
			#if ! JucePlugin_IsMidiEffect
			#if ! JucePlugin_IsSynth
			 .withInput ("Input", juce::AudioChannelSet::stereo(), true)
			#endif
			 .withOutput ("Output", juce::AudioChannelSet::stereo(), true)
			#endif
			 )
#endif
{
}
```

`#ifndef` and `#if` and `#endif`
are for the Projucer to cover all
different possible plug-in types.

Clean up
```cpp
DelayAudioProcessor::DelayAudioProcessor() :
	AudioProcessor(
		BusesProperties()
			.withInput("Input", juce::AudioChannelSet::stereo(), true)
			.withOutput("Output", juce::AudioChannelSet::stereo(), true)	
	)
{
}
```

A **constructor** is a special function that always has the same name as the object,
which is why this is called `DelayAudioProcessor::DelayAudioProcessor`

A **constructor** does not have a return type
it can have arguments in between ()
but this has none

Since `DelayAudioProcessor` is based on `juce::AudioProcessor`
we need to call the constructor of that class first

In cpp is done by writing a colon followed by `AudioProcessor` and args for its constructor

The argument for the `juce::AudioProcessor` constructor is `BusesProperties` object
that says the plug-in has stereo audio input and stereo audio output.

in the  {} braces add:

```cpp
auto* param = apvts.getParameter(gainParamID.getParamId());
gainParam = dynamic_cast<juce::AudioParameterFloat*>(param);
```

`apvts.getParameter(gainParamID.getParamId());`
looks up the parameter object in the APVTS

parameter is temporarily stored in a local variable named `param`
the type of this is `juce::RangedAudioParameter*`  but
we use shorthand `auto*`
means "some kind of pointer"

`dynamic_cast<juce::AudioParameterFloat*>`
a **cast** is a way to convert between different data types
this tells is a pointer to a `juce::AudioParameterFloat` object

The result of `dynamic_cast` gets stored in `gainParam` variable

We can now use `gainParam` to directly read the current value of param

in `processBlock` now in `gainInDecibels`
```cpp
float gainInDecibels = gainParam->get();
```

Since `gainParam` is a pointer
use -> arrow notation
to call the parameter object's `get()` function

The pointer apprach is a lot faster than `apvts.getRawParameterValue`
`getRawParameterValue` looks up the parameter by name in APVTS
which may involve many string comparisons, when having lots of params.

we keep track of `AudioParameterFloat*` 
accesing inmmediately the param through this pointer
without looking it up over and over again.
This is a type of "caching"

