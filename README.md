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

![Serializable](/Imagens/serializable.jpg"Serializable

















