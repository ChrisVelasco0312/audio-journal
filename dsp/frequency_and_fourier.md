# Applied DSP: Frequency & Fourier Series

> Based on Youngmoo Kim's lecture: [Applied Digital Signal Processing - What is Frequency?](https://www.youtube.com/watch?v=IOrSdklyJ1k)

---

## Core Concepts

### Frequency & Period

For something to have **frequency**, there must be something that occurs *frequently*. A signal with repeating structure is called **periodic** — the repeating section is one **period** ($T$).

$$
f = \frac{1}{T}
$$

- **Period ($T$)**: time for one complete cycle (seconds)
- **Frequency ($f$)**: cycles per second, measured in **Hertz** (Hz)
- Named after Heinrich Hertz, 19th century physicist

> **Math Refresher:** [Reciprocal (inverse relationship)](https://www.khanacademy.org/math/precalculus/x9e81a4f98389efdf:complex/x9e81a4f98389efdf:complex-numbers-intro/v/complex-numbers-intro)

---

### Sinusoids: The Building Blocks

The simplest repetition is circular motion. Measuring the y-coordinate of a dot traveling around a circle at constant speed gives us the **sine function**.

If the dot circles every second → frequency of 1 Hz → $\sin(2\pi t)$

**Key insight:** Sine and cosine are the same function, just shifted by a quarter period. They are **pure frequencies** — the building blocks of all periodic behavior.

Since a sinusoid has exactly one frequency, **sinusoids and frequency are interchangeable concepts**.

> **Math Refresher:**
> - [Basic Trigonometry (Khan Academy)](https://www.khanacademy.org/math/trigonometry/basic-trigonometry/basic_trig_ratios/v/basic-trigonometry)
> - [Sine, Cosine, Tangent (Math is Fun)](https://www.mathsisfun.com/sine-cosine-tangent.html)
> - [Sine waves visualized (3Blue1Brown)](https://www.youtube.com/watch?v=IkdOMLXNjCA)

---

### Human Hearing Range

- Average perception: **20 Hz** to **20,000 Hz** (20 kHz)
- Dogs and bats hear much higher frequencies
- Aging reduces high-frequency perception

---

## Fourier's Breakthrough

### The Claim (1822)

Joseph Fourier made an outrageous claim:

> *Any periodic signal can be built from sinusoids that are **harmonics** (integer multiples) of a **fundamental frequency** ($f_0 = 1/T$).*

This was controversial because many periodic signals look nothing like sinusoids — how could they be composed of them?

### The Answer: Addition

Different sinusoids **add together** to form more complex periodic signals, but only at integer multiples of the fundamental frequency.

**Example:** A square wave (which looks nothing like a sinusoid) is actually:

$$
\text{square}(t) = \sin(2\pi f_0 t) + \frac{1}{3}\sin(2\pi \cdot 3f_0 t) + \frac{1}{5}\sin(2\pi \cdot 5f_0 t) + \ldots
$$

Infinite odd harmonics → perfect square wave.

> **Math Refresher:**
> - [Fourier Series (Math is Fun)](https://www.mathsisfun.com/calculus/fourier-series.html) — excellent interactive examples
> - [But what is a Fourier series? (3Blue1Brown)](https://www.youtube.com/watch?v=r6sGWTCMz2k) — best visual explanation
> - [Fourier Series Intro (Khan Academy)](https://www.khanacademy.org/science/electrical-engineering/ee-signals/ee-fourier-series/v/ee-fourier-series-intro)

---

### The Fourier Series Equation

The signal $x(t)$ is expressed as a sum of frequency components:

$$
x(t) = \sum_{k=-\infty}^{\infty} c_k \cdot e^{j2\pi k f_0 t}
$$

Where:
- $f_0$ = fundamental frequency (inverse of period)
- $c_k$ = weight (contribution) of frequency $k \cdot f_0$
- $e^{j2\pi k f_0 t}$ = complex sinusoid at frequency $k \cdot f_0$

### Computing the Weights

Fourier provides a way to compute $c_k$:

$$
c_k = \frac{1}{T} \int_0^T x(t) \cdot e^{-j2\pi k f_0 t} \, dt
$$

**Intuition:** Multiply the signal by each frequency and integrate over one period — this extracts how much of that frequency is present.

> **Math Refresher:**
> - [Integration basics (Khan Academy)](https://www.khanacademy.org/math/ap-calculus-ab/ab-integration-new/ab-4-2/v/definite-integrals)
> - [What is integration? (3Blue1Brown)](https://www.youtube.com/watch?v=rG5Xv7NqjZY)

---

## Euler's Formula

Euler's formula allows us to break complex exponentials into cosine and sine terms:

$$
e^{j\theta} = \cos(\theta) + j\sin(\theta)
$$

This connects:
- **Exponential growth/rotation** ($e^{j\theta}$)
- **Circular motion** (cosine = x-coordinate, sine = y-coordinate)

**Why it matters for DSP:** It lets us rewrite the Fourier series in terms of real-valued sine and cosine components ($a_k$ for cosine, $b_k$ for sine).

> **Math Refresher:**
> - [Euler's Formula (Math is Fun)](https://www.mathsisfun.com/algebra/eulers-formula.html) — step-by-step derivation
> - [Intuitive Understanding (BetterExplained)](https://betterexplained.com/articles/intuitive-understanding-of-eulers-formula/)
> - [Euler's Formula (3Blue1Brown Lockdown Math)](https://3blue1brown-website.vercel.app/lessons/ldm-eulers-formula/)

---

## Physical Significance: Standing Waves

Real physical systems (guitar strings, air columns) vibrate in specific **modes** or **standing waves**. These modes are sinusoidal — each is a harmonic of the fundamental frequency.

When you pluck a guitar string, **all modes happen simultaneously**. The resulting motion is a Fourier series of those standing waves.

This is why Fourier analysis is fundamental:
- Sound and musical instruments
- Geological movement
- Orbits of celestial bodies
- Signal processing everywhere

> **Math Refresher:**
> - [Standing waves (Khan Academy)](https://www.khanacademy.org/science/physics/mechanical-waves-and-sound/standing-waves/v/standing-waves-on-a-string)
> - [Harmonics (Physics Classroom)](https://www.physicsclassroom.com/class/sound/Lesson-4/Nodes-and-Antinodes)

---

## Resources

### Primary
- [Video Lecture](https://www.youtube.com/watch?v=IOrSdklyJ1k) — Youngmoo Kim, Applied DSP
- [Fourier Series Visualization](https://www.mathsisfun.com/calculus/fourier-series.html) — Interactive examples

### Math Foundations
| Topic | Resource |
|-------|----------|
| Trigonometry | [Khan Academy - Trig](https://www.khanacademy.org/math/trigonometry) |
| Sinusoids | [Math is Fun - Sine/Cosine](https://www.mathsisfun.com/sine-cosine-tangent.html) |
| Integration | [Khan Academy - Integration](https://www.khanacademy.org/math/ap-calculus-ab) |
| Euler's Formula | [BetterExplained](https://betterexplained.com/articles/intuitive-understanding-of-eulers-formula/) |
| Fourier Series | [3Blue1Brown](https://www.youtube.com/watch?v=r6sGWTCMz2k) |
| Complex Numbers | [Khan Academy - Complex](https://www.khanacademy.org/math/algebra2/x2ec2f6f830c9fb89:complex) |

### Next Steps
- [Next video in series](https://www.youtube.com/watch?v=IOrSdklyJ1k&list=PLzH6jRbS4rMQ8aE7LyGWJvQfLzHc7rTfL)
- [DSP Textbook (Oppenheim)](https://www.amazon.com/Discrete-Time-Signal-Processing-3rd/dp/0131988425)
