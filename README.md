# Previsão de cancelamento de clientes (churn) com MLP

Trabalho final da disciplina **Modelagem de Dados com Redes Neurais Artificiais** (USP).

Integrantes: Rebeca Camille Bernardes, Ana Carolina Moraes Campos, Sabrina de Araújo Corrêa e Karen Dal Magro Frigeri.

Classificação binária do cancelamento de clientes de uma operadora de telecomunicações com um perceptron multicamadas (MLP) em TensorFlow/Keras, comparado a uma regressão logística.

## Dados

- **Base:** *Telco Customer Churn* (IBM), publicada no Kaggle em <https://www.kaggle.com/datasets/blastchar/telco-customer-churn>.
- 7.043 clientes, 19 variáveis explicativas e o alvo `Churn` (26,5% de cancelamentos).
- O notebook baixa o arquivo automaticamente com `kagglehub`. Se o download falhar, usa a cópia pública da IBM:
  <https://raw.githubusercontent.com/IBM/telco-customer-churn-on-icp4d/master/data/Telco-Customer-Churn.csv>.

## Como executar

1. Abra `Churn_Telco_MLP.ipynb` no Google Colab (*Arquivo → Fazer upload de notebook*) ou em um Jupyter local.
2. Localmente, instale as dependências: `pip install -r requirements.txt`.
3. Execute todas as células em ordem (*Ambiente de execução → Executar tudo*). Tempo aproximado: 20 a 30 minutos em CPU.

## Etapas do notebook

| Seção | Conteúdo |
|---|---|
| 1–2 | Ambiente, versões, sementes e carga dos dados |
| 3 | Análise exploratória: tipos, ausentes, duplicidades, classes, distribuições |
| 4–5 | Divisão estratificada 60/20/20 e pré-processamento ajustado só no treino |
| 6 | Modelos de referência: classe majoritária e regressão logística |
| 7 | MLP inicial, sem regularização |
| 8 | Busca aleatória de hiperparâmetros com validação cruzada estratificada |
| 9 | Ablação: contribuição de Dropout, L2, pesos de classe e EarlyStopping |
| 10 | Modelo final (conjunto de 5 redes) e escolha do limiar na validação |
| 11 | Avaliação única no conjunto de teste |
| 12 | Análise de erros e importância por permutação |

## Reprodutibilidade

- Semente global: `42` (`keras.utils.set_random_seed`); redes do conjunto com sementes 0 a 4.
- Saídas geradas: pasta `figuras/`, `busca_hiperparametros.csv`, `ablacao.csv`, `resultados_teste.csv`.
- Pequenas diferenças numéricas entre máquinas podem ocorrer por operações de ponto flutuante na CPU/GPU.
