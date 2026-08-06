# Exploring the Plugin Source Code

## 1. Project State & Workflow
* **Initial Code Skeleton:** The provided code includes a minimal skeleton to get started. It currently builds, runs, and iterates through samples, but does not apply any audio processing yet.
* **Learning Approach:** You will work in the `todo` folder and can compare your work with the `complete` folder. It is highly recommended to implement and test your solution before checking the complete folder to practice active recall.

## 2. JUCE Modules Structure
* **`tremolo_plugin` Folder:** The plugin's internals are implemented as a JUCE module to allow usage from both the plugin binary and automated test projects.
* **Includes:**
  * All header files used in the module are `#included` in `tremolo_plugin.h`.
  * All implementation (`.cpp`) files are `#included` in `tremolo_plugin.cpp`.
  * No other files in this folder should `#include` any other files.

## 3. PluginProcessor Class (`PluginProcessor.h` & `.cpp`)
The `PluginProcessor` class handles reporting plugin information to the host and inherits from `juce::AudioProcessor`.

### Key Functions:
* **`prepareToPlay()`:** 
  * Invokes the `prepare()` member function of the `Tremolo` class.
  * Passes `sampleRate` (number of samples representing one second of audio) and `expectedMaxFramesPerBlock` (the largest number of frames expected).
  * *Note:* The host might pass more frames in `processBlock()` than declared here, so defensive coding is required.
* **`releaseResources()`:** 
  * Calls `Tremolo::reset()` to prepare the effect for fresh playback (e.g., from a new playback location).
* **`processBlock()`:** 
  * Takes a buffer of samples (floats) and a buffer of MIDI messages (ignored for now).
  * Empties input channels of the audio buffer not used for processing to prevent playback of uninitialized memory (which can cause unpleasant sounds).
  * Passes the audio buffer to the `Tremolo` class instance for the actual processing.
  * *Future Work:* Updating parameters and implementing bypass will be added here later.

## 4. The Tremolo Class & Separation of Concerns
* **Design:** To facilitate a better separation of concerns (adhering to the Single Responsibility Principle), actual audio processing logic is extracted into a separate `Tremolo` class.
* **Usage:** An instance of `Tremolo` is added as a member of the `PluginProcessor` class.
* **Current State:** For simplicity, its declaration and definition are entirely in a single header file. 
  * `prepare()` and `reset()` currently do nothing.
  * `process()` contains basic frame and channel iteration (frame-wise processing) but applies no observable effect yet.

## 5. Plugin Entry Point
* **`createPluginFilter()`:** 
  * A free function defined in the global namespace.
  * Returns a raw pointer to a freshly created processor instance.
  * Acts as the entry point to the plugin code (similar to the `main()` function for JUCE audio plugins).
  * Modify parameters passed to the plugin's constructor here.

## Summary
This lesson detailed how the plugin processor code is laid out across header and `.cpp` files, and how audio processing logic is cleanly extracted into a dedicated class (`Tremolo`) utilized by the main processor. The next steps will involve actively implementing the tremolo effect within this prepared canvas.