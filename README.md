A simple example of a CRUD application in Java using Spring Boot, Hibernate, Thymeleaf and Angular 5.


## 1. Análise

Na análise deve-se fazer o levantamento de requisitos, com o objetivo de apresentar as principais necessidades do cliente.

## 1.1 Requisitos

Implementar uma solução para controle de estacionamento, os requisitos necessários para a solução são:
• Autenticação via banco de dados
• Cadastro de Clientes (Nome, CPF, Telefone)
• Cadastro de Veículos (Placa, Modelo, Cor)
• Cadastro de Pátio (Descrição, Número de Vagas, Taxa/hora)
• Estacionamento: Registrar entrada e saída de veículos tempo de permanência e valor a ser pago. 
• Exibir um dash em tela com o total de vagas ocupadas e total livre.

## 1.2 Diagrama de Classes

O Diagrama de Classes abaixo foi feito com base nos requisitos.
![Alt text](./der.png?raw=true "DER")

## 1.3 Observações

Não foi criada uma classe telefone pois pressumiu-se que o cliente possui apenas um único telefone.
Todos os relacionamentos foram feitos de forma bidirecional, por exemplo, Veiculo possui uma variável cor, e Cor possui uma variável List<Veiculo>.
Na classe Estacionamento o tempo de permanência não foi salvo no Banco de Dados pois é uma variável derivada que pode ser calculada facilmente através da entrada e saída do veículo. No entanto, foi criada a variável valorPago pois a taxaHora pode mudar e não foi decidido armazenar o histórico de mudanças das taxas.
A escolha de agregação foi feita quando a remoção de um registro na Classe container não implica na remoção da classe contida, por exemplo: a remoção de Veiculo não implica em remoção de Cor, portanto é uma agregação e não uma composição.
Pressumiu-se que o veículo somente pertence a um único cliente, caso o veículo seja de mais de um cliente ele será armazenado de forma repetida no Banco de Dados.

## 2. Projeto

No projeto deve-se escolher quais ferramentas, frameworks e linguagens devem ser utilizadas para criar uma solução baseada no problema identificado na etapa de análise. As tecnologias (open-source) escolhidas foram: 
• Java 8: para desenvolver o Backend (servidor);
• Spring Boot: para integrar os Frameworks e Ferramentas do Java;
• Hibernate: Framework para salvar os objetos no Banco de Dados;
• Angular 2+: para desenvolver o Frontend (telas);
• Bootstrap com CSS Meta Queries: controlar responsividade (versão mobile das telas);
• PostgreSQL: Sistema Gerenciador de Banco de Dados;
• Lombok: para otimizar o código Java.
	Algumas decisões de arquitetura:
• Uso de GenericDAO.java para persistência de objetos no Banco de Dados,
• Uso de GenericController.java para a criação de controladores MVC.
• Uso de Maven: para baixar todos os frameworks utilizados no Java.
• Não foi criada uma camada de serviço e repositório, para simplificar a arquitetura e não haver necessidade a priori.
• Uso de generic.component.ts no Frontned para efetuar o CRUD básico das telas.
• Uso de generic.service.ts no Frontend para efetuar as requisições HTTP com JSON do CRUD básico.

## 3. Instalação
Os links para instalação do software são apresentador a seguir.
3.1 Instalar JDK do Java (Versão 8):
http://www.oracle.com/technetwork/pt/java/javase/downloads/jdk8-downloads-2133151.html

3.2 Instalar Eclipse IDE for Java EE Developers (Versão Photon):
http://www.eclipse.org/downloads/eclipse-packages/

3.3 Instalar PostgreSQL (Versão 9.6 ou superior):
https://www.postgresql.org/download/windows/

3.4 Instalar Atom:
https://atom.io

3.5 Instalar Node.js e NPM (LTS):
https://nodejs.org/en/download

3.6 Instalar Angular CLI globalmente:
npm install -g npm
npm install -g @angular/cli@latest

3.7 Criar projeto
cd \
ng new estacionamento-frontend
cd estacionamento-frontend

3.8 Instalar módulos dentro da pasta angular-crud do projeto:
npm install --save @angular/material @angular/cdk
npm install --save angular/material2-builds angular/cdk-builds
npm install --save @angular/animations
npm install --save hammerjs
npm install --save bootstrap
npm install --save @ng-bootstrap/ng-bootstrap
npm install --save ng2-currency-mask
npm install --save web-animations-js
npm audit fix –force

3.9 Adicionar as 3 linhas abaixo dentro da tag “styles” que fica dentro do arquivo angular.json (removendo a linha “styles.css”:

"styles": [
              "src/styles.scss",
              "./node_modules/bootstrap/dist/css/bootstrap.css",
              "./src/app/util/tema.scss"
            ],

Obs.: Em caso de erro remover a pasta node_modules e digitar:
npm install
npm link
Obs.: Para executar o Angular:
ng serve --open

3.10 Criar banco de dados estacionamento no PostgreSQL

3.11 Instalar lombok por fora do Eclipse
Dar update maven
Dar clean no projeto

3.12 Foi utilizado o Spring Initializr (https://start.spring.io) para a criação inicial do projeto Maven:

## Screenshots

![Alt text](https://github.com/jairabu/estacionamento/blob/master/dash.PNG?raw=true "Dashboard")

![Alt text](https://github.com/jairabu/estacionamento/blob/master/estacionamentos.PNG?raw=true "Estacionamentos")

![Alt text](https://github.com/jairabu/estacionamento/blob/master/listagem.PNG?raw=true "Listagem")

![Alt text](https://github.com/jairabu/estacionamento/blob/master/mobile.PNG?raw=true "Estacionamentos Mobile")



## Creator

**Jair Alarcón**

- E-mail: jairabu@gmail.com
- LinkedIn: https://www.linkedin.com/in/jair-alarc%C3%B3n-84067b13/

- Facebook: www.facebook.com/jairabu
- Instagram: https://www.instagram.com/jairabu
- Github: https://github.com/jairabu
