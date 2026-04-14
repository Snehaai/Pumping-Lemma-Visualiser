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
| a*b* | Regular | ⌊\|s\|/2⌋ | The entire a-block (up to p chars) |
| (ab)+ | Regular | 2 | First "ab" unit (exactly 2 chars) |
| aⁿbⁿ | n (count of a's) | First block of a's — y = one 'a' |
| aⁿbⁿcⁿ | n (count of a's) | First block of a's — y = one 'a' |
| wwᴿ (palindrome) | ⌈|s|/4⌉ × 2 | First two characters |
| aᵖ (prime length) | 2 | First two characters |

**Rule**: y must be placed within the first p characters and must be non-empty. This is derived directly from the lemma's condition |xy| ≤ p. The pumping length p can also be set manually by the user.

---
## How It Functions — Logic Section
 
### 1. Input Parsing
- User selects a language and enters a string (letters a, b, c only)
- Optional: user can set their own pumping length p, or click **Auto** to compute it
 
### 2. Pumping Length (p) Computation
- **aⁿbⁿ / aⁿbⁿcⁿ**: p = number of a's in the input string
- **wwᴿ**: p = ⌈|s|/4⌉ × 2 (ensures y falls in the first half)
- **aᵖ (prime)**: p = 2 (minimal, sufficient to demonstrate)
- **a*b***: p = ⌊|s|/2⌋
- **(ab)+**: p = 2 (length of one "ab" unit)
 
### 3. String Decomposition
- `xLen` and `yLen` are computed per language based on p
- `x = s[0 .. xLen)`, `y = s[xLen .. xLen+yLen)`, `z = s[xLen+yLen ..]`
- Always guarantees: |y| ≥ 1 and |xy| ≤ p
 
### 4. Pumping
- User adjusts i (0, 1, 2, 3 … no upper limit)
- Result string = x + yⁱ + z (i repetitions of y)
- The validate() function checks if the pumped string is still in the language
 
### 5. Verdict Logic
- **Non-regular language + pumped string ∉ L**: Contradiction found — language proved NOT regular
- **Non-regular language + pumped string ∈ L**: Still in language, try a different i
- **Regular language**: Pumped string always stays in L regardless of i — confirms regularity
 
### 6. Formal Proof Generation
- After each run, a 5-step formal proof is generated automatically
- Proof updates live as you change the pump count i
- Steps: Assume regular → Choose s → Adversary splits → Pump → Contradiction (or confirmation)
 
### 7. Animate Pumping
- Clicking **▶ Animate Pumping** auto-increments i from 1 to 8 at 700ms intervals
- The tape segment pulses visually on each pump step
- Click **■ Stop** to halt animation at any time
 
---

## Features

- **Theory box** — explains the Pumping Lemma statement and proof-by-contradiction method
- **6 languages** — 4 non-regular + 2 regular (see table above)
- **Adjustable pumping length p** — set manually or compute automatically
- **Visual tape decomposition** — colour-coded x (blue) · y (terracotta/green) · z (green) segments
- **Unlimited pump counter** — increment i as high as needed, no cap
- **Animate pumping** — auto-steps through i=1 to i=8 with tape pulse animation
- **Live verdict** — instantly shows if the pumped string is in or out of the language
- **Formal proof panel** — 5-step proof generated and updated live after every analysis
- **Rule badges** — displays |xy| ≤ p and |y| ≥ 1 conditions visually
- **Stats panel** — string length, p, current i, pumped string length


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

### Regular Languages
 
#### 5. a*b*
Any number of a's followed by any number of b's. Example: `aaabb`, `b`, `aaa`.
y is chosen from the a-block. Pumping changes the a-count — still matches a*b*. **Always in L.**
 
#### 6. (ab)+
One or more repetitions of the pair "ab". Example: `ab`, `ababab`.
y = "ab" (one full unit). Pumping adds more "ab" units — still matches (ab)+. **Always in L.**

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
