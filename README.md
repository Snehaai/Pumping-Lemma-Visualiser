# Pumping Lemma Visualiser Web App
### TAFL Visualization Assignment — Topic 6

By Sneha Manohar (2023UCA1930)

---

## Live Link

https://snehaai.github.io/Pumping-Lemma-Visualiser/

Deployed on GitHub Pages. Directly accessible via link.

---

An interactive web application that visually demonstrates the **Pumping Lemma for Regular Languages** — a fundamental theorem in Theory of Automata and Formal Languages (TAFL) used to prove that certain languages are *not regular*.


---

## What Is the Pumping Lemma?

The Pumping Lemma states:

> If a language **L** is regular, then there exists a pumping length **p** such that any string **s ∈ L** with |s| ≥ p can be split into three parts **s = xyz** where:
> 1. |y| ≥ 1 (y is non-empty)
> 2. |xy| ≤ p (the split happens early in the string)
> 3. For all i ≥ 0, **xyⁱz ∈ L** (pumping y any number of times stays in the language)

If **any** pumped string falls outside the language, then **L is NOT regular**.

---

## How the String Is Split (Not Random!)

The decomposition follows strict Pumping Lemma rules — it is **deterministic, not random**:

| Language | Pumping Length p | Where y comes from |
|---|---|---|
| aⁿbⁿ | n (count of a's) | First block of a's — y = one 'a' |
| aⁿbⁿcⁿ | n (count of a's) | First block of a's — y = one 'a' |
| wwᴿ (palindrome) | ⌈|s|/4⌉ × 2 | First two characters |
| aᵖ (prime length) | 2 | First two characters |

**Rule**: y must be placed within the first p characters and must be non-empty. This is derived directly from the lemma's condition |xy| ≤ p.

---

## Features

- **4 pre-built languages** — aⁿbⁿ, aⁿbⁿcⁿ, palindromes (wwᴿ), prime-length strings (aᵖ)
- **Visual tape decomposition** — colour-coded x (blue) · y (terracotta) · z (green) segments
- **Interactive pump control** — increment/decrement i from 0 to 8, string updates live
- **Live verdict** — instantly tells whether the pumped string is still in the language
- **Rule badges** — shows |xy| ≤ p and |y| ≥ 1 conditions are satisfied
- **Step-by-step explanation** — each language explains *why* pumping breaks it
- **Stats panel** — string length, pumping length p, current i, pumped string length


---

## Languages Supported

### 1. aⁿbⁿ
Strings with exactly n a's followed by n b's. Example: `aabb`, `aaabbb`.
Pumping breaks it because the y segment (from the a-block) adds more a's without adding b's.

### 2. aⁿbⁿcⁿ
Strings with equal a's, b's, and c's. Example: `aabbcc`.
Pumping the a-block unbalances all three counts.

### 3. wwᴿ (Palindromes)
Strings over {a,b} that read the same forwards and backwards. Example: `abba`, `aabbaa`.
Pumping the start of the string makes the left side longer, destroying the palindrome property.

### 4. aᵖ (Prime Length)
Strings of all a's whose length is a prime number. Example: `aa` (2), `aaa` (3), `aaaaa` (5).
If length q is prime, pumped length q + (i−1)·|y| is generally composite.

---

## Tech Stack

| Technology | Purpose |
|---|---|
| HTML5 | Structure |
| CSS3 | Styling, animations, layout |
| Vanilla JavaScript | All logic — no frameworks |
| Google Fonts (Syne + JetBrains Mono) | Typography |

---


*TAFL Visualization Assignment · Topic 6 — Pumping Lemma Demonstration Tool*
