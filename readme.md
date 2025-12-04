# Glioma Classification with KNN

Projeto de classificação binária de Glioma (LGG vs GBM) usando KNN em Python/Scikit-learn. O fluxo inclui EDA, preparação dos dados, divisão treino/validação/teste, normalização, treinamento do KNN e avaliação com métricas, matriz de confusão e curva ROC/AUC.

## Estrutura do projeto

- `main.ipynb`: Notebook principal com todo o pipeline.
- `glioma.csv`: Dataset usado no treinamento e avaliação (não versionado aqui).
- `readme.md`: Este documento.

## Dataset

Coluna-alvo:
- `Glioma` (antiga `Grade`): 0 = LGG (Benign), 1 = GBM (Malignant)

Principais features:
- Demográficas: `Gender`, `Age_at_diagnosis`, `Race`
- Genéticas: `IDH1`, `TP53`, `ATRX`, `PTEN`, `EGFR`, etc. (0 = NOT_MUTATED, 1 = MUTATED)

Não há valores ausentes reportados no dataset.

## Ambiente e dependências

Requisitos:
- Python 3.10+ (Linux)
- VS Code com extensão Python e Jupyter


Instalação rápida (Linux):

```bash
python3 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
```

## Como executar no VS Code

1. Abra a pasta do projeto no VS Code.
2. Selecione o kernel do Python (use o ambiente `.venv`).
3. Abra `main.ipynb`.
4. Garanta que `glioma.csv` está na mesma pasta do notebook.
5. Execute as células em sequência (Run All ou passo a passo).

## Pipeline do notebook

- EDA:
  - Distribuição das classes
  - Matriz de correlação
  - Análise das features com maior correlação com `Glioma`
- Split:
  - Train/Val/Test com `train_test_split` e `stratify`
- Normalização:
  - MinMaxScaler aplicado em `Age_at_diagnosis` (fit no treino, transform em val/test)
- Modelo:
  - `KNeighborsClassifier(n_neighbors=14)`
- Avaliação:
  - Matriz de confusão (Val e Test)
  - Métricas: Acurácia, Precisão, Recall, F1-Score
  - Curva ROC e AUC (Val e Test)

# Sugestões de melhorias

- Experimentar outros algoritmos de classificação (SVM, Random Forest, etc.).
- Implementar validação cruzada para melhor avaliação do modelo.
- Realizar tuning de hiperparâmetros com GridSearchCV ou RandomizedSearchCV.
- Analisar importância das features e realizar seleção de features.
