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

## Arquivos Principais

- `analise_crimes_classificacao.ipynb`: notebook principal (EDA + preparação + modelagem + avaliação)
- `slides_apresentacao_sad.tex`: slides da apresentação em Beamer
- `prints/`: imagens usadas nos slides (extraídas/geradas a partir das saídas do notebook)
- `TP_pratico_II_30_pontos.pdf`: enunciado do trabalho

## Prints Usados nos Slides

O arquivo `slides_apresentacao_sad.tex` referencia os seguintes arquivos:

- `prints/01_leitura_base.png`
- `prints/02_caracterizacao_tabelas.png`
- `prints/03_eda_geral_2x2.png`
- `prints/04_taxa_prisao_temporal.png`
- `prints/05_taxa_prisao_por_tipo.png`
- `prints/06_split_e_atributos.png`
- `prints/07_tabela_e_grafico_metricas.png`
- `prints/08_relatorio_matriz_confusao.png`

## Como Executar o Notebook

### 1. Criar/ativar ambiente virtual (opcional, recomendado)

No Windows (PowerShell):

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 2. Instalar dependências

```powershell
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### 3. Abrir o notebook

```powershell
python -m jupyter notebook
```

Abra `analise_crimes_classificacao.ipynb` e execute as células.

## Execução com Base Completa

O notebook foi preparado para rodar com a base completa usando:

```python
N_ROWS = None
```

Observações práticas:

- a base é grande (~1.8 GB), então a execução pode levar vários minutos
- a etapa de regressão logística pode ser a mais demorada
- se necessário, use `solver='saga'` para acelerar em bases grandes

Exemplo:

```python
LogisticRegression(
    max_iter=120,
    class_weight='balanced',
    solver='saga',
    n_jobs=-1,
    random_state=42,
    tol=1e-3
)
```

## Compatibilidade (`pandas` / `scikit-learn`)

Em algumas versões, pode ocorrer erro no pipeline categórico (`SimpleImputer` + colunas com `pd.NA`).

Solução recomendada antes do treinamento:

- manter colunas categóricas como `object`
- converter colunas numéricas com `pd.to_numeric(..., errors='coerce')`

## Como Gerar os Slides

Com os prints salvos em `prints/`, compile o arquivo:

- `slides_apresentacao_sad.tex`

Exemplo (MiKTeX / `pdflatex`):

```powershell
pdflatex .\slides_apresentacao_sad.tex
```

Pode ser necessário rodar 2 vezes para atualizar elementos.

## Checklist Final de Entrega

- notebook executado e salvo com outputs
- prints gerados e presentes em `prints/`
- métricas atualizadas no `slides_apresentacao_sad.tex` (`\MetricAcc`, `\MetricPrec`, `\MetricRec`, `\MetricFone`, `\TargetPosRate`)
- slides compilados sem placeholders
- PDF com link do repositório/apresentação enviado no Moodle

