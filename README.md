# Reinforcement Learning — Challenge 1: Taxi

**Language / Idioma:** [English](README.md) | [Português](README.pt-br.md)

AI Residency · **Reinforcement Learning** course unit.

Model-based planning challenge on the [Taxi](https://gymnasium.farama.org/environments/toy_text/taxi/) environment (`Taxi-v3`, with fallback to `Taxi-v4` on recent Gymnasium).

## What this project does

From-scratch implementation of:

- **Value Iteration**
- **Policy Iteration**

using the transition model `env.P` (dynamic programming). The notebook compares efficiency (runtime / iterations) and the effect of the discount factor `gamma` on the policy and return.

The Taxi task has **500 discrete states**. The agent must pick up a passenger and drop them off at the correct destination (`+20`), while avoiding illegal pickup/drop-off (`-10`) and paying `-1` per step.

## Main file

- [RL_Desafio_Taxi_VI_PI.ipynb](RL_Desafio_Taxi_VI_PI.ipynb) — algorithms, experiments, Q/policy plots, and episode rollouts

## How to run

1. Use **Python 3.11 or 3.12** (recommended; avoid 3.14).
2. Create a virtual environment and install dependencies:

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
pip install gymnasium numpy matplotlib seaborn moviepy pillow ipykernel
```

3. Open the notebook in Jupyter / VS Code / Cursor and run the cells in order.

## Episode artifacts

After the per-`gamma` comparison section, the notebook generates:

- `taxi_gamma_0.1.gif` / `.mp4`
- `taxi_gamma_0.5.gif` / `.mp4`
- `taxi_gamma_0.9.gif` / `.mp4`
- `taxi_gamma_0.99.gif` / `.mp4`

On GitHub’s notebook preview, section **5.2** shows the GIFs inline and links to the MP4s. Section **6** shows the final policy (`gamma=0.99`) the same way.

## Key takeaways

1. **Performance:** Value Iteration and Policy Iteration reach the **same optimal policy**. Policy Iteration uses few outer iterations (policy stabilizes early) but each outer step is expensive; Value Iteration uses cheaper sweeps and more of them. Both are fast at 500 states.
2. **Myopic behavior (`γ = 0.1`):** With a very small discount, the distant `+20` delivery reward is nearly zeroed out, so the agent fails to chain pickup → transport → drop-off. Reliable success needs high `γ` (`0.9`, `0.99`).
3. **Theory:** Both solve the same Bellman optimality equation and converge to the same `V*` / `π*` for `γ < 1`. Identical policies are expected, not a coincidence.

## Repository

https://github.com/igorfnogueira/rl-python-taxi-agent
