# Random-Attractors-Found-using-Lyapunov-Exponents
This project is based on Paul Bourke’s Random Attractors Found using Lyapunov Exponents (2001), with contributions by Philip Ham and Johan Bichel Lindegaard. The original code and methodology were reused, with only minor parameter adjustments and small modifications to adapt it for this repository.


# Random Chaotic Attractors (Lyapunov Search)

Python port of Paul Bourke’s `gen.c` for generating random chaotic attractors using **Lyapunov exponents**.

Original concept and C implementation:
Paul Bourke – *Random Attractors Found Using Lyapunov Exponents* (October 2001)

Python implementation:
Johan Bichel Lindegaard – [http://johan.cc](http://johan.cc)

This version includes small parameter adjustments and minor modifications to explore a slightly wider coefficient range and generate more examples.

---

## Overview

This project searches for **2D quadratic chaotic systems** of the form:

```
x(n+1) = a0 + a1*x + a2*x² + a3*x*y + a4*x²*y + a5*y²
y(n+1) = b0 + b1*y + b2*y² + b3*y*x + b4*y²*x + b5*x²
```

Each coefficient is randomly selected within a defined range.
The system is iterated for a large number of steps and evaluated using the **largest Lyapunov exponent**.

If:

* λ > 0 → The system is chaotic (image saved)
* λ < 0 → The system converges to a fixed or periodic attractor
* System diverges → Discarded

Only chaotic systems are rendered and saved as images.

---

##  How It Works

1. Randomly generate coefficients `a0..a5`, `b0..b5`
2. Initialize a small perturbation between two nearby points
3. Iterate the quadratic map (`100,000` iterations)
4. Compute the Lyapunov exponent
5. If chaotic:

   * Compute bounding box
   * Normalize coordinates
   * Render to 512x512 PNG
   * Save as `attractor_N.png`

---

## Parameters

```python
MAXITERATIONS = 100000
NEXAMPLES = 2000
Coefficient range: [-2.5, 2.5]
Image size: 512x512
```

Modifications from original:

* Slightly expanded coefficient range
* Increased number of attractor attempts
* Minor structural adjustments in quadratic terms

---

## Requirements

* Python 3.x
* Pillow

Install dependencies:

```bash
pip install pillow
```

---

## Usage

Simply run:

```bash
python attractor.py
```

The script will:

* Search for chaotic systems
* Print Lyapunov exponents
* Save generated attractors as PNG images

---

##  References

* Paul Bourke – Random Attractors (2001)
* Devaney – *An Introduction to Chaotic Dynamical Systems*
* Peitgen, Jürgens, Saupe – *Chaos and Fractals*
* Feigenbaum – Universal Behavior in Nonlinear Systems

---

##  License

This project builds upon publicly available work by Paul Bourke and Johan Bichel Lindegaard.
Please credit original authors if reusing or modifying this code.

