# API REST COM SPRING BOOT - SWAGGER, POSTGRES REMOTO COM HEROKU

Curso Michelli Brito - API REST com Spring Boot, Swagger, Postgres Remoto (Heroku)
Vídeos publicados em: 14 de agosto de 2018.

## Tecnologias utilizadas no Projeto

Java 8 (Usado no Curso) eu vou utilizar o Java 17.
Eclipse IDE for Java EE Developers Oxygem M2 64 bits (Usado no curso) eu uso o STS - Spring Tool Suite.
Spring Boot 2.0.4 no curso, eu vou utilizar o Spring Boot 3.0.2

## Início

Spring Initializr - https://start.spring.io

## Heroku agora é paga

Surgiu um comunicado em 25 de Agosto de 2022 que a Heroku vai acabar com os planos gratuítos nos próximos meses. 
Estou no dia 29/01/2023 e realmente não tem mais planos gratuítos.

Achei um vídeo no youtube que o Youtuber oferece 3 alternativas gratuítas: https://www.youtube.com/watch?v=uJiuOUrg_3w


**Netlify** - https://www.netlify.com/ - também tem integração com Git e Github para fazer a manutenção de toda sua aplicação.
Testei e é inútil para minha finalidade. Não tem um servidor de aplicação para rodar spring boot.

**CapRover** - OpenSource - https://caprover.com/ - Free and Open Source PaaS. Posso utilizar na minha própria infra, servidor local. (localhost ou web).
No GitHub tem o fonte: https://github.com/caprover/caprover.

**PaaS** - Plataforma como Serviço.

**Catalyst** - Plataforma PaaS - https://catalyst.zoho.com/ - Free e valores baixos se escalar.

**Fly.io** - https://fly.io/ -
Vídeo de um Youtuber demonstrando: https://www.youtube.com/watch?v=b5q3Nc2iWCw

**Railway** - https://railway.app/ -

Outra Alternativa são as nuvens: AWS, Azure e GCP - Nuvem da Google.

O que estou vendo ao pesquisar que o serviço precisa ter recursos de API, Ambiente de desenvolvimento integrado, Depuração, Controle de Fonte, Monitoramento.

E pelo que pesquisei, não há suporte a Ambiente de Desenvolvimento Integrado nos sites encontrados, exceto Heroku.

Neste site temos os comparativos de alguns sites e nuvens: https://www.capterra.com.br/alternatives/158191/heroku

## MongoDB na Nuvem - MongoLab

MongoLab - https://mlab.com/ - MongoDB na Nuvem.
Login: https://account.mongodb.com/account/login
Joel@2240
crudapi - joelguarulhos  
senha - joel2240
Server: crudapi.gnicsu3.mongodb.net
Replica Set Name:atlas-25t4rl-shard-0

mongodb+srv://joelguarulhos:joel2240@crudapi.gnicsu3.mongodb.net/?retryWrites=true&w=majority


Replica Set Name: atlas-25t4rl-shard-0
SRV Service Name (opcional): mongodb
Connection Type: DNS Seedlist (mongo = srv connections)
User Name: joelguarulhos
Password: joel2240
Authentication DB: admin
mongodb-driver-core-4.8.2]

mongodb+srv://joelguarulhos:<password>@crudapi.gnicsu3.mongodb.net/?retryWrites=true&w=majority
mongodb+srv://joelguarulhos:<password>@crudapi.gnicsu3.mongodb.net/?retryWrites=true&w=majorityprivate String host;

private int port = DBPort.PORT;

private String uri = "mongodb://localhost/test";

private String database;

private String gridFsDatabase;

private String username;

private char[] password;

## Model

* @Entity - Informa que é uma Entidade para o Spring Boot
* @Table - Informa o nome da Tabela
* @Id - Obrigatório
* @GeneratedValue(strategy=GenarationType.AUTO) - AutoIncremento na Tabela.

public class Produto implements Serializable - o implements Serializable gera um long

O Serializable gera um hash mantendo uma versão da classe.

![Serializable](/Imagens/serializable.jpg "Serializable")

## Configurando o banco de dados

Em resources tem um arquivo chamado application.properties:

server.port=8084
spring.jpa.properties.hibernate.jdbc.lob.non_contextual_creation=true

### Banco local - Joel
spring.datasource.url=jdbc:postgresql://localhost:5432/produtos-apirest
spring.datasource.username=postgres
spring.datasource.password=joel@2240
spring.jpa.hibernate.ddl-auto=update 

Essa última linha spring.jpa.hibernate.ddl-auto=update  fará que na inicialização da aplicação, que seja criado a tabela TB_Produtos.
Eu criei no banco antes produtos-apirest (não sei se é necessário).

## Postgres

Posso utilizar o editor pgAdmin 4 ou o SQL Shell (psql).

**SQL Shell:**

![SQL_Shell](/Imagens/SQL_Shell.jpg "SQL_Shell")

**pgAdmin 4:**

![pgAdmin](/Imagens/pgAdmin.jpg "pgAdmin")

### Comandos do Postgres

-- alter sequence tb_produto_seq increment by 1;

--select * from tb_produto;
--select nextval('tb_produto_seq')
--ALTER SEQUENCE tb_produto_seq RESTART;
-- ALTER SEQUENCE tb_produto_seq RESTART WITH 1;
--UPDATE t SET idcolumn=nextval('tb_produto_seq');
--truncate table tb_produto;
-- ALTER SEQUENCE tb_produto_seq RESTART WITH 1
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'samsung s8',1.00,2599.00);
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'notebook lenovo ideapad320',2.00,3500.00);
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'Mac Book',1.00,8000.00);
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'Iphone 8',2.00,4500.00);
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'notebook lenovo ideapad320',1.00,1500.00);
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'SmartTV LG 50',1.00,3550.00);
insert into tb_produto(id, nome,quantidade, valor) values (nextval('tb_produto_seq'),'SmartTV LG 65',1.00,4990.00);

--select currval('tb_produto_seq')

SELECT last_value FROM tb_produto_seq;

--select setval('tb_produto_seq',7)

## Postman - Endpoints

* **GetMapping:** - http://localhost:8084/api/produtos

![GetProdutos](/Imagens/GetProdutos.jpg "GetProdutos")

* **GetMapping -  by ID:** - http://localhost:8084/api/produtos/1

![GetProdutosporid](/Imagens/GetProdutoporid.jpg "GetProdutosporid")

Aqui há um ponto importante: 

O Spring Boot se coloco findbyid ele pede para colocar Optional. E antes era findOne que foi depreciado.

![Findbyid](/Imagens/Findbyid.jpg "Findbyid")

* **PostMapping:**

![PostMapping](/Imagens/PostMapping.jpg "PostMapping")

* **DeleteMapping:**

![DeleteMapping](/Imagens/DeleteMapping.jpg "DeleteMapping")

* **PutMapping:** 

![PutMapping](/Imagens/PutMapping.jpg "PutMapping")





















