# HISE

**HISE is a cross-platform open source audio application for building virtual instruments.**

It emphasizes on sampling, but includes some basic synthesis features for making hybrid instruments. 
You can build patches, design a custom interface and compile them as VST / AU plugin or iOS app. 

More information:

[HISE website](http://hise.audio)

## System requirements

HISE is tested on Windows and OSX with the following hosts:

- Cubase
- Ableton Live
- Logic
- Reaper

It supports x86 and x64 on Windows, altough the 64bit version is highly recommended.

## Highlights

### Sampler engine

- fast disk streaming sampler engine using memory mapped files
- multi mic sample support (with purging of single mic channels)
- looping with crossfades
- sample start modulation
- crossfade between samples for dynamic sustain samples
- customizable voice start behaviour
- regex parser for mapping samples
- custom monolith file format for faster loading times
- switch sample mappings dynamically

### Modulation

- complex modulation architecture for nested modulation of common parameters
- includes the most common modulators (LFO, envelopes)

### Audio Effects

- fast convolution reverb
- filters / eq
- phaser / chorus
- delay / reverb

### Javascript interpreter

- superset of Javascript built for real time usage (no allocations, low overhead function calls)
- write MIDI processing scripts
- create plugin interfaces with a WYSIWYG editor
- built in IDE features (autocomplete / API reference, variable watch, console debugging)
- combine DSP routines for custom effects

### C / C++ compiler

- embedded C JIT compiler for fast prototyping of DSP routines (based on TinyCC)
- API for adding DSP modules via dynamic libraries
- one click C++ build system for building VST / AU / AAX plugins (based on JUCE) from within HISE (using msbuild / xcodebuild)

## Licence

GPL v3 or a commercial licence for closed source usage. HISE is based on JUCE, which must be separately licenced.

## Included frameworks

For FFT routines and some vector operations, it is recommended to build HISE against the Intel IPP library (not included).

Apart from the JUCE C++ library, there are some other 3rd party frameworks and libraries included in HISE, which are all non restrictively licenced (either BSD or MIT):

- **ICSTDP DSP library**: A pretty decent DSP library with some good and fast routines.   [Website](https://www.zhdk.ch/index.php?id=icst_dsplibrary)
- **Tiny C Compiler** Awesome little compiler that translates C files into machine code within milliseconds. It is embedded into HISE as development tool. The compiler is LGPL licenced, so it is linked dynamically into HISE, but for closed source plugins, the C files will be compiled by a "real" compiler anyway.
- **Kiss FFT**: A easy and C-only FFT library with a clean interface and acceptable performance. It is used as fallback FFT when the IPP library is not available.
- **WDL** (just for the convolution, it might get sorted out in the future)
- some other public domain code taken from various sources (music-dsp.org, etc.).