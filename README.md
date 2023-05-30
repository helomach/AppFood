# App Food
## API de serviço de pedidos de um restaurante
A aplicação trata-se de uma API que pode ser utilizada para clientes realizarem pedidos em determinado restaurante. A API também possibilita que o restaurante cadastre produtos e categorias.

---

## Passo a passo para executar o servidor
* Realizar o download dos arquivos contidos neste repositório;

* Executar o comando `npm install` para instalar os módulos Node necessários para executar a aplicação;
*  **OBS:** É necessário estar na mesma pasta do projeto para que o código funcione.

* Depois, é necessário realizar a inicialização de um container no Docker, para hostear o banco de dados MongoDB;
* **OBS:** Se o sistema operacional utilizado para a execução da aplicação for Windows: é necessário estar com o programa Docker Desktop aberto antes de digitar o comando para iniciar o container. E se o sistema operacional utilizado para a execução da aplicação for Linux: é necessário apenas ter o Docker instalado na máquina;

* Comando `docker run --name 'nome do banco' -p 27017:27017 -d mongo` para iniciar um container Docker

* Comando `npm i -g yarn` para instalar o yarn (gerenciador de pacotes para aplicar comandos prontos ao código de uma aplicação);

* Comando `yarn dev` para inicializar o servidor. Se tudo rodar normalmente, aparecerá a mensagem "🚗Server is runing on http://localhost:8000" no terminal.

* Para realizar as requisições, é necessário ter instalado alguma ferramenta cliente de API Rest, como por exemplo, o Insomnia.

* Com o servidor rodando normalmente, para realizar requisições para a API é necessário criar uma nova request no Insomnia.

---
## Passo a passo para realizar requisições na API

