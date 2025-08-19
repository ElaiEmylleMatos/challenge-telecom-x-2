# Análise e Modelagem de Churn de Clientes em Telecom

Este projeto tem como objetivo analisar e modelar o churn de clientes de uma empresa de telecomunicações, buscando identificar os fatores que levam à evasão e construir modelos preditivos para antecipar o churn.

## Estrutura do Notebook

O notebook está organizado nas seguintes seções:

1.  **Preparação dos Dados**: Carregamento, limpeza e pré-processamento dos dados.
    *   Importação das bibliotecas necessárias.
    *   Carregamento do conjunto de dados.
    *   Tratamento de valores nulos e conversão de tipos de dados.
    *   Codificação de variáveis categóricas.
    *   Análise de correlação (Heatmap).
    *   Remoção de features com alta correlação ou baixa importância.
2.  **Modelagem**: Construção e treinamento de modelos de classificação.
    *   Separação dos dados em conjuntos de treino, validação e teste.
    *   Verificação e tratamento do desbalanceamento das classes (SMOTE).
    *   Treinamento de modelos base (Dummy Classifier), Random Forest e KNN.
    *   Otimização do melhor modelo (Random Forest) utilizando `GridSearchCV`.
3.  **Avaliação**: Comparação e análise do desempenho dos modelos.
    *   Implementação de uma função para avaliar modelos com diversas métricas (Acurácia, Precisão, Recall, F1-Score, ROC-AUC).
    *   Avaliação dos modelos treinados no conjunto de teste.
    *   Visualização comparativa das métricas.
    *   Análise da importância das features no melhor modelo (Random Forest).
4.  **Conclusões Estratégicas**: Interpretação dos resultados e recomendações.
    *   Comparação da performance do Random Forest básico e otimizado.
    *   Análise da performance do modelo KNN.
    *   Comparação com o modelo base.
    *   Recomendação final de qual modelo utilizar dependendo do objetivo de negócio (minimizar falsos positivos vs. maximizar detecção de churn).

## Resultados Principais

Após a análise e modelagem, obtivemos os seguintes resultados comparativos nos modelos avaliados:

| Modelo                     | Acurácia | Precisão | Recall | F1-Score | ROC-AUC |
| -------------------------- | -------- | -------- | ------ | -------- | ------- |
| Dummy                      | 0.4997   | 0.4997   | 1.0000 | 0.6664   | 0.5000  |
| RandomForest               | 0.8547   | 0.8498   | 0.8614 | 0.8556   | 0.9392  |
| KNN                        | 0.7730   | 0.7252   | 0.8787 | 0.7946   | 0.8492  |
| RandomForest Otimizado     | 0.8299   | 0.8005   | 0.8787 | 0.8378   | 0.9148  |

**Destaques:**

*   **Random Forest Básico:** Apresentou o melhor equilíbrio entre as métricas e o maior ROC-AUC, indicando excelente capacidade discriminativa.
*   **KNN:** Obteve um alto Recall, sendo uma boa opção se o foco principal for identificar o maior número possível de clientes que potencialmente darão churn, mesmo que isso gere mais falsos positivos.
*   **Otimização:** A otimização com `GridSearchCV` não resultou em uma melhoria significativa na performance do Random Forest básico.

## Conclusões e Recomendações

O modelo **Random Forest Básico** é o mais recomendado para a empresa devido ao seu bom desempenho geral em todas as métricas relevantes para o problema de churn.

No entanto, a escolha final do modelo pode depender da estratégia de negócio:

*   Para uma estratégia de **retenção agressiva** (priorizando a identificação de churns, mesmo com mais falsos positivos), o modelo **KNN** pode ser considerado pela sua alta capacidade de Recall.
*   Para uma estratégia que prioriza a **eficiência em campanhas de retenção** (minimizando falsos positivos), o **Random Forest Básico** é a melhor escolha pela sua maior Precisão e F1-Score.

Todos os modelos preditivos desenvolvidos superaram significativamente o modelo base (Dummy Classifier), demonstrando a importância da modelagem para este problema.
