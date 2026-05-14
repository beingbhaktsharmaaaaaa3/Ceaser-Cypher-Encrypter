# 🔐 CipherLab — Caesar Cipher Analysis Suite

> **CEH Edition** · A browser-based cryptography lab for learning, practicing, and attacking Caesar ciphers — no installation required.

---

## 📋 Table of Contents

- [What Is This?](#what-is-this)
- [Quick Start](#quick-start)
- [Feature Overview](#feature-overview)
- [Tab Guide](#tab-guide)
  - [Cipher Tab](#1--cipher-tab)
  - [Brute Force Tab](#2--brute-force-tab)
  - [Frequency Analysis Tab](#3--frequency-analysis-tab)
  - [Education Tab](#4--education-tab)
  - [History Tab](#5--history-tab)
- [Keyboard Shortcuts](#keyboard-shortcuts)
- [Examples](#examples)
- [CEH Learning Notes](#ceh-learning-notes)
- [Tech Details](#tech-details)
- [FAQ](#faq)

---

## What Is This?

**CipherLab** is a single-file, zero-dependency HTML tool that turns your browser into a full Caesar cipher cryptography lab. It was built with CEH (Certified Ethical Hacker) learners in mind, covering encryption, decryption, brute force, frequency analysis, and classical attack simulation — all in one place.

Open `cipherlab.html` in any browser. That's it.

---

## Quick Start

```
1. Download cipherlab.html
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Type text in the Cipher tab
4. Hit Encrypt or just start typing — output appears in real time
```

No server. No npm. No Python. Just one `.html` file.

---

## Feature Overview

| # | Feature | Where |
|---|---------|--------|
| 1 | Real-time encrypt / decrypt | Cipher tab |
| 2 | Shift slider (1–25) + arrow buttons | Cipher tab |
| 3 | Preserve / Upper / Lower case toggle | Cipher tab |
| 4 | Special chars, spaces, numbers preserved | Cipher tab |
| 5 | Copy input / Copy output buttons | Cipher tab |
| 6 | Character counter | Cipher tab |
| 7 | .txt file drag & drop support | Cipher tab |
| 8 | Save output as TXT / CSV / LOG | Cipher tab |
| 9 | Alphabet mapping visualization | Cipher tab |
| 10 | Brute force — all 25 shifts at once | Brute Force tab |
| 11 | English detection highlight (auto-score) | Brute Force tab |
| 12 | Known Plaintext Attack simulator | Brute Force tab |
| 13 | Letter frequency bar chart | Freq Analysis tab |
| 14 | English baseline overlay for comparison | Freq Analysis tab |
| 15 | Auto-suggest shift from frequency | Freq Analysis tab |
| 16 | Educational reference (history, algorithm, weaknesses) | Education tab |
| 17 | CEH exam callout | Education tab |
| 18 | Operation history (last 20 sessions) | History tab |
| 19 | Real-time operation log (timestamped) | Log panel |
| 20 | Export operation log as .log file | Cipher tab |
| 21 | Keyboard shortcuts | Global |
| 22 | Light / Dark theme toggle | Header |
| 23 | Matrix rain background (subtle) | Visual |
| 24 | Fade-in panel animations | Visual |
| 25 | Fully responsive (mobile + desktop) | Global |

---

## Tab Guide

### 1 · Cipher Tab

The main workspace. Everything you need to encrypt or decrypt text lives here.

**Mode Toggle**

```
[ 🔒 Encrypt ]  [ 🔓 Decrypt ]
```

Click either button to switch modes. Labels on the text boxes update automatically.

**Shift Key**

- Use the **◀ ▶** arrow buttons to increment/decrement the shift one step at a time.
- Drag the **slider** for quick visual selection (range: 1–25).
- The big green number shows the current shift value.

**Case Mode**

| Option | Behavior |
|--------|----------|
| `Preserve` | Uppercase stays uppercase, lowercase stays lowercase |
| `ALL UPPER` | All output letters are uppercase |
| `all lower` | All output letters are lowercase |

**Text Areas**

- Left box: your plaintext (or ciphertext if decrypting).
- Right box: the result — updates live as you type.
- Output is read-only to prevent accidental edits.

**File Input**

- Drag and drop any `.txt` file onto the drop zone or the left text box.
- Or click the drop zone to open a file browser.
- File contents load directly into the input box.

**Action Buttons**

| Button | Action |
|--------|--------|
| `🔒 Encrypt` / `🔓 Decrypt` | Process text and save to history |
| `Copy Input` | Copy the left box to clipboard |
| `Copy` (on output) | Copy the right box to clipboard |
| `✕ Clear` | Wipe both boxes and reset |
| `⬇ TXT` | Download output as a `.txt` file |
| `⬇ CSV` | Download as `.csv` with shift, mode, input, output columns |
| `⬇ LOG` | Download the operation log as a `.log` file |

**Alphabet Mapping**

Below the text boxes, a live visualization shows which letter maps to which for the current shift and mode.

```
A  B  C  D  E  F  G  ...
↕  shifts by 3 positions
D  E  F  G  H  I  J  ...
```

---

### 2 · Brute Force Tab

Tries all 25 possible shifts against your input text simultaneously.

**How to use:**

1. Enter ciphertext in the Cipher tab.
2. Switch to Brute Force tab.
3. All 25 decryptions appear instantly.
4. Click any row to apply that shift — you'll be taken back to the Cipher tab with the result.

**English Detection**

When the toggle is ON, rows that look like readable English are highlighted with a green border. A percentage score shows how many words matched common English vocabulary.

```
 3  KHOOR ZRUOG! 123          ← not highlighted
 ✓  HELLO WORLD! 123   82%    ← highlighted (likely English)
```

> Toggle "Highlight likely English" off if you're working with non-English text.

**Known Plaintext Attack**

If you know one word from the original plaintext and its encrypted form:

1. Enter the plaintext word (e.g. `hello`)
2. Enter the ciphertext equivalent (e.g. `khoor`)
3. Click **Run Known Plaintext Attack**
4. The tool deduces the shift and applies it automatically

```
Plaintext:   hello
Ciphertext:  khoor
→ Shift found: K = 3 ✓
```

---

### 3 · Frequency Analysis Tab

Shows a bar chart of letter frequencies in your input text compared to standard English.

**Reading the chart:**

- **Green bars** = your text's letter frequencies
- **Dark bars** = expected English frequency baseline (E=12.7%, T=9.1%, A=8.2%, …)

**Attack logic:**

In English, `E` is the most common letter. In a Caesar-encrypted English text, the most frequent ciphertext letter corresponds to `E`. The tool calculates the shift automatically:

```
Most frequent letter in your text: X (9.4%)
Suggested shift key: 19
[ Apply Shift 19 ] ← button appears automatically
```

Click the button to jump to the Cipher tab with that shift applied.

---

### 4 · Education Tab

A quick-reference reference panel covering:

- **History** — Julius Caesar, Augustus Caesar, ancient use
- **Algorithm** — encrypt/decrypt formulas with examples
- **Weaknesses** — why it's broken and how
- **Attack Methods** — brute force, frequency analysis, known plaintext
- **Related Ciphers** — ROT13, Vigenère, Atbash, Affine
- **Fun Facts** — interesting trivia
- **CEH Exam Note** — what the exam actually tests and why it matters

---

### 5 · History Tab

Stores your last 20 encrypt/decrypt operations for the current session.

Each row shows:
- Timestamp (HH:MM)
- Mode badge (ENC / DEC)
- Input preview
- Output preview
- Shift key used

**Click any row** to reload that operation into the Cipher tab — useful for comparing results or revisiting a previous session.

Use the **Clear History** button to wipe all records.

> History is session-only. Closing the browser tab clears it.

---

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl + E` | Switch to Encrypt mode |
| `Ctrl + D` | Switch to Decrypt mode |
| `Ctrl + B` | Jump to Brute Force tab |
| `Ctrl + Shift + C` | Copy output to clipboard |
| `Ctrl + X` | Clear all fields |
| `Alt + ↑` | Shift key + 1 |
| `Alt + ↓` | Shift key − 1 |
| `?` | Open keyboard shortcut reference |
| `Esc` | Close modal |

> Shortcuts are disabled when typing inside text fields so they don't interfere with normal input.

---

## Examples

### Basic encryption

```
Input:   HELLO WORLD! 123
Shift:   3
Mode:    Encrypt
Output:  KHOOR ZRUOG! 123
```

Numbers, spaces, and symbols are untouched.

### Decryption

```
Input:   KHOOR ZRUOG! 123
Shift:   3
Mode:    Decrypt
Output:  HELLO WORLD! 123
```

### Case preservation

```
Input:   Hello World
Shift:   5
Output:  Mjqqt Btwqi   ← case preserved
```

### ROT13 (shift 13)

```
Input:   Hello
Shift:   13
Output:  Uryyb

Encrypt again with shift 13:
Output:  Hello         ← self-inverse
```

### Brute force — find readable output

```
Ciphertext: YMJWJ NX FQ\FBX F \FB

Shift  1: XLIQE MW EK\EAX E \EA
Shift  4: THERE IS AL\AYS A \AY   ← ✓ readable English, highlighted
...
```

---

## CEH Learning Notes

This tool covers concepts tested in the **CEH v13** domain on **Cryptography**:

| Topic | Where to practice |
|-------|-------------------|
| Substitution ciphers | Cipher tab — encrypt any text |
| Key space exhaustion | Brute Force tab — see all 25 keys instantly |
| Frequency analysis attack | Frequency Analysis tab |
| Known plaintext attack | Brute Force tab → KPA section |
| Ciphertext-only attack | Freq Analysis + Brute Force combined |
| Why Caesar is broken | Education tab |
| Comparison to AES key space | Education tab → CEH callout |

**Key formulas to remember for the exam:**

```
Encrypt:  C = (P + K) mod 26
Decrypt:  P = (C − K + 26) mod 26

Key space: 25 keys (trivially brute-forceable)
```

---

## Tech Details

| Property | Value |
|----------|-------|
| File type | Single `.html` file |
| Dependencies | Google Fonts (JetBrains Mono, Syne) — loaded from CDN |
| Framework | Vanilla JS, no libraries |
| Browser support | Chrome 90+, Firefox 88+, Edge 90+, Safari 15+ |
| Offline use | Works offline except fonts (will fall back to monospace) |
| File size | ~35 KB |
| Data storage | Session memory only — nothing is sent anywhere |

---

## FAQ

**Does this send my text anywhere?**
No. Everything runs entirely in your browser. No server, no network requests, no analytics.

**Can I use it offline?**
Yes. The tool works fully offline. Fonts will fall back to your system monospace font if Google Fonts can't load.

**Why does the brute force always show "decrypt" results?**
Brute force tests all possible decryptions of your input — that's the point. You're looking for whichever shift produces readable plaintext.

**What does the English percentage score mean?**
It's the proportion of words in that decoded output that appear in a list of common English words. Higher % = more likely to be real English text.

**Can I encrypt non-English text?**
Yes. The tool encrypts/decrypts all Latin alphabet characters regardless of language. The English detection feature won't highlight non-English results, but everything else works normally.

**Can I use this for a CTF?**
Absolutely. The brute force + frequency analysis combo is the standard approach for classic cipher challenges in CTF competitions.

---

## Credits

Built as a CEH learning project.  
Tool concept and design by **Bhoku**.  
Single-file HTML — share, fork, or modify freely.

---

*CipherLab · Caesar Cipher Analysis Suite · CEH Edition*
