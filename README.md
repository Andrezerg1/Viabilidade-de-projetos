# Analisador de Viabilidade de Projetos com Machine Learning

## Sobre o Projeto

Este projeto foi desenvolvido com o objetivo de aplicar conceitos de Machine Learning e Inteligência Artificial na análise de viabilidade de projetos.

O sistema utiliza um modelo de aprendizado supervisionado para analisar informações históricas de projetos e identificar padrões que indiquem a probabilidade de um novo projeto ser considerado viável ou não.

A partir de variáveis como investimento necessário, retorno esperado e pontuação de impacto, o modelo é capaz de estimar a probabilidade de sucesso de novos projetos e classificá-los de acordo com os padrões aprendidos durante o treinamento.

---

## Como Funciona

O funcionamento do sistema segue as seguintes etapas:

### 1. Carregamento dos Dados

Os dados históricos são armazenados em um arquivo CSV contendo informações de projetos já avaliados.

Exemplo de atributos utilizados:

* Investment (Investimento necessário)
* Expected Return (Retorno esperado)
* Impact Score (Pontuação de impacto)
* Viability (Viabilidade do projeto)

---

### 2. Pré-processamento

Após o carregamento dos dados, as variáveis independentes (features) são separadas da variável alvo (target).

**Features:**

* investment
* expected_return
* impact_score

**Target:**

* viability

Em seguida, os dados passam por um processo de normalização utilizando o `StandardScaler`, permitindo que todas as variáveis fiquem em uma escala semelhante e evitando que atributos com valores maiores exerçam influência desproporcional sobre o modelo.

---

### 3. Divisão dos Dados

O conjunto de dados é dividido em dois grupos:

* Treinamento (70%)
* Teste (30%)

Essa divisão permite avaliar o desempenho do modelo utilizando dados que não foram vistos durante o treinamento.

---

### 4. Treinamento do Modelo

O algoritmo utilizado é a **Regressão Logística (Logistic Regression)**, amplamente empregada em problemas de classificação binária.

Durante o treinamento, o modelo aprende a relação entre as características dos projetos e sua viabilidade, ajustando automaticamente seus parâmetros internos para maximizar a capacidade de previsão.

---

### 5. Avaliação

Após o treinamento, o modelo é testado utilizando o conjunto de teste.

São calculadas métricas como:

* Accuracy
* Precision
* Recall
* F1-Score

Essas métricas permitem avaliar a qualidade das previsões realizadas.

---

### 6. Persistência do Modelo

Para evitar a necessidade de treinar o modelo a cada execução, o sistema salva em disco:

* Modelo treinado
* Normalizador (Scaler)
* Métricas de desempenho

Os arquivos são armazenados utilizando a biblioteca `joblib`.

---

### 7. Predição de Novos Projetos

Após treinado, o modelo pode receber novos projetos para análise.

Exemplo:

```python
new_projects = [
    {
        "investment": 40000,
        "expected_return": 60000,
        "impact_score": 6
    }
]
```

Os dados são normalizados utilizando o mesmo scaler empregado durante o treinamento e então enviados ao modelo.

O sistema retorna:

* Classificação de viabilidade (0 ou 1)
* Probabilidade estimada de sucesso

Exemplo de saída:

| investment | expected_return | impact_score | probability | viability |
| ---------- | --------------- | ------------ | ----------- | --------- |
| 40000      | 60000           | 6            | 0.82        | 1         |

---

## Tecnologias Utilizadas

* Python
* Pandas
* NumPy
* Scikit-Learn
* Joblib
* Google Colab

---

## Conceitos Aplicados

* Machine Learning Supervisionado
* Classificação Binária
* Regressão Logística
* Normalização de Dados
* Treinamento e Teste de Modelos
* Avaliação de Desempenho
* Persistência de Modelos

---

## Objetivo Educacional

Este projeto foi desenvolvido como parte dos estudos em Machine Learning e Inteligência Artificial, com foco na compreensão prática do ciclo completo de desenvolvimento de modelos preditivos, desde o tratamento dos dados até a geração de previsões para novos cenários.
