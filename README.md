# Mutually Exclusive NO Bet Calculator

Static GitHub Pages app for sizing NO bets in a mutually exclusive winner market (for example, March Madness champion).

## What It Does

- Accepts team-level true probabilities, NO prices, and your currently filled NO shares.
- Computes state-by-state wealth for each possible champion outcome.
- Solves incremental full Kelly size for each possible next NO fill.
- Applies a user-defined Kelly fraction (default `0.25` for quarter Kelly).
- Shows worst-case state wealth before and after suggested fractional sizing.

## Formula Basis

For team `i` NO bet with price `n_i` and shares `q_i`:

- If team `i` wins: payoff contribution is `-n_i * q_i`
- If any other team wins: payoff contribution is `(1 - n_i) * q_i`

State wealth for champion state `s`:

`W_s = W0 + sum_i q_i * r_{s,i}`

Incremental sizing for candidate team `k` solves:

`max_{delta q >= 0} [ pi_k log(W_k - n_k delta q) + sum_{s!=k} pi_s log(W_s + (1 - n_k) delta q) ]`

Then fractional Kelly sizing is:

`delta_q_fractional = f * delta_q_full_kelly`

## Run Locally

Open `index.html` in a browser.

## Publish On GitHub Pages

1. Push this repository to GitHub.
2. In repository settings, open **Pages**.
3. Set source to deploy from `main` branch root.
4. Save, then open the published URL.