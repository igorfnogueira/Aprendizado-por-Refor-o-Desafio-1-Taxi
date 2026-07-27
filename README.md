# Aprendizado por Reforço — Desafio 1: Taxi

Residência em Inteligência Artificial · unidade de **Aprendizado por Reforço**.

Desafio de **planejamento com modelo** no ambiente [Taxi](https://gymnasium.farama.org/environments/toy_text/taxi/) (`Taxi-v3`, com fallback para `Taxi-v4` no Gymnasium recente).

## O que este projeto faz

Implementação do zero de:

- **Value Iteration**
- **Policy Iteration**

Usando o modelo de transição `env.P` (programação dinâmica). O notebook também compara eficiência (tempo / iterações) e o impacto do fator de desconto `gamma` na policy e no retorno.

## Arquivo principal

- [RL_Desafio_Taxi_VI_PI.ipynb](RL_Desafio_Taxi_VI_PI.ipynb) — código, experimentos e visualizações

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

Após a seção de comparação por `gamma`, o notebook gera:

- `taxi_gamma_0.1.gif` / `.mp4`
- `taxi_gamma_0.5.gif` / `.mp4`
- `taxi_gamma_0.9.gif` / `.mp4`
- `taxi_gamma_0.99.gif` / `.mp4`

No preview do GitHub, a seção **5.2** do notebook mostra os GIFs inline e links para os MP4s.

## Repositório

https://github.com/igorfnogueira/Aprendizado-por-Refor-o-Desafio-1---Taxi
