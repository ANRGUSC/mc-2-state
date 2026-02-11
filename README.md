# Markov Chain Explorer — 2-State

**Author: Bhaskar Krishnamachari (USC)**
*Built with assistance from Claude Code*

Interactive single-page tool for analyzing a 2-state Markov chain. Enter transition probabilities and instantly see:

- **Steady-state distribution** (π₀, π₁)
- **Coherence time** — expected steps before a state transition (per-state and weighted average)
- **Probability evolution** — P(state j at step n) conditioned on starting in state 0 or state 1
- **Sample trajectory** — a live simulated run showing how smooth or noisy the chain is

Also includes a comprehensive **tutorial page** with KaTeX-rendered derivations covering:

- Transition matrices and the Chapman–Kolmogorov equation
- Eigendecomposition and closed-form k-step transition probabilities
- Steady-state distribution derivation
- Coherence time and sojourn time distributions
- Autocorrelation structure and the positive correlation condition (p₁₁ ≥ p₀₁)

## Live Demo

**[mc-2-state.vercel.app](https://mc-2-state.vercel.app)**

## Features

- Dark / neon aesthetic with responsive layout
- Two input modes: enter (p₀₁, p₁₀) or (p₀₁, p₁₁) — the other matrix entries autofill
- Sliders + numeric inputs for precise control
- All math computed analytically (closed-form Pⁿ via eigendecomposition)
- Sample trajectory with resample button and empirical statistics
- In-depth tutorial with full derivations rendered in KaTeX
- Single HTML files — no build step, no dependencies to install

## Usage

Open `index.html` in any modern browser, or visit the live demo above. Click "Tutorial & Derivations" for the full theory.

## Math

For a 2-state chain with transition matrix:

```
P = [[1-p₀₁, p₀₁],
     [p₁₀,   1-p₁₀]]
```

**Steady state:** π₀ = p₁₀/(p₀₁+p₁₀), π₁ = p₀₁/(p₀₁+p₁₀)

**n-step transition probabilities** (λ = 1 − p₀₁ − p₁₀):
- P(Xₙ=j | X₀=i) = πⱼ + (δᵢⱼ − πⱼ)·λⁿ

**Autocorrelation:** ρ(k) = λᵏ

**Coherence time:** τᵢ = 1/pᵢⱼ (expected geometric waiting time), weighted average τ̄ = π₀τ₀ + π₁τ₁

**Positive correlation:** p₁₁ ≥ p₀₁ (equivalently λ ≥ 0)

## License

[PolyForm Noncommercial 1.0.0](LICENSE)
