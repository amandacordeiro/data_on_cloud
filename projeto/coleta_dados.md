### Coleta de Dados


Nesta etapa vamos aplicar o Framework Data Management Body of Knowledge (DAMA - DMBoK) para desenvolvermos a governaça dos dados, a estrutura do DAMA-DMBoK é definida em 11 áreas funcionais de gerenciamento (Governança de Dados, Arquitetura de dados, Modelagem de dados e Design, Armazenamento e operações de dados, Segurança de dados, Integração de dados, Documentação, Dados Mestres, DW e BI, Metadados e qualidade dos dados), importante ressaltar que a governança dos dados fica no centro de todas as áreas citadas.






### Arquitetura de dados - Data Lake GCP

![_Diagrama GCP (Google Cloud Platform)](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/00ae8f89-e9f6-4923-9fb5-b16b611a3be2)



### Modelagem de dados e Design


A modelagem de dados será Star Schema

![Database ER diagram (crow's foot)](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/95100e5a-5192-41dd-bded-cf04765a6d4d)


### Armazenamento e operações de dados

O armazenamento final e as operaçoes de dados ocorrerão utilizando SQL.


### Segurança de dados

Os dados coletados são públicos e disponíbilizados pela google, não sendo necessários tomar cuidados extras para estar dentro da LGPD ou GDPN. Em relação ao repositorio dos dados ele estará em nuvem com acesso restrito para as pessoas integrantes do projeto.

#### As demais áreas funcinais de gerenciamnto do DAMA-DMboK já estão sendo contemplandas nas áreas já citadas dentro do escopo do desse projeto.

### Coleta

Os dados financeiros serão coletados na página do google sheets utilizando o seguinte código de referência: `GOOGLEFINANCE(ticker; [attribute]; [start_date]; [end_date|num_days]; [interval])` 

Código utilizado para extração de dados de uma empresa: `=GOOGLEFINANCE("SQIA3";"all";"13/09/2018";"13/09/2023";"DAILY")`

Após retornar os dados basta clicar em `Arquivo` - `Fazer Download` - `Valores separados por vírgula(.CSV)`, dessa maneira é possível extrair os dados brutos para posterior processo de ingestão dos dados em nuvem.
![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/02bbb77d-8a5b-47d5-8122-6815e8098e0a)










Referências bibliográficas: De PAULA, T. & CROCCO, M. (2014). “Flutuações cíclicas e seus efeitos no território:  uma nota sobre a preferência pela liquidez regional”. Anais do 20th APDR Congress.  Évora, Portugal, 2014. [1] Mobile Time. (2023). Bloomberg apresenta sua IA generativa financeira:  BloombergGPT. Disponível  em: https://www.mobiletime.com.br/noticias/03/04/2023/bloomberg-apresenta-suaia-generativa-financeira-bloomberggpt/ HADDAD, P. R. (1989). “Economia regional: teorias e métodos de análise”. Série Estudos  Econômicos e Sociais, Vol. 36. Ed. Banco, do Nordeste. 11 IBGE (2019). PIB avança 1,0%  em 2017 e fecha ano em R$ 6,6 trilhões. Agência de Notícias. Disponível em:  https://agenciadenoticias.ibge.gov.br/agencia-sala-de-imprensa/2013-agencia-denoticias/releases/20166-pib-avanca-1- 0-em-2017-e-fecha-ano-em-r-6-6-trilhoes. [2] Arxiv.org. (2023). BloombergGPT: A Generative Finance Model for Large-Scale Data  Analysis and Forecasting./ Disponível em: https://arxiv.org/pdf/2303.17564.pdf
