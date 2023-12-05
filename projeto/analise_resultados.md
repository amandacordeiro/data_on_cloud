### Análise dos resultados

A avaliação dos dois modelos levantaram os seguintes resultados:
![img4](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/6f098e41-458a-48d5-b69b-57fcc5703c4c)

Análise dos resultados para cada modelo:

### Modelo 1:
•	Mean Absolute Error (MAE): 38.46

•	Mean Squared Error (MSE): 3856.71

•	Mean Squared Log Error (MSLE): 0.33

•	Median Absolute Error: 21.85

•	R² Score: 0.48

•	Explained Variance: 0.48

### Modelo 2:
•	Mean Absolute Error (MAE): 37.15

•	Mean Squared Error (MSE): 3357.02

•	Mean Squared Log Error (MSLE): 0.20

•	Median Absolute Error: 22.99

•	R² Score: 0.55

•	Explained Variance: 0.55

### Interpretação das métricas:

1.	Mean Absolute Error (MAE): Representa a média das diferenças absolutas entre os valores previstos e os valores reais. Quanto menor, melhor. O Modelo 2 tem um MAE ligeiramente inferior, indicando um melhor desempenho nessa métrica.
2.	Mean Squared Error (MSE): Representa a média dos quadrados das diferenças entre os valores previstos e os valores reais. Quanto menor, melhor. O Modelo 2 tem um MSE menor, indicando uma melhor capacidade de generalização.
3.	Mean Squared Log Error (MSLE): Mede a média dos quadrados dos logaritmos das diferenças entre os valores previstos e reais. Valores menores indicam uma correspondência mais próxima entre os logs dos valores previstos e reais. O Modelo 2 tem um MSLE menor, sugerindo uma melhor previsão em uma escala logarítmica.
4.	Median Absolute Error: Representa a mediana das diferenças absolutas entre os valores previstos e os valores reais. Semelhante ao MAE, mas menos sensível a valores extremos. Ambos os modelos têm valores semelhantes nesta métrica.
5.	R² Score (Coefficient of Determination): Uma medida da variação total nos dados explicada pelo modelo. Quanto mais próximo de 1, melhor. O Modelo 2 tem um R² Score superior, indicando uma melhor explicação da variação nos dados.
6.	Explained Variance: Representa a proporção da variância na variável dependente que é previsível a partir das variáveis independentes. O Modelo 2 tem uma variância explicada ligeiramente superior.
Em resumo, o Modelo 2 parece ter um desempenho ligeiramente superior com base nessas métricas de avaliação. No entanto, a escolha do melhor modelo pode depender das necessidades específicas do problema e das características dos dados.

