Programs in cpp consists of **objects** and **functions**
An object is a "thing"  that lives inside computer's memory (RAM)

`DelayAudioProcessorEditor` is an object
represents the plug-in's user interface

`paint` is a function
draws the contents of the editor on the screen
and is part of the `DelayAudioProcessorEditor`

`DelayAudioProcessorEditor` is the object `paint` is the name of the function
it belongs to `DelayAudioProcessorEditor::paint`
Between parenthesis are the arguments of the functions
`paint` has one argument
An object of type `juce::Graphics`
`void` is the function's **return type**

```
void DelayAudioProcessorEditor::paint (juce::Graphics& g)
{
 g.fillAll (juce::Colours::blue);
 g.setColour (juce::Colours::blue);
 g.setFont (40.0f);
 g.drawFittedText ("My First Plug-in!",
	 getLocalBounds(), juce::Justification::centred, 1);
}
```

The order of the statements in the body function matters.
One statement can overwrite the actions of others.
`g.fillAll` acts over all the background, 
if it is after `g.setColour` or `g.setFont`
we will not see it.

The `paint` function `juce::Graphics& g` argument
means that when the host tells the plugin to paint itself
the host also provide a `juce::Graphics` object
This object knows how to draw lines, text and images.

`fillAll` is a function belongs to `juce::Graphics`
this fills all the background with the `juce::Colours::blue`

`juce::` is the **namespace**

`g.setColour(juce::Colours::white);`
sets the drawing color to white
change the color of the pen used by subsequent drawing ops

`g.setFont(40.0f);`
Set the size of the font to 40 points.
the f at the end of `40.f` the number means is a **floating-point number**
[[literals]]

```
 g.drawFittedText ("My First Plug-in!",
	 getLocalBounds(), juce::Justification::centred, 1);
```
The first argument is a **string** that contains the text to display "My First Plug-in!"
The second argument is the area (a rectangle) into which to fit the text
`getlocalBounds()` get the size of the entire editor window
it belongs to the `DelayAudioProcessorEditor` object
Third arguments determines how the text is positioned in the area
`juce::Justification::centred` centers the text
horizontally and vertically.
Fouth argument is the maximum number of lines to use `1`


