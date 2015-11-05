# patches
My Pure Data patches

You'll need pd-extended for these. I currently have this directory added in my
search path and just throw everything in there, but I'm new at this and it may
not be a sustainable strategy. YMMV.

Items of interest:

## polyphonic bank
The `jdp-poly-bank` patch functions as a 20-way polyphonic bank, which is
really handy for use with a MIDI keyboard. It expects input messages containing
a MIDI note and frequency. The arguments should be the name of an object that
accepts those same messages, and outputs an audio stream, followed by any arguments
for that object. The whole bank then outputs the combined audio stream. See
`jdp-midi-hammond` for an example.

## the hammond synth

![jdp-midi-hammond patch](http://i.imgur.com/hFE7Ri0.png)

I suggest looking at `jdp-midi-hammond` in order to get an idea of how to use
this. It consists of two parts: `jdp-hammond-controller` and `jdp-hammond-synth`.
`jdp-hammond-synth` accepts MIDI messages (as in `jdp-poly-bank`) and outputs
audio. Its first argument is a name, which should also be passed to the corresponding
`jdp-hammond-controller`. The controller adjusts the timbre of all synth objects with
the same name. By splitting this, it can be used with the `jdp-poly-bank` object easily.

The controller object displays a set of nine drawbars, a vibrato controller, and a bang
which can be used to "remind" any synth objects of the current settings. The controller
input accepts messages which provide settings (from 0 to 8) for the drawbars.
