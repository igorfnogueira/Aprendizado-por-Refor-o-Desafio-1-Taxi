# Aprendizado por Reforço — Desafio 1: Taxi

**Language / Idioma:** [English](README.md) | [Português](README.pt-br.md)

Residência em Inteligência Artificial · unidade de **Aprendizado por Reforço**.

Desafio de **planejamento com modelo** no ambiente [Taxi](https://gymnasium.farama.org/environments/toy_text/taxi/) (`Taxi-v3`, com fallback para `Taxi-v4` no Gymnasium recente).

## O que este projeto faz

Implementação do zero de:

- **Value Iteration**
- **Policy Iteration**

usando o modelo de transição `env.P` (programação dinâmica). O notebook compara eficiência (tempo / iterações) e o impacto do fator de desconto `gamma` na policy e no retorno.

O Taxi tem **500 estados** discretos. O agente precisa pegar o passageiro e deixá-lo no destino correto (`+20`), evitando pickup/drop-off ilegal (`-10`) e pagando `-1` por passo.

## Arquivo principal

- [RL_Desafio_Taxi_VI_PI.ipynb](RL_Desafio_Taxi_VI_PI.ipynb) — algoritmos, experimentos, mapas de Q/policy e rollouts

## Como rodar

1. Use **Python 3.11 ou 3.12** (recomendado; evite 3.14).
2. Crie um ambiente virtual e instale as dependências:

```bash
python -m venv .venv
# Windows:
.venv\Scripts\activate
pip install gymnasium numpy matplotlib seaborn moviepy pillow ipykernel
```

3. Abra o notebook no Jupyter / VS Code / Cursor e execute as células na ordem.

## Artefatos de episódio

Após a comparação por `gamma`, o notebook gera:

- `taxi_gamma_0.1.gif` / `.mp4`
- `taxi_gamma_0.5.gif` / `.mp4`
- `taxi_gamma_0.9.gif` / `.mp4`
- `taxi_gamma_0.99.gif` / `.mp4`

No preview do GitHub, a seção **5.2** mostra os GIFs inline e links para os MP4s. A seção **6** exibe a policy final (`gamma=0.99`) da mesma forma.

## Principais conclusões

1. **Performance:** Value Iteration e Policy Iteration chegam à **mesma policy ótima**. O Policy Iteration usa poucas iterações externas (a policy estabiliza cedo), mas cada uma é cara; o Value Iteration usa varreduras mais baratas e em maior número. Com 500 estados, ambos são rápidos.
2. **Comportamento míope (`γ = 0.1`):** com desconto muito baixo, o `+20` da entrega é descontado quase a zero e o agente não encadeia pickup → transporte → drop-off. Sucesso confiável exige `γ` alto (`0.9`, `0.99`).
3. **Teoria:** ambos resolvem a mesma equação de Bellman de otimalidade e, com `γ < 1`, convergem para o mesmo `V*` / `π*`. Policy idêntica é garantia matemática, não coincidência.

## Repositório

https://github.com/igorfnogueira/Aprendizado-por-Refor-o-Desafio-1-Taxi
