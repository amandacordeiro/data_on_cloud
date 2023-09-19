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



### Configuração a Cloud Storage do GCP para criar nosso Data Lake

Crie uma conta GCP utilizando seu e-mail gratuito, a google libera 90 dias e 300 dolares para teste:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/4425d975-a633-4a60-94e9-5f99a150fc7d)

Na barra de pesquisa digite Cloud Storage e clique no serviço:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/2b67d926-6ca9-463b-9620-758c970df380)

Configurando um Bucket, os "Buckets são os recipientes básicos que armazenam seus dados. Tudo o que você armazena no Cloud Storage precisa estar contido em um bucket", clique em criar:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/9c162f69-f2fb-4ed1-81b6-39b6fce2076c)

Digite o nome do projeto e em continuar:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/a82d532e-84be-46b1-89a0-0f8d20917256)

Escolha o local de armazenamento da Cloud, no nosso caso foi escolhido a região us-central1 (iowa) devido ao seu custo baixo:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/c1afc86c-8741-4a53-a66e-354fa558464e)

Escolha uma classe de armazenamento, foi selecionado o standard devido ao baixo volume de dados:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/4a58ce8d-bb60-43be-ab5d-919fabddd2c7)

Controle de acesso foi escolhido o uniforme, pois nossos dados são públicos e não necessitam de cuidados maiores no controle de acesso:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/e2950469-68a0-4e81-a926-984489b24ec6)

Selecione o tipo de proteção (Ferramenta e Criptogradia), optamos por não selecionar nehuma ferramenta e utilizar a chave de criptogfrafia padrão google:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/c3153385-3466-48b7-85ee-4c7b1434ee2f)

Pronto bucket do Cloud Storage configurado, agora basta clicar em permisões e adicinar perfis para acesso ao seu Data Lake GCP(Cloud Storage):

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/b5811a68-11cd-4203-b3cd-1e982042ceeb)

Inserindo arquivos da máquina local no Data Lake, clique em fazer upload dos arquivos:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/885293b2-3fab-4fc2-8d99-f0f230214376)

Selecione o arquivo e clique em abrir:

![image](https://github.com/amandacordeiro/data_on_cloud/assets/50846753/d4e6982f-8c2c-49a6-a9fa-472d4b0cc2d5)
























Referências bibliográficas: 

De PAULA, T. & CROCCO, M. (2014). “Flutuações cíclicas e seus efeitos no território:  uma nota sobre a preferência pela liquidez regional”. Anais do 20th APDR Congress.  Évora, Portugal, 2014. [1] Mobile Time. (2023). Bloomberg apresenta sua IA generativa financeira:  BloombergGPT. Disponível  em: https://www.mobiletime.com.br/noticias/03/04/2023/bloomberg-apresenta-suaia-generativa-financeira-bloomberggpt/ 

HADDAD, P. R. (1989). “Economia regional: teorias e métodos de análise”. Série Estudos  Econômicos e Sociais, Vol. 36. Ed. Banco, do Nordeste. 11 IBGE (2019). PIB avança 1,0%  em 2017 e fecha ano em R$ 6,6 trilhões. Agência de Notícias. Disponível em:  https://agenciadenoticias.ibge.gov.br/agencia-sala-de-imprensa/2013-agencia-denoticias/releases/20166-pib-avanca-1- 0-em-2017-e-fecha-ano-em-r-6-6-trilhoes. 

Arxiv.org. (2023). BloombergGPT: A Generative Finance Model for Large-Scale Data Analysis and Forecasting./ Disponível em: https://arxiv.org/pdf/2303.17564.pdf
