# Projeto Prático II (SAD)

Mineração de dados aplicada à base **Chicago Crimes** com foco em **classificação da variável `Arrest`** (prever se houve prisão).

## Base de Dados (Baixar Antes de Rodar)

O arquivo CSV é grande (aprox. `1.8 GB`) e **não deve ser versionado no GitHub**.

Faça o download da base em:

- Kaggle: `https://www.kaggle.com/datasets/utkarshx27/crimes-2001-to-present?utm_source=chatgpt.com`

Depois, salve o arquivo **na raiz do projeto** com este nome exato:

- `Crimes_-_2001_to_Present.csv`

Sem esse arquivo, o notebook `analise_crimes_classificacao.ipynb` não executa.

## Autores

- Nahan Rezende
- Iasmin Ghirlinzone

## Objetivo

Construir e avaliar um modelo de classificação binária para prever `Arrest` a partir de atributos como:

- tipo de crime
- descrição
- local da ocorrência
- variáveis temporais derivadas de `Date`
- atributos geográficos/administrativos

Também é feita comparação com um baseline (`DummyClassifier`) e avaliação com:

- acurácia
- precisão
- revocação
- F1-score
- matriz de confusão
