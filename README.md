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
#### Adicionar uma nova categoria de produto
* Para adicionar uma nova categoria é preciso realizar uma requisição do tipo POST no seguinte endereço: http://localhost:3000/categories. No body, corpo da requisição, é necessário ter um código JSON informando o nome da categoria e o seu ícone, que pode ser um emoji.


#### Listar categorias já criadas
* Para listar uma categoria que já existe, é necessário realizar uma requisição do tipo GET no seguinte endereço: http://localhost:3000/categories. Assim, o servidor irá retornar todas as categorias já criadas na aplicação.

#### Adicionar novo produto
* Para adicionar um novo produto é necessário realizar uma requisição do tipo POST no seguinte endereço: http://localhost:3000/products. No corpo da requisição, é necessário conter um _formdata_, que é um conjunto de chaves e valores que representam campos de um elemento form (formulário) e seus valores.

#### Listar produtos já criados
* Para listar os produtos que já foram criados, é necessário realizar uma requisição do tipo GET no seguinte endereço: http://localhost:3000/products. O servidor irá retornar os dados de todos os produtos existentes na aplicação.
