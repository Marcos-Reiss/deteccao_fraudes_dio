# Detecção de anomalias em transações — DIO

Notebook para identificar fraudes em cartão de crédito em dados extremamente desbalanceados. Acurácia isolada não é suficiente: com cerca de 0,17% de fraudes, prever sempre “normal” gera acurácia elevada sem identificar fraudes.

## Execução

1. Instale as dependências: `pip install -r requirements.txt notebook`.
2. Abra `deteccao_fraudes.ipynb` no Jupyter.
3. Informe a URL direta do dataset `creditcard.csv` da Aula 1 na variável de ambiente `DATASET_URL`, ou coloque o arquivo na pasta local (não faça commit).
4. Execute todas as células e salve o notebook com as saídas.

## Preparação

Criamos `Amount_log` com `log1p`, dividimos os dados com estratificação em treino (60%), validação (20%) e teste (20%) e aplicamos `StandardScaler` à regressão logística dentro do pipeline, sem ajustar o scaler com dados de teste.

## Modelos e avaliação

Comparamos regressão logística ponderada, Random Forest ponderada e XGBoost com `scale_pos_weight`. Selecionamos limiar na validação com meta ilustrativa de recall ≥ 0,80 e máximo F1. Avaliamos recall, precisão, F1, ROC AUC e Average Precision no teste. O SHAP explica contribuições de atributos para previsões individuais.

## Resultados

**Preencher após executar o notebook com o dataset real**: tabela de recall, precisão e F1 por modelo, limiar selecionado e variáveis relevantes no SHAP. Não há métricas inventadas neste README.

## Adaptações em relação à aula

Adicionamos um conjunto de validação independente para ajustar o limiar sem usar o teste, seleção orientada por recall e apresentação conjunta de ROC e precisão-recall.

## Limitações

Amostragem aleatória é baseline; em aplicações reais, avaliar divisão temporal, custos de falsos positivos, deriva e segurança operacional.
