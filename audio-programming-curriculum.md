# University Curriculum: Audio Programming & Audio Engineering

**A complete, self-study university program from zero to professional audio developer.**

> *"The best time to start was yesterday. The second best time is now."*

---

## How to Use This Curriculum

This is a **holistic, ordered university program** designed so that each level builds on the previous one. A student who jumps into Will Pirkle's book without DSP fundamentals will struggle. A student who skips the math will hit walls. This curriculum solves that by being **completely sequential** — every resource is placed exactly where it needs to be.

- **Level 0**: Complete beginner foundations (math, programming, physics, domain knowledge)
- **Level 1**: DSP fundamentals
- **Level 2**: Audio-specific DSP and signal processing
- **Level 3**: Audio plugin development (C++, JUCE, effects)
- **Level 4**: Synthesis and sound design programming
- **Level 5**: Advanced topics and specialization

**Estimated total time**: 2-3 years at a dedicated pace (10-15 hours/week), or faster for full-time students.

Each topic in this curriculum is split into two clearly-labelled blocks:

- **MAIN MATERIAL** — the resource(s) you actually work through to learn the topic. This is your "course." If it is a book and no free online course covers the same ground, the book *is* your course and is marked as such.
- **BIBLIOGRAPHY REFERENCES** — additional reading to deepen understanding. These are optional and supplement the main material; you can skip them if budget or time is tight.

### Legend for resource type

| Tag | Meaning |
|---|---|
| **COURSE (FREE)** | Free online course with all lectures/materials accessible for $0. |
| **COURSE (PAID)** | Online course(s) requiring payment — free alternative is always listed alongside. |
| **BOOK (MAIN)** | A book *replaces* a free course — there is no open course that covers the same material, so you treat the book as your main course. Pay the ~$30–$80 once; it pays off for years. |
| **BOOK (BIB)** | A book used as a bibliography companion to a free (or paid) course. Optional. Skip without losing the path. |
| **REFERENCE (FREE)** | Free online reference site / docs you consult as needed. |
| **VIDEO (FREE)** | Free YouTube/lecture video series. |
| **COMMUNITY (FREE)** | Free forum / Discord / Reddit to ask questions. |

### Note on pricing (verify before enrolling)

> **Coursera (as of July 2026):** In mid-2025, Coursera replaced its "Free Audit" mode with "Preview Mode," which allows free access to only the *first module* of most courses. Full content now requires paying for the individual course or subscribing to Coursera Plus ($59/month or $399/year). Some courses may still offer "Full Course, No Certificate" access, but availability varies.
>
> **edX** kept free audit mode on most of its courses (verify each course's enrollment page).
>
> Always check the current pricing on the platform before enrolling. Free alternatives are listed beside every paid resource in this curriculum.

**Cheapest viable path (everything you can get for $0):** If you only spend the absolute minimum, you can complete Levels 0–5 using *only* MIT OCW, Khan Academy, Think DSP, dspguide.com, the JUCE course, The Cherno, and free YouTube/community resources. Books marked **BOOK (MAIN)** are the only purchases the curriculum treats as "near-essential" — and even those are skippable if you are willing to hunt harder for free online coverage of the same topics.

---

## LEVEL 0: FOUNDATIONS

*"You can't build a house on sand."*

This level ensures the student has every prerequisite needed before touching DSP or audio code. The order within Level 0 matters: start with math and programming in parallel, then add physics and domain knowledge.

---

### 0.1 — Mathematics Foundations

Without math, DSP is just copying code you don't understand. Don't study math in isolation — always keep audio applications in mind and return to these resources when you hit a wall in later levels.

**Order:** Work through these sequentially, but revisit as needed.

#### MAIN MATERIAL

Pick based on your current level — you only need one starting point.

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Khan Academy** — math tracks (arithmetic → algebra → trigonometry → precalculus → basic calculus) | COURSE (FREE) | Free | <https://www.khanacademy.org/math> | Start here if you need to rebuild school math. Interactive, self-paced, free forever. |
| **Math Overboard! (Basic Math for Adults)** by Colin W. Clark (2 vols) | BOOK (MAIN) | ~$30/vol | Search by title + author | Choose this if you prefer learning from a book and your school math is weak. Written for adults. |
| **3Blue1Brown — "Essence of Linear Algebra" + "Essence of Calculus"** | VIDEO (FREE) | Free | <https://www.youtube.com/@3blue1brown/playlists> | Beautiful visual explanations. Watch the linear-algebra and calculus journeys *once,* even if you also use Khan Academy. |

**Specific math topics you need (in rough order):**

1. **Arithmetic and Basic Algebra** — variables, equations, functions, graphs
2. **Trigonometry** — sine, cosine, tangent, unit circle, radians, phase. *Critical for audio.*
3. **Complex Numbers** — imaginary unit, complex plane, Euler's formula (e^(jθ) = cos(θ) + j·sin(θ)). *Essential for DSP.*
4. **Logarithms and Decibels** — log base 10, decibel scale, how humans perceive loudness and frequency. *Used everywhere in audio.*
5. **Calculus (introductory)** — derivatives, integrals, limits, basic differential equations. *You need this for understanding filters and continuous signals.*
6. **Linear Algebra (basics)** — vectors, matrices, matrix multiplication. *Used in advanced DSP, machine learning for audio.*
7. **Probability & Statistics (basics)** — random variables, mean, variance, probability distributions. *Useful for noise generation, stochastic processes.*

#### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **An Introduction to the Mathematics of Digital Signal Processing** by F.R. Moore (Computer Music Journal, 1978) | BOOK (BIB) | Paywall (often findable as PDF) | <https://www.jstor.org/journal/compmusic> (search JSTOR/Google Scholar for "Moore Introduction to the Mathematics of DSP") | Two-part article, audio-targeted math. Read it for the bridge between math and DSP; not required to complete the path. |
| **Musimathics Vol. 1** by Gareth Loy | BOOK (BIB) | ~$50 | Publisher: <https://mitpress.mit.edu/9780262122826/musimathics-volume-1/> · search: <https://www.google.com/search?q=Musimathics+Gareth+Loy+MIT+Press> | Mathematical foundations of music (scales, acoustics, psychoacoustics). MIT Press. |
| **Musimathics Vol. 2** by Gareth Loy | BOOK (BIB) | ~$50 | Publisher: <https://mitpress.mit.edu/9780262122825/musimathics-volume-2/> · search: <https://www.google.com/search?q=Musimathics+Gareth+Loy+MIT+Press> | Digital audio, filtering, Fourier, sound synthesis. |

> **Key insight from Matthijs Hollemans (audiodev.blog):** *"Don't go and study math on its own, do it in the context of digital signal processing. Get a couple of DSP books first, and if you get stuck, level up the areas of math you're having problems with."*

---

### 0.2 — Programming Foundations

The audio programmer's language of choice is **C++**. However, starting C++ from zero while also learning DSP is overwhelming. The strategy is: learn programming basics in a gentle language first, then transition to C++.

**Order:** 0.2a first, then 0.2b.

#### 0.2a — Programming Fundamentals (any language)

*If you already know how to program, skip to 0.2b.*

##### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Harvard CS50x** | COURSE (FREE) | Free (edX audit) | <https://cs50.harvard.edu/x> | Best intro to computer science. Teaches C in the second half. Covers loops, functions, arrays, memory. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Python for Everybody** by Charles Severance | BOOK (BIB) | Free (book/course) | <https://www.py4e.com> | Gentle introduction to programming in Python. Great for non-programmers. |
| **Automate the Boring Stuff with Python** by Al Sweigart | BOOK (BIB) | Free online | <https://automatetheboringstuff.com> | Practical, fun intro to programming concepts. |

**What to learn at this stage:**

- Variables, data types, operators
- Control flow (if/else, loops)
- Functions and scope
- Arrays/lists
- Basic file I/O
- The concept of compilation vs interpretation
- Debugging (using a debugger, reading error messages)

#### 0.2b — C++ for Audio

*Once you have basic programming knowledge, jump into C++. If your goal is audio software, go straight to C++ — don't waste time learning "simpler" languages first.*

##### MAIN MATERIAL

Pick one of the first three rows as your primary course; the rest are alternatives/references.

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **C++ Primer (5th Edition)** by Lippman, Lajoie & Moo | BOOK (MAIN) | ~$55 | Publisher: <https://www.informit.com/store/c-primer-9780321714114> | The recommended book for C++ beginners. Comprehensive, well-organized. Treat it as your C++ "course." |
| **A Tour of C++ (3rd Edition)** by Bjarne Stroustrup | BOOK (MAIN) | ~$40 | Publisher: <https://www.informit.com/store/a-tour-of-c-plus-plus-9780136870183> | A faster overview by C++'s creator. Good if you already program in another language. |
| **The Cherno — C++ YouTube Series** | VIDEO (FREE) | Free | <https://www.youtube.com/@TheCherno> (C++ playlist) | Excellent, very clear video series. A free alternative if you cannot afford a book. |
| **learncpp.com** | REFERENCE (FREE) | Free | <https://www.learncpp.com> | Comprehensive, regularly updated C++ tutorial. Use alongside the book or videos. |
| **cppreference.com** | REFERENCE (FREE) | Free | <https://en.cppreference.com> | Bookmark this. Indispensable reference for the C++ standard library. |

**Minimum C++ knowledge needed for audio:**

- Modern C++ (C++11 or newer): `auto`, range-based `for` loops, smart pointers, lambdas
- Classes and objects (OOP basics)
- Templates (basic understanding)
- Standard library containers (`vector`, `array`)
- References and pointers
- Header files and compilation model
- RAII (Resource Acquisition Is Initialization)
- You don't need to be a C++ expert — know enough to read and write clear, functional code.

**IDE Setup:**

- **macOS**: Xcode (free from Mac App Store)
- **Windows**: Visual Studio Community Edition (free from <https://visualstudio.microsoft.com>)
- **Linux**: CLion (paid, JetBrains) or VSCode + CMake
- **Any platform**: VSCode (free, but requires configuring the C++ toolchain)

> **Important:** Learn C++ and audio programming *together*. Studying C++ in isolation is not productive. Start writing simple audio code as soon as you know the basics.

---

### 0.3 — Physics of Sound & Acoustics

Understanding how sound works in the physical world is essential before processing it digitally.

**Order:** 0.3a first, then 0.3b.

#### 0.3a — Physics of Sound (foundational)

##### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **MIT OCW 8.03 — Physics III: Vibrations and Waves** | COURSE (FREE) | Free | OCW search: <https://ocw.mit.edu/search?q=8.03> · Lewin lectures on YouTube: <https://www.youtube.com/playlist?list=PLUl4u3cNGP63X18CE9nFgVjZks2m3-vS1> | **Best free option.** Prof. Walter Lewin (classic) or Prof. Yen-Jie Lee (2016). Covers vibrations, waves, sound waves, Fourier series. Excellent video lectures. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **University of Rochester — Fundamentals of Audio and Music Engineering Part 1** (Coursera) | COURSE (PAID) | May require payment | <https://www.coursera.org/learn/audio-engineering> | Coursera Preview Mode: only first module free. Covers vibrations, waves, electronics fundamentals. |

**What to learn:**

- Sound as vibration and wave propagation
- Frequency, wavelength, amplitude, period
- The electromagnetic spectrum vs. audible spectrum (20 Hz – 20 kHz)
- Speed of sound, resonance, harmonics
- How microphones and speakers work (transducers)
- Basic electronics: voltage, current, resistance, impedance

#### 0.3b — Acoustics & Psychoacoustics

##### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Fundamentals of Acoustics** (IIT Kanpur — Swayam/NPTEL) | COURSE (FREE) | Free | <https://nptel.ac.in> (search the catalog for "Acoustics") or <https://swayam.gov.in> | Comprehensive acoustics principles. NPTEL course IDs are occasionally renumbered; search by course name on the homepage. |
| **Architectural Acoustics** (IIT Kharagpur — Swayam/NPTEL) | COURSE (FREE) | Free | <https://nptel.ac.in/courses/112101096> (or search "Architectural Acoustics NPTEL") | Room acoustics, sound design for spaces. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Intro to Acoustics Part 1 & 2** (KAIST — Coursera) | COURSE (PAID) | May require payment | <https://www.coursera.org/learn/intro-to-acoustics> | Coursera Preview Mode: only first module free. Intermediate level, requires calculus. (Part 2 lives on a neighbouring slugged course — search "intro-to-acoustics" on Coursera if the link changes.) |

**What to learn:**

- Wave equation, standing waves, modes
- Impedance and its significance
- Room acoustics: reflection, absorption, reverberation
- How humans hear: ear anatomy, frequency response of hearing
- Loudness perception (Fletcher-Munson curves, equal-loudness contours)
- Pitch perception, critical bands, masking

---

### 0.4 — Domain Knowledge: The Audio World

*You can't write audio software if you don't understand what audio professionals do with it. This is called "domain knowledge."*

#### 0.4a — Learn to Use a DAW (Digital Audio Workstation)

##### MAIN MATERIAL

Pick one DAW and get hands-on with it for a few weeks.

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **REAPER** | Software | $60 (free trial, fully functional) | <https://www.reaper.fm> | Lightweight, excellent, affordable. Recommended for audio programmers. |
| **Ableton Live Lite** | Software | Free with many audio interfaces | <https://www.ableton.com/en/live-lite> | Popular, good for electronic music. |
| **Logic Pro** | Software | $200 (macOS only) | <https://www.apple.com/logic-pro> | Industry standard on Mac. |
| **Pro Tools — Intro** | Software | Free tier | <https://www.avid.com/products/pro-tools-intro> | Free intro version of the studio industry standard. |

**What to do:** Record audio, use plugins (EQ, compressor, reverb, delay), create MIDI instruments, understand signal flow, automation, mixing basics. You don't need to be a producer, but you need to understand the workflow.

#### 0.4b — Learn Basic Music Theory

##### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **musictheory.net** | REFERENCE (FREE) | Free | <https://www.musictheory.net> | Interactive lessons on notes, scales, intervals, chords, rhythm. |
| **Hooktheory** | REFERENCE (FREE) | Free tier | <https://www.hooktheory.com> | Modern approach to music theory. |

**What to learn:** Notes and frequencies, scales (especially chromatic and major/minor), intervals, chords, rhythm and time signatures, MIDI basics, how synthesizers work at a high level.

#### 0.4c — Learn Sound Design Basics

##### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Andrew Huang — synthesis videos** | VIDEO (FREE) | Free | <https://www.youtube.com/@andrewhuang> | Good introductions to synthesis concepts. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Syntorial** | Software/training | ~$130 | <https://www.syntorial.com> | Teaches you to hear and create synth sounds by ear. Highly recommended but optional. |

**What to learn:** Subtractive synthesis, FM synthesis, sampling, envelope (ADSR), filters (low-pass, high-pass, band-pass), LFOs, modulation. Understanding these concepts from a *user* perspective before implementing them as a programmer.

---

## LEVEL 1: DIGITAL SIGNAL PROCESSING (DSP) FUNDAMENTALS

*"DSP is the heart of audio programming."*

**Prerequisites:** Level 0 complete (math basics, basic programming, physics of sound).

**Strategy:** Start with the most accessible DSP resource, then deepen. Don't jump to advanced books before you have the basics.

---

### 1.1 — Gentle Introduction to DSP

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Think DSP** by Allen B. Downey | BOOK (MAIN) | Free online (print ~$30) | <https://greenteapress.com/wp/think-dsp> | **START HERE.** Written for beginners, light on math, uses audio signals for examples. The single best first DSP book. Read it cover-to-cover and do the exercises. |
| **The Scientist and Engineer's Guide to Digital Signal Processing** by Steven W. Smith | BOOK (MAIN) | Free online (<https://www.dspguide.com/pdfbook.htm>) | <https://www.dspguide.com> | Comprehensive, written for newcomers. Not audio-specific but covers everything. Download the PDFs. Read alongside Think DSP. |
| **DSP For Audio Programming** | REFERENCE (FREE) | Free | <https://www.dspforaudioprogramming.com> | Interactive guide designed specifically for audio. Great visualizations. |

**Core topics to master at this stage:**

- What is a signal? Continuous vs. discrete
- Sampling: sample rate, Nyquist theorem, aliasing
- Quantization and bit depth
- Digital audio representation (PCM)
- What is a system? Input/output
- Linearity and time-invariance (LTI systems)
- Impulse response
- Convolution (the most important operation in DSP)
- Frequency domain: what does it mean?
- The Fourier Transform (conceptual understanding)
- The Discrete Fourier Transform (DFT)
- The Fast Fourier Transform (FFT)
- Frequency spectrum, magnitude, phase
- Windowing
- Decibels in digital audio (dBFS)

### 1.2 — Intermediate DSP

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **MIT RES.6-007 — Signals and Systems** (Alan Oppenheim, OCW) | COURSE (FREE) | Free | <https://ocw.mit.edu/courses/res-6-007-signals-and-systems-spring-2011/> | **Best free option.** Prof. Oppenheim's classic lectures. Covers Fourier analysis, Laplace, Z-transforms, sampling, filtering. The gold standard for DSP theory. |
| **projet μ** by Yü Fang | COURSE (FREE) | Free | <https://mu.krj.st> | Teaches DSP from scratch in C. Linux-focused but works elsewhere. Requires complex numbers and basic calculus. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Understanding Digital Signal Processing** by Richard G. Lyons | BOOK (BIB) | ~$80 | Search by title + author (Pearson/Prentice Hall) | More math than Think DSP / Smith. Reads after the free intro material. Buy only if the free MIT OCW path feels insufficient — it is excellent but skippable. |
| **EPFL Digital Signal Processing 1: Basic Concepts and Algorithms** (Coursera) | COURSE (PAID) | May require payment | <https://www.coursera.org/specializations/digital-signal-processing> | Coursera Preview Mode: only first module free. Intermediate. The MIT RES.6-007 course above is the free alternative. |

**Core topics to master:**

- Z-Transform
- Transfer functions, poles and zeros
- FIR filters (design and implementation)
- IIR filters (design and implementation)
- Filter design: Butterworth, Chebyshev, etc.
- Bilinear transform
- Frequency response
- Group delay
- Spectral analysis
- Multi-rate signal processing (basics)

### 1.3 — University-Level DSP (Optional but Recommended)

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **MIT 6.003 — Signals and Systems** (OCW) | COURSE (FREE) | Free | <https://ocw.mit.edu/courses/6-003-signals-and-systems-fall-2011/> | Prof. Dennis Freeman. Fourier representations, Laplace, Z-transforms, sampling, modulation. Lecture 25 is literally "Audio CD." |
| **MIT RES.6-008 — Digital Signal Processing** (OCW) | COURSE (FREE) | Free | <https://ocw.mit.edu/courses/res-6-008-digital-signal-processing-spring-2011/> | Graduate-level but accessible. The gold standard for DSP theory. |

> **Cheapest viable path for Level 1:** Think DSP (free) → dspguide.com (free) → MIT RES.6-007 (free) → MIT 6.003 (free). Lyons's book is highly recommended but optional.

---

## LEVEL 2: AUDIO-SPECIFIC DSP & SIGNAL PROCESSING

*"Now we apply DSP to the domain of sound and music."*

**Prerequisites:** Level 1 complete (solid DSP fundamentals).

---

### 2.1 — Audio Signal Processing

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Audio Signal Processing for Music Applications** (Xavier Serra & Julius O. Smith — Stanford/UPF) | COURSE (PAID) | Coursera; check current access | <https://www.coursera.org/learn/audio-signal-processing> | Spectral processing, DFT, STFT, sinusoidal model, harmonic model. Excellent bridge between DSP theory and audio. Coursera's audit/preview availability varies — try the course page. If unavailable free: see bibliography alternative below. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Hack Audio** by Eric Tarr | BOOK (BIB) | Book ~$50; site free | Book: search by title (CRC Press). Site: <https://www.hackaudio.com> | Accessible intro to audio processing algorithms. Code examples on hackaudio.com with video tutorials. MATLAB (Python on GitHub). |
| **Spectral Modeling Synthesis — online notes** (Julius O. Smith, Stanford CCRMA) | REFERENCE (FREE) | Free | <https://ccrma.stanford.edu/~jos/sasp/sasp.html> | Free, comprehensive online book covering everything the Coursera course teaches. Use as the free alternative to the Coursera paid course above. |

**Core topics to master:**

- Spectral processing of audio
- Short-Time Fourier Transform (STFT)
- Spectral analysis and description
- Pitch detection and tracking
- Time-stretching and pitch-shifting
- Audio effects: gain, panning, mixing
- Digital filters applied to audio: EQ, crossover
- Dynamics processing: compression, limiting, gating
- Time-domain effects: delay, chorus, flanger, phaser
- Convolution reverb
- Noise reduction techniques

### 2.2 — Audio Effects Theory

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Audio Effects: Theory, Implementation and Application** by Joshua D. Reiss & Andrew McPherson | BOOK (MAIN) | ~$60 | Publisher search: <https://www.routledge.com/search?kw=Audio+Effects+Reiss+McPherson> · code: see the book's companion page on the publisher site | Practical book explaining audio effects with working C++ code. Use as your structured "course" for effects theory. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **DAFX: Digital Audio Effects** by Udo Zölzer | BOOK (BIB) | ~$60 | Search by title (Wiley) | Classic, more academic reference covering a wide range of effects. |
| **The Computer Music Tutorial** by Curtis Roads | BOOK (BIB) | ~$70 | Search by title (MIT Press) | Massive reference covering all facets of computer music. Describes algorithms in detail. Keep on your shelf forever. |

### 2.3 — Practical DSP Prototyping

Before writing C++ plugins, prototype your ideas quickly in a simpler environment.

#### MAIN MATERIAL

Pick ONE and spend a few weeks building simple synthesizers, effects, and experiments. This builds invaluable intuition before you tackle C++ plugin development.

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **SuperCollider** | Software + language | Free | <https://supercollider.github.io> | Powerful audio programming language. Great for live coding, synthesis, algorithmic composition. **Recommended default choice.** |
| **ChucK** | Software + language | Free | <https://chuck.cs.princeton.edu> | Real-time, strongly-timed audio programming language. Good for learning audio programming concepts. |
| **Csound** | Software + language | Free | <https://csound.com> | One of the oldest and most powerful computer music systems. Huge collection of opcodes. |
| **Pure Data (Pd)** | Software | Free | <https://puredata.info> | Visual programming language for audio — patch cables instead of code. Great for understanding signal flow. |
| **Max/MSP** | Software | ~$399 (free trial) | <https://cycling74.com> | Visual programming. Industry standard for prototyping. |

##### Specific tutorials

| Resource | Tag | Link | Notes |
|---|---|---|---|
| **Nick Collins' SuperCollider Tutorial** | COURSE (FREE) | <https://composerprogrammer.com/teaching.html> | 12-week structured course, free. (Look for the SuperCollider tutorial link on his teaching page.) |
| **Eli Fieldsteel's SuperCollider Tutorials** | VIDEO (FREE) | <https://www.youtube.com/@elifieldsteel> | Excellent video series. |
| **Introduction to Real-Time Audio Programming in ChucK** (Kadenze) | COURSE (FREE) | <https://www.kadenze.com/courses/introduction-to-real-time-audio-programming-in-chuck> | Free; ~48 hours of content. |

---

## LEVEL 3: AUDIO PLUGIN DEVELOPMENT

*"Now we build real audio software."*

**Prerequisites:** Level 1 + Level 2 complete. Comfortable with C++, DSP concepts, and audio effects theory.

**Strategy:** This is where Pirkle's books finally make sense. You've built the foundation — now the "hard" books become accessible.

---

### 3.1 — Your First Plugin (JUCE Framework)

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Official JUCE Audio Plugin Development Course** (by Jan Wilczek, hosted on JUCE) | COURSE (FREE) | Free | Course: <https://juce.com/learn/course> · Author's site: <https://www.thewolfsound.com> | **50+ video lessons, 8 modules.** Takes you from zero to a complete tremolo plugin. Covers: dev environment setup, plugin formats, audio processing, parameters, GUI, testing, distribution. Industry best practices. **Start here.** |
| **The Audio Programmer — YouTube channel** (Joshua Hodge) | VIDEO (FREE) | Free | <https://www.youtube.com/@TheAudioProgrammer> | Excellent JUCE tutorials, live streams, interviews with industry experts. |
| **JUCE Official Tutorials** | REFERENCE (FREE) | Free | <https://juce.com/learn/tutorials> | Built-in JUCE tutorials. Don't skip these. |

**What you'll build first:** A tremolo plugin (amplitude modulation with an LFO). This teaches you the entire plugin development pipeline.

### 3.2 — The Essential Books

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **The Complete Beginner's Guide to Audio Plug-in Development** by Matthijs Hollemans | BOOK (MAIN) | $35 | <https://www.audiodev.blog/beginners-book/> | **If you know nothing about software development, start here.** 473 pages. Explains C++, IDE setup, JUCE, and DSP code from scratch. Lowers the learning curve dramatically. |
| **Creating Synthesizer Plug-Ins with C++ and JUCE** by Matthijs Hollemans | BOOK (MAIN) | $35 | <https://www.audiodev.blog/synth-book> | Step-by-step building of a complete software synthesizer. Explains the theory AND the implementation. Source code on GitHub. |

**Why these first and not Pirkle?** Hollemans' books explain *everything* from scratch, including the C++ and JUCE setup. Pirkle's books assume you already know C++ and jump straight into DSP algorithms. Hollemans is the bridge.

### 3.3 — Pirkle's Books (Now You're Ready)

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Designing Audio Effect Plug-Ins in C++** by Will C. Pirkle | BOOK (MAIN) | ~$65 | Author: <https://www.willpirkle.com> · Publisher search: <https://www.routledge.com/search?kw=Designing+Audio+Effect+Plug-Ins+Pirkle> | Wealth of information on audio-effect DSP algorithms. Explanations can sometimes be confusing — but now that you have DSP fundamentals, you can fill in the gaps. Fully worked plugin examples. |
| **Designing Software Synthesizer Plug-Ins in C++** by Will C. Pirkle | BOOK (MAIN) | ~$65 | Author: <https://www.willpirkle.com> · Publisher search: <https://www.routledge.com/search?kw=Designing+Software+Synthesizer+Plug-Ins+Pirkle> | The synth book. Widely recommended as *the* book for plugin development. Oscillators, filters, envelopes, modulation, all in C++. First edition is slightly easier to read than second. |

> **Community wisdom from the JUCE forum:** *"The book I found helped me the most when I started was Designing Audio Effect Plugins in C++ by Will Pirkle. It does a good job of explaining the fundamentals, and you get to make a large selection of effects. There is plenty of maths if you are that way inclined. I skipped a lot of the maths on my first read, made some fun stuff, and then as I progressed went back and learned a lot of the theory. I still regularly refer to this book 10 years later."*

### 3.4 — More Advanced Plugin Topics

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **JUCE Forum** | COMMUNITY (FREE) | Free | <https://forum.juce.com> | Ask questions, find solutions. Very active and welcoming. |
| **The Audio Programmer Discord** | COMMUNITY (FREE) | Free | Invite link via <https://www.theaudioprogrammer.com> | Smart, friendly people chatting about audio development every day. Beginners through industry professionals. |
| **Audio Developer Conference (ADC) talks** | VIDEO (FREE) | Free | <https://www.youtube.com/@audiodevcon> | Yearly conference. Practical, code-focused talks from industry professionals. |

**Core topics at this level:**

- Plugin formats: VST3, AU, AAX, LV2, CLAP
- Audio processing chain and buffer management
- Real-time audio programming (no memory allocation, no locks, no file I/O in the audio thread)
- Parameter management, automation, presets
- GUI development with JUCE
- Cross-platform concerns (Windows, macOS, Linux)
- Plugin testing (pluginval: <https://github.com/Tracktion/pluginval>)
- Plugin distribution and code signing
- SIMD optimization basics

---

## LEVEL 4: SYNTHESIS & SOUND DESIGN PROGRAMMING

*"Create new sounds from mathematics."*

**Prerequisites:** Level 3 (comfortable building audio plugins in C++/JUCE).

---

### 4.1 — Synthesis Theory & Implementation

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Creating Synthesizer Plug-Ins with C++ and JUCE** (Hollemans) | BOOK (MAIN) | $35 | <https://www.audiodev.blog/synth-book> | If you haven't read this yet, now is the time. Complete synth implementation. |
| **Designing Software Synthesizer Plug-Ins in C++** (Pirkle) | BOOK (MAIN) | ~$65 | <https://www.willpirkle.com> · <https://www.routledge.com/search?kw=Designing+Software+Synthesizer+Plug-Ins+Pirkle> | Deep dive into synth algorithms. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **The Computer Music Tutorial** by Curtis Roads | BOOK (BIB) | ~$70 | Search by title (MIT Press) | Reference for synthesis methods: additive, subtractive, FM, granular, physical modeling, spectral, and more. Not a programming book but describes algorithms in detail. |

**Synthesis methods to implement (in rough order):**

1. **Subtractive Synthesis** — oscillators (saw, square, triangle, noise) → filter → envelope → output
2. **Additive Synthesis** — sum of sinusoids with individual amplitude/phase/frequency control
3. **FM Synthesis** (Frequency Modulation) — carrier + modulator, ratio and index
4. **Wavetable Synthesis** — pre-computed waveforms, interpolation
5. **Granular Synthesis** — grains, windows, time-stretching
6. **Physical Modeling** — Karplus-Strong, waveguide synthesis, digital waveguides
7. **Sampling and Playback** — file reading, time-stretching, pitch-shifting

### 4.2 — Advanced DSP for Audio

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Musimathics Vol. 2** by Gareth Loy | BOOK (BIB) | ~$50 | <https://mitpress.mit.edu/9780262122825/musimathics-volume-2> · search: <https://www.google.com/search?q=Musimathics+Gareth+Loy+MIT+Press> | Math behind digital audio, filtering, Fourier, sound synthesis. |
| **musicdsp.org** | REFERENCE (FREE) | Free | <https://www.musicdsp.org> | Community-contributed collection of DSP algorithms. Great reference for specific building blocks. |
| **Academic papers** (AES Journal, DAFX conference) | Papers | Sometimes free | <https://aes.org> (AES), <https://dafx.de> (DAFX) | Once you're comfortable, start reading papers. Many are free PDFs online. |

---

## LEVEL 5: ADVANCED TOPICS & SPECIALIZATION

*"Choose your path."*

**Prerequisites:** Level 4 complete. You can build audio plugins. Now go deeper in your area of interest.

---

### 5.1 — Real-Time Audio Programming & Optimization

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Awesome Audio DSP** (BillyDM) — sections on optimization, real-time, embedded | REFERENCE (FREE) | Free | <https://github.com/BillyDM/awesome-audio-dsp> (mirror on Codeberg too) | Comprehensive curated resource list. |
| **ADC Talks on Optimization** | VIDEO (FREE) | Free | <https://www.youtube.com/@audiodevcon> | Real-world optimization from industry engineers. |

**Topics:** Lock-free programming, SIMD (SSE, AVX, NEON), multi-threading, memory allocation strategies, cache efficiency, fixed-point arithmetic, compiler optimizations.

### 5.2 — Machine Learning for Audio

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **librosa** (Python library + docs) | REFERENCE (FREE) | Free | <https://librosa.org> | Audio analysis library. Start here for hands-on ML experimentation in Python. |
| **Google Magenta demos + notebooks** | REFERENCE (FREE) | Free | <https://magenta.tensorflow.org> | Practical ML applications in audio. |
| **Demucs (Meta) — music source separation** | REFERENCE (FREE) | Free | <https://github.com/facebookresearch/demucs> | State-of-the-art music source separation. Read + run the code. |

##### BIBLIOGRAPHY REFERENCES

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **ML for Audio Signal Processing** (various Coursera specializations) | COURSE (PAID) | May require payment | Search "Machine Learning for Audio" on <https://www.coursera.org> | Neural networks for audio classification, source separation, speech enhancement. |

### 5.3 — Game Audio Programming

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Wwise** | Middleware | Free (with license) | <https://www.audiokinetic.com/products/wwise> | Industry-standard game audio middleware. Free for non-commercial/educational use. |
| **FMOD** | Middleware | Free (with license) | <https://www.fmod.com> | Other major game audio middleware. Free for personal/non-commercial. |

### 5.4 — Embedded Audio & Hardware

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **Andrew McPherson — C++ Real-Time Audio Programming with Bela** | VIDEO (FREE) | Free | Bela channel: <https://www.youtube.com/@BelaPlatform> · lecture search: <https://www.youtube.com/results?search_query=McPherson+Bela+Real-Time+Audio+C%2B%2B> | 20+ lectures on C++ audio programming using Bela. Based on teaching at Queen Mary University of London. |
| **Bela Platform** | Hardware + software | ~$99 | <https://bela.io> | Embedded platform for real-time audio. Excellent for learning low-latency, hardware-level audio. |

### 5.5 — Music Information Retrieval & Audio Analysis

#### MAIN MATERIAL

| Resource | Tag | Cost | Link | Notes |
|---|---|---|---|---|
| **MIT 6.3020 — Fundamentals of Music Processing** (OCW) | COURSE (FREE) | Free | <https://ocw.mit.edu/search?q=Fundamentals+of+Music+Processing> | Analyzes recorded music using signal processing and optimization. Covers feature extraction, chord recognition, beat tracking. |
| **librosa** | REFERENCE (FREE) | Free | <https://librosa.org> | Audio analysis library. Great for prototyping MIR algorithms. |

---

## SUPPLEMENTARY RESOURCES & COMMUNITIES

### Communities to Join

| Community | Tag | Link | Notes |
|---|---|---|---|
| **The Audio Programmer Discord** | COMMUNITY (FREE) | Invite via <https://www.theaudioprogrammer.com> | Welcoming, beginners through pros. |
| **JUCE Forum** | COMMUNITY (FREE) | <https://forum.juce.com> | The main forum for JUCE-based audio development. |
| **DSPRelated.com Forums** | COMMUNITY (FREE) | <https://www.dsprelated.com/forums> | General DSP discussions. |
| **r/audioengineering** | COMMUNITY (FREE) | <https://www.reddit.com/r/audioengineering> | Broad audio engineering community. |
| **r/DSP** | COMMUNITY (FREE) | <https://www.reddit.com/r/DSP> | Digital signal processing discussions. |
| **r/JUCE** | COMMUNITY (FREE) | <https://www.reddit.com/r/JUCE> | JUCE-specific discussions. |

### Awesome Lists (Bookmark These)

| List | Tag | Link | Notes |
|---|---|---|---|
| **BillyDM/awesome-audio-dsp** | REFERENCE (FREE) | <https://github.com/BillyDM/awesome-audio-dsp> | The most comprehensive curated list of audio DSP resources. |
| **olilarkin/awesome-musicdsp** | REFERENCE (FREE) | <https://github.com/olilarkin/awesome-musicdsp> | Collection of audio DSP code and references. |
| **sudara/awesome-juce** | REFERENCE (FREE) | <https://github.com/sudara/awesome-juce> | JUCE-specific resources. |

### Reference Websites

| Site | Tag | Link | Notes |
|---|---|---|---|
| **audiodev.blog** (Matthijs Hollemans) | REFERENCE (FREE) | <https://www.audiodev.blog> | Excellent blog on audio development. |
| **WolfSound** (Jan Wilczek) | REFERENCE (FREE) | <https://www.thewolfsound.com> | Audio plugin development tutorials and resources. |
| **The Audio Programmer** | REFERENCE (FREE) | <https://www.theaudioprogrammer.com> | Books, courses, tutorials, community. |
| **dspguide.com** | REFERENCE (FREE) | <https://www.dspguide.com> | Steven Smith's free DSP book. |
| **musicdsp.org** | REFERENCE (FREE) | <https://www.musicdsp.org> | DSP code snippets and algorithms. |
| **cppreference.com** | REFERENCE (FREE) | <https://en.cppreference.com> | C++ reference. Essential. |
| **Kadenze** | REFERENCE (FREE) | <https://www.kadenze.com> | Free courses on audio programming (ChucK, etc.). |

---

## RECOMMENDED STUDY SCHEDULE

> Coursera courses below are marked **[PAID]** — assume only the first module is free unless the course page explicitly says otherwise. Free alternatives are noted.

### Phase 1: Foundations (Months 1-4)

- **Months 1-2**: Math (Khan Academy: algebra, trig, complex numbers) + Python basics (CS50x free, edX audit)
- **Months 2-3**: C++ basics (C++ Primer **[BOOK MAIN]** *or* The Cherno videos **[FREE]**) + Physics of sound (MIT OCW 8.03 **[FREE]**)
- **Months 3-4**: Continue C++ + Domain knowledge (REAPER trial, musictheory.net, Andrew Huang videos)

### Phase 2: DSP (Months 5-8)

- **Month 5**: Think DSP (book) **[FREE]** — read cover-to-cover, do the exercises
- **Months 5-6**: dspguide.com **[FREE]** — read alongside Think DSP
- **Month 7**: Audio Signal Processing for Music Applications (Stanford/UPF on Coursera) **[PAID]** OR the free CCRMA online notes by Julius O. Smith **[FREE]**
- **Month 8**: MIT RES.6-007 — Signals and Systems **[FREE]** (Lyons book **[BOOK BIB]** optional, only if you want a deeper textbook on top of Oppenheim)

### Phase 3: Audio Prototyping (Months 9-10)

- **Month 9**: Learn SuperCollider **[FREE]** — Nick Collins' tutorial or Eli Fieldsteel's YouTube series. Build simple synthesizers and effects.
- **Month 10**: Read Hollemans' *Beginner's Plugin Book* (**[BOOK MAIN]**) while following along in code

### Phase 4: Plugin Development (Months 11-16)

- **Month 11**: Official JUCE Course **[FREE]** — build the tremolo plugin
- **Months 12-13**: Hollemans' *Synth Plugin Book* **[BOOK MAIN]** — build a complete synthesizer
- **Months 14-16**: Pirkle's *Synth Book* + Pirkle's *Effects Book* **[BOOK MAIN]** — build multiple synthesizer and effect plugins

### Phase 5: Advanced (Months 17+)

- Pick a specialization from Level 5. Read papers from AES and DAFX. Build your portfolio. Contribute to open-source audio projects.

---

## KEY PRINCIPLES

1. **Don't skip foundations.** The number-one reason people give up on audio programming is trying to read Pirkle without understanding DSP first. Build the foundation.

2. **Learn math in context.** Don't study math in isolation. When you encounter a concept you don't understand (complex numbers, calculus), go study just enough to understand it, then return to audio.

3. **Write code from day one.** Even in Level 0, write small programs. As soon as you can, make them produce sound.

4. **Prototype before implementing.** Use SuperCollider, Python, or Pure Data to test ideas quickly before writing C++.

5. **Read the same material twice.** You'll understand Pirkle's book completely differently the second time. That's normal and expected.

6. **Build projects.** Theory without practice is wasted. Every topic should have a project attached to it.

7. **Join communities.** The Audio Programmer Discord and JUCE Forum are invaluable. Don't learn alone.

8. **Respect the BOOK (MAIN) tag.** Books marked BOOK (MAIN) are the only purchases the curriculum treats as "near-essential" — they replace a free course that doesn't exist. Everything else has a free alternative listed alongside it.

9. **Be patient.** This is a university-level curriculum. It takes years. That's okay. The journey is enjoyable if you let it be.

---

*Last updated: July 2026*
*Curated from research across university curricula, industry recommendations, and community wisdom.*