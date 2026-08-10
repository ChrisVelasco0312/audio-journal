Programs in cpp consists of **objects** and **functions**
An object is a "thing"  that lives inside computer's memory (RAM)

`DelayAudioProcessorEditor` is an object
represents the plug-in's user interface

`paint` is a function
draws the contents of the editor on the screen
and is part of the `DelayAudioProcessorEditor`

```
void DelayAudioProcessorEditor::paint (juce::Graphics& g)
{
 //body
}
```

The name of the function: `DelayAudioProcessorEditor::paint`