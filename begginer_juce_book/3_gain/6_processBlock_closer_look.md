
## juce::ScopedNoDenormals noDenormals
at top of `processBlock` is
`juce::ScopedNoDenormals noDenormals;`

Sample amplituds in `AudioBuffer` are -1.0f and 1.0f
full range is  as small as $10^{-38}$ and as large as $10^{38}$

When a sound is fading out
amplitude becoms smaller over time
dropping towards 0.

Once sample value becomes smaller than $10^{-38}$
`float` switches to a different internal representation
known as **denormal** or **subnormal** numver.

**denormals** are super slow
causing CPU usage spike

`juce::ScopedNoDenormals` object tell the CPU to round off
floating-point numbers to zero when they become really small
instead of making them denormals.

Scoped means that JUCE automatically
stores the CPU prev behavior once `processBlock` ends
So rounding-to-zero only happens inside processBlock 
doesn't affect any other operations in the program.

---

```cpp
auto totalNumInputChannels = getTotalNumInputChannels();
auto totalNumOutputChannels = getTotalNumOutputChannels();

for (auto i = totalNumInputChannels; i < totalNumOutputChannels; ++i)
	buffer.clear (i, 0, buffer.getNumSamples);
```

The purpose of this is to write silens in the audio buffer
samples with value 0.0f if there are more output channels than input channels.

If plug-in has a mono input bus (one channel)
and a stereo output bus (two channels)
`juce::AudioBuffer` contain two channels of sample data
first filled with audio of mono input
second will be filled with arbitrary numbers or garbage

To prevent outputting garbage
we replace everything in unused input with silence.

This is `defensive programming`

> Notice the loop does not have {}
> in C++ is allowed when loop only contains a single line of code

---

`juce::MidiBuffer` is the second argument contain MIDI messages
MIDI describes events such as `note on-off` and are used in Synth plug-ins

```cpp
void DelayAudioProcessor::processBlock (juce::AudioBuffer<float>& buffer),
								[[maybe_unused]] juce::MidiBuffer& midiMessages)
```

`[[maybe_unused]]` attribute makes c++ compiler understend
we are not going to use `juce::MidiBuffer` object inside function
