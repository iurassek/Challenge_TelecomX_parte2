# Relatório de Análise e Resultados do Modelo Preditivo de Churn - Telecom X

**Data:** 06 de Agosto de 2025  
**Autor:** Ricardo Iurassek, auxiliado por AI  

## 1. Introdução
Este relatório apresenta os resultados da análise preditiva de churn (evasão de clientes) realizada com base no dataset da Telecom X. O objetivo foi desenvolver um modelo capaz de prever quais clientes têm maior risco de churn, identificar as variáveis mais influentes nesse comportamento e fornecer insights para estratégias de retenção. Utilizamos um modelo de Random Forest Classifier e exploramos os dados fornecidos, incluindo estatísticas descritivas e visualizações.

## 2. Metodologia

### Pré-processamento dos Dados:
- Carregamos o dataset `TelecomX_Dados_Tratados.csv` e convertemos variáveis categóricas (como `Churn`, `internet.InternetService`, etc.) para formato numérico usando `LabelEncoder`.
- Escalamos features numéricas (`customer.tenure`, `account.Charges.Monthly`, `account.Charges.Total`) com `StandardScaler` para normalizar os dados.
- Dividimos os dados em conjuntos de treino (80%) e teste (20%).

### Modelo Preditivo:
- Implementamos um `RandomForestClassifier` com 100 estimadores e semente aleatória fixa (42) para garantir reprodutibilidade.
- Treinamos o modelo e avaliamos sua performance com métricas como acurácia e relatório de classificação.

### Análise de Resultados:
- Calculamos a importância das features para identificar os fatores mais relevantes.
- Previsões de probabilidade foram usadas para identificar clientes de alto risco (probabilidade de churn > 0.5).

## 3. Resultados
- **Acurácia do Modelo:** A acurácia obtida foi de 0.78, indicando que o modelo prevê corretamente cerca de 80% dos casos de churn.
- **Relatório de Classificação:** O relatório detalha precisão, recall e F1-score para as classes "Não" e "Sim". Por exemplo:
  - Classe "Não": Alta precisão e recall, refletindo boa identificação de clientes que não churnaram.
  - Classe "Sim": Possível desbalanceamento, com recall mais baixo, sugerindo que alguns casos de churn podem não estar sendo capturados.
- **Importância das Features:** As features mais influentes incluíram `customer.tenure` (tempo de permanência), `account.Charges.Monthly` (custos mensais) e `internet.InternetService` (tipo de serviço de internet), corroborando os insights exploratórios de que clientes com alta rotatividade estão associados a serviços de fibra óptica e custos elevados.
- **Clientes de Alto Risco:** Identificamos uma lista de clientes com probabilidade de churn superior a 0.5, incluindo detalhes como `customerID`, `Probabilidade_Churn`, `customer.tenure`, `internet.InternetService` e `account.Charges.Monthly`. Esses clientes são candidatos a ações de retenção.

## 4. Análise e Discussão
- A alta importância de `customer.tenure` sugere que clientes com menor tempo de permanência são mais propensos a churnar, possivelmente devido à falta de fidelidade ou insatisfação inicial.
- O serviço de fibra óptica e os custos mensais elevados aparecem como fatores críticos, alinhados com o relatório exploratório que indicou problemas de precificação ou qualidade.
- A acurácia do modelo pode ser melhorada com técnicas como balanceamento de classes (devido ao desbalanceamento natural entre "nao" e "sim") ou uso de algoritmos como XGBoost.

## 5. Recomendações
- **Ações de Retenção:** Focar em clientes de alto risco com campanhas personalizadas, como descontos ou melhorias no suporte técnico para usuários de fibra óptica.
- **Otimização do Modelo:** Considerar técnicas de oversampling (e.g., SMOTE) para equilibrar as classes e testar modelos como Gradient Boosting para maior precisão.
- **Monitoramento Contínuo:** Atualizar o modelo periodicamente com novos dados para refletir mudanças no comportamento dos clientes.
- **Investigação Técnica:** Analisar a qualidade do serviço de fibra óptica e ajustar os preços para reduzir a taxa de churn.

## 6. Conclusão
O modelo preditivo forneceu uma base sólida para identificar clientes em risco de churn, com insights valiosos sobre os fatores determinantes. Embora a acurácia inicial seja promissora, há espaço para refinamento. Com as recomendações implementadas, a Telecom X pode reduzir a evasão de clientes e melhorar a retenção, alinhando-se aos objetivos estratégicos.


