# Análise de Cancelamento de Clientes (Churn)

Análise exploratória e modelo de referência para entender quem cancela uma assinatura e transformar os dados em regras de retenção que um time de negócio consiga aplicar.

## Principais resultados

- Taxa geral de cancelamento: **56,7%** (48.527 clientes após a limpeza).
- **Cinco regras simples** levam a ~100% de cancelamento: contrato mensal, mais de 4 ligações ao call center, mais de 20 dias de atraso, idade acima de 50 anos e gasto total abaixo de 500.
- Essas regras cobrem 54,9% da base e capturam **96,1% dos cancelamentos**. Quem não cai em nenhuma delas cancela só 4,8%.
- As regras (F1 = 0,979) superam a regressão logística (F1 = 0,907), e o Gradient Boosting é quase perfeito (AUC 1,000), o que indica padrões muito marcados na base.

## Metodologia

1. **Qualidade dos dados:** remoção de 1.469 duplicatas exatas e 4 linhas com nulos; correção de tipos.
2. **Análise exploratória:** taxa de cancelamento por categoria e por faixa de cada variável numérica.
3. **Descoberta de regras:** varredura de limiares para achar os cortes em que a taxa chega a ~100%.
4. **Modelagem de referência:** `Pipeline` do scikit-learn (padronização + one-hot) com divisão 80/20 estratificada. Comparação entre baseline, regressão logística, Gradient Boosting e as regras de negócio.
5. **Recomendações:** uma ação de retenção sugerida para cada sinal de risco.

## Estrutura do repositório

```
.
├── analise_cancelamentos.ipynb   
├── cancelamentos_sample.csv                       
├── requirements.txt
└── README.md
```

## Tecnologias

Python, pandas, NumPy, Matplotlib, Seaborn, scikit-learn.

## Limitações

- Amostra única, sem dimensão temporal; correlação não é causalidade.
- Os padrões quase determinísticos sugerem dados sintéticos, então as métricas altas não devem ser esperadas em dados reais.
- Não há custo de retenção nem valor do cliente, então o retorno financeiro das ações não foi estimado.


## Autor

**Gabriell Soriano** · [LinkedIn](https://www.linkedin.com/in/gabriell-soriano-270419232/)
