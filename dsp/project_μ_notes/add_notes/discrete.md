Read further <https://en.wikipedia.org/wiki/Discrete_mathematics/>

In mathematics and signal processing, the word **discrete** comes directly from the Latin word **_discretus_**, which is the past participle of _discernere_—meaning **"to separate," "to distinguish," or "to set apart."**

When we talk about **discrete-time**, we literally mean **"separated time."**

---

## Continuous Time vs. Discrete Time

To see why the name fits so well, compare it with its counterpart:

### 1. Continuous-Time (Flowing)

- **Mathematical Set:** Real numbers $\mathbb{R}$
- **Analogy:** A smooth, unbroken river or a analog clock hand gliding continuously.
- **Property:** Between any two instants of time $t_1$ and $t_2$, there are **infinitely many** intermediate time points—no matter how close $t_1$ and $t_2$ are. Time flows seamlessly without gaps.

### 2. Discrete-Time (Separated)

- **Mathematical Set:** Integers $\mathbb{Z}$
- **Analogy:** A digital clock ticking second by second, or footsteps on stepping stones.
- **Property:** Points in time are **distinct, isolated, and separated by gaps**. Between index $n = 1$ and $n = 2$, there is no $n = 1.5$ in the domain of $x[n]$. The points exist as separate entities.

---

## A Common Confusion: _Discrete_ vs. _Discreet_

Because they sound identical in English, these two words often get confused:

- **Discreet** (ee): Modest, cautious, or keeping secrets (e.g., _"be discreet about this information"_).
- **Discrete** (ete): Separate, distinct, or composed of individual parts (e.g., _"discrete data points"_).

Both come from the same Latin root _discernere_ (to separate), but **discreet** evolved toward "separate good judgment from bad" (circumspect), while **discrete** kept the physical/mathematical meaning of "individually separate."

---

## What Discrete-Time Means in Practice

When a system operates in **discrete-time**, it means time is reduced to a **countable sequence of events** indexed by integers $n \in \{\dots, -2, -1, 0, 1, 2, \dots\}$.

```
Continuous-Time t:   ----------------------------> (Infinite points between 0 and 1)
                     0                          1

Discrete-Time n:     *          *          *    -> (Isolated points: n=0, n=1, n=2)
                    n=0        n=1        n=2

```

In $x[n]$, time is no longer a physical variable measuring seconds—it is simply a step counter. The physical time $T$ between step $n$ and step $n+1$ is fixed, but the signal $x[n]$ only cares about the **index sequence**, treating each sample point as an isolated, distinct snapshot.
