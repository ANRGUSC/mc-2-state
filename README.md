# Markov Chain Explorer — 2-State

Interactive single-page tool for analyzing a 2-state Markov chain. Enter transition probabilities and instantly see:

- **Steady-state distribution** (π₀, π₁)
- **Coherence time** — expected steps before a state transition (per-state and weighted average)
- **Probability evolution** — P(state j at step n) conditioned on starting in state 0 or state 1
- **Sample trajectory** — a live simulated run showing how smooth or noisy the chain is

## Live Demo

**[mc-2-state.vercel.app](https://mc-2-state.vercel.app)**

## Features

- Dark / neon aesthetic with responsive layout
- Two input modes: enter (p₀₁, p₁₀) or (p₀₁, p₁₁) — the other matrix entries autofill
- Sliders + numeric inputs for precise control
- All math computed analytically (closed-form P^n via eigendecomposition)
- Sample trajectory with resample button and empirical statistics
- Single HTML file — no build step, no dependencies to install

## Usage

Open `markov-explorer.html` in any modern browser, or visit the live demo above.

## Math

For a 2-state chain with transition matrix:

```
P = [[1-p₀₁, p₀₁],
     [p₁₀,   1-p₁₀]]
```

**Steady state:** π₀ = p₁₀/(p₀₁+p₁₀), π₁ = p₀₁/(p₀₁+p₁₀)

**n-step transition probabilities** (λ = 1 − p₀₁ − p₁₀):
- P(Xₙ=0 | X₀=0) = π₀ + π₁·λⁿ
- P(Xₙ=0 | X₀=1) = π₀·(1 − λⁿ)

**Coherence time:** τᵢ = 1/pᵢⱼ (expected geometric waiting time), weighted average τ̄ = π₀τ₀ + π₁τ₁

## License

[PolyForm Noncommercial 1.0.0](LICENSE)
