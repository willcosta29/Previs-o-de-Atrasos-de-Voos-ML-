# ✈️ Previsão de Atrasos de Voos

## 📋 Sobre o Projeto

Este projeto tem como objetivo construir e avaliar um modelo simples de **Machine Learning** (Regressão Logística) capaz de **prever se um voo terá atraso ou não** com base em dados de planejamento (código da companhia aérea, origem, destino, horários programados e distância).

O modelo foi desenvolvido em um notebook Google Colab, seguindo as etapas clássicas de um projeto de classificação: preparação e pré-processamento de dados, divisão em conjuntos de treino/teste, treinamento do modelo e avaliação de desempenho.

## 🚀 Como Executar o Notebook

Este projeto está contido em um notebook Jupyter (Google Colab) e pode ser executado diretamente na plataforma.

### Pré-requisitos

* Uma conta Google.
* Acesso ao arquivo `Machine_learning_project.ipynb` no Google Colab.

### Passos para Execução

1.  **Acesse o Notebook:** Abra o arquivo `Machine_learning_project.ipynb` no seu ambiente Colab.
2.  **Instale as Dependências:** As bibliotecas principais (Pandas, Scikit-Learn, Matplotlib, Seaborn) já devem estar disponíveis no ambiente Colab, mas execute as primeiras células de código para garantir a importação correta.
3.  **Execução:**
    * Vá em **"Ambiente de execução"** no menu superior.
    * Clique em **"Executar tudo"** (Run all).

O notebook executará todas as etapas, desde o carregamento dos dados até a visualização da matriz de confusão final.

## 🛠️ Tecnologias Utilizadas

* **Linguagem:** Python
* **Manipulação de Dados:** Pandas
* **Machine Learning:** Scikit-Learn (para Regressão Logística e `train_test_split`)
* **Visualização:** Matplotlib e Seaborn
* **Dataset:** Dados de satisfação de passageiros de companhias aéreas do Kaggle (link utilizado no projeto: `https://www.kaggle.com/datasets/giovannianto/airline-passenger-satisfaction`)

## ⚙️ Pipeline do Projeto

As principais etapas executadas no notebook foram:

### 1. Seleção e Pré-processamento dos Dados
* **Coluna Alvo:** A coluna alvo `ARR_DEL15` não foi encontrada, sendo criada a variável binária **`IS_DELAYED`** com base na coluna `ARR_DELAY` (1 se `ARR_DELAY` > 0, 0 caso contrário).
* **Seleção de Features:** Colunas como `AIRLINE_CODE`, `ORIGIN`, `DEST`, `CRS_DEP_TIME`, `CRS_ARR_TIME`, e `DISTANCE` foram utilizadas como preditores.
* **Tratamento de Categóricas:** As colunas categóricas (`AIRLINE_CODE`, `ORIGIN`, `DEST`) foram transformadas em variáveis numéricas usando a técnica **One-Hot Encoding**.
* **Tratamento de Missings:** Linhas com valores ausentes (NaN) nas colunas selecionadas foram removidas.

### 2. Divisão e Treinamento do Modelo
* **Divisão:** O dataset processado foi dividido em conjuntos de treino (`X_train`, `y_train`) e teste (`X_test`, `y_test`) usando `test_size=0.2`.
* **Modelo:** Foi utilizada a **Regressão Logística** para a tarefa de classificação binária (Atrasado/Não Atrasado).

### 3. Avaliação e Visualização
* O modelo foi avaliado usando **Acurácia** e **Matriz de Confusão**.
* A Matriz de Confusão foi visualizada com um *heatmap* usando Seaborn para maior clareza.

## 📈 Resultados da Avaliação

O modelo de Regressão Logística obteve os seguintes resultados no conjunto de teste:

* **Acurácia do Modelo:** `0.6000` (60% de acertos)

### Matriz de Confusão

| Real / Previsto | Não Atrasado (0) | Atrasado (1) |
| :--- | :--- | :--- |
| **Não Atrasado (0)** | 11 (Verdadeiros Negativos - TN) | 3 (Falsos Positivos - FP) |
| **Atrasado (1)** | 5 (Falsos Negativos - FN) | 1 (Verdadeiros Positivos - TP) |

### Insights Chave

* **Acurácia Moderada (60%):** O desempenho inicial do modelo é modesto e sugere que, embora ele consiga classificar corretamente a maioria dos voos, há um espaço significativo para melhorias.
* **Falsos Negativos:** O modelo falhou em prever 5 voos que estavam atrasados (Falsos Negativos), enquanto só acertou 1 voo atrasado (Verdadeiro Positivo). Isso indica que o modelo tem uma dificuldade maior em **identificar a classe minoritária (atrasos)**.
* **Próximos Passos:** Para melhorar o modelo, seria crucial implementar a **padronização de dados numéricos** (devido ao aviso de convergência da Regressão Logística), experimentar outros algoritmos (como Random Forest ou XGBoost), ou aplicar técnicas de balanceamento de classes (como SMOTE).
