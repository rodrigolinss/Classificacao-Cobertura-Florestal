# Classificação de Cobertura Florestal com Redes Neurais

## Descrição do Projeto

Este projeto tem como objetivo classificar o tipo de cobertura florestal utilizando um modelo de deep learning baseado em redes neurais. O estudo foi conduzido como parte de um experimento acadêmico e utilizou o conjunto de dados [Covertype](https://archive.ics.uci.edu/dataset/31/covertype) do UCI Machine Learning Repository.

O dataset contém informações cartográficas de áreas florestais no norte do Colorado, nos Estados Unidos, derivadas de fontes como o US Geological Survey (USGS) e o US Forest Service (USFS). O objetivo é prever a cobertura florestal com base em variáveis geográficas e ambientais.
 
---

## Estrutura dos Dados

O dataset é composto por 54 variáveis preditoras, incluindo:
- **Elevação**
- **Inclinação**
- **Distância até hidrografia**
- **Sombra**
- **Tipo de solo**
- **Áreas de proteção ambiental**

A variável alvo (target) representa o tipo de cobertura florestal, categorizada em sete classes:

| Código | Cobertura Florestal       |
|--------|--------------------------|
| 1      | Spruce/Fir               |
| 2      | Lodgepole Pine           |
| 3      | Ponderosa Pine           |
| 4      | Cottonwood/Willow        |
| 5      | Aspen                    |
| 6      | Douglas-Fir              |
| 7      | Krummholz                |

O conjunto de dados original apresentava um desbalanceamento entre classes, o que motivou o uso da técnica **SMOTE (Synthetic Minority Over-sampling Technique)** para equilibrar a distribuição das classes e melhorar a capacidade preditiva do modelo.

---

## Modelo Utilizado

Foi implementada uma rede neural com a seguinte estrutura:
- **Camada de entrada**: 54 neurônios (correspondente ao número de variáveis preditoras)
- **Camadas ocultas**: 
  - Primeira camada oculta: 128 neurônios + Batch Normalization + ReLU
  - Segunda camada oculta: 64 neurônios + Batch Normalization + ReLU
- **Camada de saída**: 7 neurônios (um para cada classe), com ativação softmax

A função de perda utilizada foi **CrossEntropyLoss**, e o otimizador foi o **Adam**, com taxa de aprendizado de 0.001. O treinamento foi realizado em 10 épocas.

---

## Resultados

Após a aplicação do **SMOTE**, o modelo atingiu uma acurácia de **93,54%** no conjunto de teste, apresentando os seguintes desempenhos para cada classe:

| Classe | Precisão | Recall | F1-Score | Suporte |
|--------|----------|--------|----------|---------|
| 0      | 0.91     | 0.83   | 0.87     | 45.328  |
| 1      | 0.86     | 0.86   | 0.86     | 45.328  |
| 2      | 0.94     | 0.93   | 0.94     | 45.328  |
| 3      | 0.98     | 0.99   | 0.99     | 45.328  |
| 4      | 0.95     | 0.99   | 0.97     | 45.328  |
| 5      | 0.93     | 0.95   | 0.94     | 45.328  |
| 6      | 0.97     | 1.00   | 0.98     | 45.328  |

**Métricas gerais:**
- **Acurácia**: 93,54%
- **Média macro** (macro avg): Precisão 93%, Recall 94%, F1-score 93%
- **Média ponderada** (weighted avg): Precisão 93%, Recall 94%, F1-score 93%

O modelo apresentou um desempenho sólido após o balanceamento das classes, com melhoria significativa no recall das classes minoritárias. Ainda assim, houve um número maior de erros nas classes 0 e 1, indicando oportunidades de refinamento futuro.

---

Este estudo foi conduzido para fins educacionais e demonstrativos, explorando conceitos de aprendizado de máquina e pré-processamento de dados em problemas reais.
