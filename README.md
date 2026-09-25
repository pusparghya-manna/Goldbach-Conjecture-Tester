# Goldbach Conjecture Tester

A static, single-file website that tests the **Goldbach Conjecture** — the claim (made by Christian Goldbach in a 1742 letter to Euler) that every even number greater than 2 can be written as the sum of two prime numbers.

Enter any even number and the site searches for a prime pair that sums to it, entirely in your browser. No servers, no build step, no dependencies.

Designed & developed by **Pusparghya**.

## Features

- **Instant testing** — enter any even number from 4 up to 999,999,999,999 and get the first prime pair `(a, b)` with `a + b = n`
- **All-pairs mode** — list every decomposition for numbers up to 200,000 (e.g. 100 = 3 + 97 = 11 + 89 = 17 + 83 = 29 + 71 = 41 + 59 = 47 + 53)
- **First-pair mode** — mirrors the original program's behaviour exactly: stop at the first pair found
- **Input validation** — odd numbers, values ≤ 2, and non-integer input are rejected with a clear message
- **Session log** — keeps a running history of your recent tests, with candidate counts and timings
- **Dark / light theme** — follows your system preference automatically
- **Responsive** — works on desktop and mobile
- **Zero dependencies** — one HTML file; the only external requests are Google Fonts

## How it works

The page is a faithful browser conversion of a small Python CLI program. The logic is preserved line for line:

1. **Validate input** — the number must be even and greater than 2.
2. **Iterate candidates** — `a` runs from 2 up to `n / 2` (beyond the halfway point, pairs only repeat in mirror order).
3. **Compute the partner** — for each candidate, `b = n − a`.
4. **Test primality** — trial division: after handling 2 and the even numbers, divide `a` and `b` by every odd integer up to their square root. If nothing divides, it's prime.

The first `(a, b)` found where both are prime is the answer. In first-pair mode the search stops there, exactly like the original script's `break`.

### Input limits

| Mode | Valid range |
|---|---|
| First pair | even integers, 4 – 999,999,999,999 |
| All pairs | even integers, 4 – 200,000 |

The limits keep the search snappy with trial division (≈ √n work per primality test).

## Project structure

```
.
├── goldbach-conjecture-tester.html   # the entire site (HTML + CSS + JS)
└── README.md
```

## Tech

- Plain HTML, CSS, and vanilla JavaScript — no framework, no build tooling
- [Instrument Serif](https://fonts.google.com/specimen/Instrument+Serif), [Crimson Pro](https://fonts.google.com/specimen/Crimson+Pro) & [JetBrains Mono](https://fonts.google.com/specimen/JetBrains+Mono) via Google Fonts (with system fallbacks)
- All computation happens client-side; nothing is sent anywhere

## Background

The Goldbach conjecture is one of the oldest unsolved problems in number theory. It has been verified computationally for every even number up to 4 × 10¹⁸, and no counterexample has ever been found — yet no proof exists either. This site lets you check a few cases yourself.
