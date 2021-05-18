# Clip Evolver

Welcome to Clip Evolver! To install, drag the Clip-Evolver.amxd file into your Live set. To engage the device, click the “Power” button. The device will need about 20 seconds to retrieve the algorithms over the Internet—if it's still not active after about a minute, click the “Restart” button. Feel free to select “Power” at any time during the load-up period, but the clip will not start evolving until the algorithms have been retrieved.

This device changes MIDI data, so make sure you’ve duplicated any valuable clips before engaging. Under the hood, two AI algorithms (MusicRNN and MusicVAE) from Google Magenta take the MIDI from the clip and continue it naturalistically. When the playhead reaches the end of the loop, that continuation MIDI replaces the original MIDI.

This process will repeat as long as (1) the transport is playing, (2) the clip is playing, (3) the “Power” checkbox is selected, and (4) the number in the “Clip Slot” field matches the scene number of the clip. If you want the process to affect any clip playing in the track, regardless of scene, select the “Follow” button. The maximum clip length at this time is 4 bars—if your clip is longer than 4 bars, only the first 4 bars will be evolved.

The effectiveness of this device depends very much on the speed of your computer—multiple instances of Clip Evolver will only work on the fastest machines. This is due to the processing time required by the algorithms. On slower computers, the algorithms may not have time to return the notes before the clip loops, leading to an endless cycle of waiting for notes that will never come. If you have a slower computer, make sure the “Interp” checkbox is deselected. This will drop the interpolating algorithm (MusicVAE) and just use the continuing algorithm (MusicRNN,) leading to quicker return times but less melodic continuity. You can also deselect this box if you want more randomness.

The “Temperature” dial affects the intensity of the algorithms. Low temperatures mean fewer numbers of longer notes. Higher temperatures mean many short notes spread out over a larger pitch range. The right hand side of the device adjusts the Live-specific attributes of the output notes, with sliders for “Probability,” “Velocity,” “Velocity Deviation,” and “Release Velocity.”

At the bottom-right is a pitch filter. All notes are selected by default. If you deselect a pitch, the device will randomly decide whether to search up or down for the nearest selected pitch. If all pitches are deselected, no notes will be returned.

At the far right are octave range sliders, with “Lo Oct” representing the octave floor and “Hi Oct” representing the octave ceiling, rooted in the note C. They will constrain the algorithms' output to the desired pitch range (inclusive for "Lo Oct" and exclusive for "Hi Oct.") For example, if you have “Lo Oct” set to “2” and and “Hi Oct” set to “5,” all notes between and including C2 and B4 will be let through as is. All notes outside that range will be converted to the nearest in-range octave. If “Lo Oct” is greater than or equal to “Hi Oct,” no notes will be returned.

This is Version 1.0 so there may be a few bugs—it’s viable in the studio, but at this point I would say perform live at your own risk. Sometimes the algorithms don’t make any notes at all or get stuck on the same notes, but they usually recover after a cycle or two. If this happens for a long period, try adding some notes manually or increasing the temperature. If all else fails, click the “Restart” button at the bottom-right.

Also, the device will work only when frozen. If you unfreeze the device, the reference to the Node script will break. However, I have also included an unfrozen version of the device ([**Clip-Evolver-Unfrozen.zip**](Clip-Evolver-Unfrozen.zip)) which you can play around with.
