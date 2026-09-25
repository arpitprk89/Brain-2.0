** Brain 2.0 — A Bayesian Model of Student Cognitive Load

**Live demo:** *(host `index.html` on GitHub Pages and link it here)*

## What it is

Brain 2.0 is a small self-reflection tool for students. Each day, it asks five simple questions (study hours, sleep, stress, exam pressure, felt support) and turns the answers into a **belief** — Low / Moderate / High cognitive load — using Bayesian updating: today's evidence is combined with the belief carried over from your last check-in, the same way a Bayesian model refines its estimate as new data arrives.

It is not a diagnostic or clinical tool. It's a lightweight way to make workload visible before it becomes unmanageable — something most students, especially in high-pressure exam systems, don't have.

## Why I built it

Indian students, especially in board-exam years, often normalise chronic overwork without any simple way to notice it happening. I wanted to take the Bayesian reasoning I'd already been exploring in [`bayesian-decision-maker`](https://github.com/arpitprk89/bayesian-decision-maker) and the state-modelling ideas from [`cognitive-ai-simulator`](https://github.com/arpitprk89/cognitive-ai-simulator), and point them at something real — not just an abstract demo, but a problem I and my classmates actually live with.

Brain 2.0 is meant as the synthesis point of that earlier work:
- **Bayesian inference** (from Bayesian Decision Maker) — the core belief-update mechanic
- **Modelling an internal state over time** (from Cognitive AI Simulator) — tracking load as a hidden variable, not a single snapshot
- **Learning from repeated feedback** (from RL Visualiser) — the belief sharpens the more you check in, rather than resetting each time

## Methodology

1. Five inputs are normalised to [0, 1] and combined into a single weighted load score.
2. The score is compared against three reference profiles (Low ≈ 0.25, Moderate ≈ 0.5, High ≈ 0.75) using a Gaussian likelihood.
3. Bayes' rule combines this likelihood with the prior belief (your last posterior, stored locally in the browser) to produce an updated posterior.
4. The posterior is shown as three probabilities and drives a plain-language recommendation.

## Tech

Plain HTML/CSS/JS, no dependencies. State persists in `localStorage` so it works fully offline once loaded, and is easy to host on GitHub Pages.

## Development period

Built July–September 2026, alongside ongoing conversations about computational approaches to decision-making and cognition that came out of my engagement with the Sakura Science Program application process (Neural Computation Unit, OIST) — this project isn't affiliated with or reviewed by OIST, it's my own attempt to apply similar ideas to a problem close to home.

## Honest limitations

- The scoring weights are hand-picked heuristics, not fit to real data — a natural next step would be collecting anonymised check-ins and calibrating the model properly.
- It reflects *reported* load, not a physiological or clinically validated measure.
- Recommendations are general wellbeing suggestions, not professional advice.

## What's next

- Export check-in history as CSV for a student's own record
- A small teacher/parent-facing aggregate view (opt-in, anonymous) to spot class-wide load spikes before exams
- Replace hand-picked weights with logistic regression trained on real (anonymised) check-in data**
