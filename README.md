# Identificação de motor CC com LMS e NLMS

Projeto final da disciplina de Processamento Adaptativo de Sinais.

O notebook principal replica computacionalmente a metodologia do artigo **Adaptive Filters for DC Motor Identification: A Case Study**, usando uma planta simulada de motor CC. Não há motor físico, aquisição experimental ou dependência de MATLAB.

## Objetivo

Identificar a dinâmica de um motor CC simulado por filtros FIR, usando:

- filtro de Wiener como referência ótima em lote;
- LMS como algoritmo adaptativo;
- NLMS como variante normalizada do LMS.

A métrica principal adotada é o erro quadrático médio, MSE.

## Estrutura

- `notebooks/01_identificacao_motor_dc_lms_nlms.ipynb`: notebook final organizado.
- `figures/`: figuras finais geradas automaticamente pelo notebook.
- `src/`: funções auxiliares mantidas para organização futura do projeto.
- `artigo/`: material relacionado ao artigo.
- `apresentacao/`: material de apresentação.
- `requirements.txt`: dependências principais.

## Como executar

Instale as dependências:

```bash
pip install -r requirements.txt
```

Abra e execute o notebook:

```bash
jupyter notebook notebooks/01_identificacao_motor_dc_lms_nlms.ipynb
```

O notebook deve ser executado em ordem, do início ao fim.

## Configuração principal

- `Ts = 1e-3`
- `nsamples = 100000`
- `sigma2 = 0.1`
- `u0 = 10.0`
- `delta_u = 0.6`
- `samples_per_bit = 50`
- `seed_prbs = 42`
- `seed_noise = 123`
- `Nimp = 500`
- `Ntaps = 55`
- `mu_lms = 1e-4`
- `mu_nlms = 0.1`
- `gamma = 1e-6`

## Resultados principais

Resultados obtidos na validação final do notebook:

| Método | MSE treino | MSE teste |
|---|---:|---:|
| Wiener | 0.2502 | 0.2494 |
| LMS | 0.5931 | 0.2683 |
| NLMS | 0.2029 | 0.2717 |

Os valores de teste preservam os resultados principais do desenvolvimento:

- Wiener: `MSE teste ≈ 0.2494`
- LMS: `MSE teste ≈ 0.2683`
- NLMS: `MSE teste ≈ 0.2717`

## Figuras geradas

O notebook salva automaticamente as figuras finais em `figures/`:

- `entrada_saida_sistema.png`
- `resposta_impulso_motor.png`
- `wiener_saida_teste.png`
- `comparacao_saida_lms_nlms.png`
- `convergencia_lms_nlms.png`
- `comparacao_mu.png`
- `coeficientes_lms_nlms.png`

## Limitações

Os resultados não devem ser interpretados como identificação experimental de um motor real. A planta é simulada a partir de parâmetros nominais, e o ruído de medição é sintético.

Esta versão mantém o foco em Wiener, LMS e NLMS. Algoritmos como AP e RLS ficam como extensões futuras.
