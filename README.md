# App Food

## Passo a passo para executar o servidor
* Comando **npm install**: para instalar os módulos Node;

* Depois, é necessário realizar a inicialização de um container no Docker, para hostear o banco de dados MongoDB;
* **OBS:** Se o sistema operacional utilizado para a execução da aplicação for Windows: é necessário estar com o programa Docker Desktop aberto antes de digitar o comando para iniciar o container. E se o sistema operacional utilizado para a execução da aplicação for Linux: é necessário apenas ter o Docker instalado na máquina;

* Comando **docker run --name 'nome do banco' -p 27017:27017 -d mongo**: para iniciar um container Docker

* Comando **npm i -g yarn**: para instalar o yarn (gerenciador de pacotes para aplicar comandos prontos ao código de uma aplicação);

* Comando **yarn dev** para inicializar o servidor.

## 

