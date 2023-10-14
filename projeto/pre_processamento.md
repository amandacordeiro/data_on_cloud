### Pré-processamento de Dados

Após a coleta devemos realizar um estudo desses dados. Conhecendo melhor os dados que foram coletados, podemos realizar um tratamento de variáveis, padronizar valores e limpar o que não será útil para os próximos passos de análise e treinamento dos algoritmos.



### Preparando o ambiente do BigQuery

Vá para o ambiente do BigQuery no console e selecione o projeto. Após isso, clique nos três pontos ao lado do ID do seu projeto e clique em "Criar conjunto de dados"

![e1](https://i.imgur.com/kTaKbbq.png)

Dê um nome ao seu conjunto de dados. Selecione a mesma região em que os dados estão armazenados no Cloud Storage, deixe o restante da configuração no formato padrão e clique em "Criar conjunto de dados".

![e2](https://i.imgur.com/AoJMQGL.png)

Feito isso, você verá que o conjunto de dados foi criado dentro da pasta do seu projeto. Agora, vamos criar a tabela.

Selecione os três pontos ao lado do conjunto de dados que você criou e clique em "Criar tabela".

![e3](https://i.imgur.com/4LMZNVn.png)

Preencha as informações corretamente.

1. **Projeto** é o ID do seu projeto.
2. **Conjunto** de dados é o nome que você deu ao seu conjunto de dados.
3. **Tabela** é o nome que você quer dar para a sua tabela.

Deixe o restante das configurações como padrão e clique em "Criar tabela".

> O BigQuery contém uma inteligência que já faz automaticamente o tratamento do tipo dos dados durante a criação da tabela. Se por acaso precisar alterar o tipo do dado de alguma tabela, utilize o script abaixo, substituindo e adaptando as variáveis para as informações do seu projeto:
>
> ```
> REPLACE TABLE your_project.your_dataset.new_table AS
> SELECT
>   column1,
>   CAST(column_to_change AS STRING) AS new_column_name,  -- Altere o tipo de dado conforme necessário
>   column3
> FROM
>   your_project.your_dataset.existing_table;
> ```

![e3](https://i.imgur.com/TgJUZaL.png)

Você tem uma tabela criada.

![e333](https://i.imgur.com/xTbrCdY.png)

![e33](https://i.imgur.com/RHzYb6B.png)

A partir da tabela que foi criada, criaremos uma nova tabela que terá o objetivo de extrair unicamente a data, dia, mês, ano, semestre, trimestre e bimestre.

1. Vá para uma query do BigQuery e insira o algoritmo que servirá para a criação da nova tabela.
2. Adicione no algoritmo as informações que devem ser extraídas a partir da tabela e clique em "Executar".

```
CREATE TABLE our-vigil-399400.finance_view.td_tempo AS

SELECT

 DATE(Date) AS data,

 EXTRACT(DAY FROM TIMESTAMP(DATE(Date, 'UTC'))) AS dia,

 EXTRACT(MONTH FROM TIMESTAMP(DATE(Date, 'UTC'))) AS mes,

 EXTRACT(YEAR FROM TIMESTAMP(DATE(Date, 'UTC'))) AS ano,

 CASE 

  WHEN EXTRACT(MONTH FROM TIMESTAMP(DATE(Date, 'UTC'))) <= 6 THEN 'Semestre 1'

  ELSE 'Semestre 2'

 END AS semestre,

 CONCAT('Trimestre ', CAST(CEIL(EXTRACT(MONTH FROM TIMESTAMP(DATE(Date, 'UTC'))) / 3) AS STRING)) AS trimestre,

 CONCAT('Bimestre ', CAST(CEIL(EXTRACT(MONTH FROM TIMESTAMP(DATE(Date, 'UTC'))) / 2) AS STRING)) AS bimestre

FROM

 our-vigil-399400.finance_view.finance_info;
```

![e4](https://i.imgur.com/kjC3aj7.png)

Após criado deverá ser exibido da seguinte forma:

![e44](https://i.imgur.com/YKPOq2Q.png)

![e444](https://i.imgur.com/Zfjk0Vu.png)

Caso tenha tido algum problema durante a execução dos scripts, utilize o comando para deletar a tabela e criar novamente:

```
drop table your_project.your_dataset.your_table;
```

Caso queira verificar a existência de dados nulos, utilize o script:

```
SELECT *
FROM your_project.your_dataset.your_table
WHERE column1 IS NULL
  AND column2 IS NULL
  AND column3 IS NULL;
```

Para excluir os dados nulos, utilize o script para as respectivas colunas que contém dados nulos:

```
REPLACE TABLE your_project.your_dataset.your_table AS
SELECT *
FROM your_project.your_dataset.your_table
WHERE column1 IS NOT NULL
  AND column2 IS NOT NULL
  AND column3 IS NOT NULL;
```

#### That's All Folks :)
