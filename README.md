
# API - Serviço de pedido de comida em restaurante
## Descrição da aplicação
A aplicação consiste em uma API (Interface de Programação de Aplicação) que pode ser utilizada para clientes realizarem pedidos em um restaurante. O estabelecimento, por sua vez, pode cadastrar categorias de alimentos e produtos que serão disponibilizados para seus clientes.

---

### Guia de utilização da aplicação
- Após fazer o download dos arquivos contidos neste repositório, o primeiro passo é instalar os módulos Node necessários para rodar a aplicação, para isso basta digitar o seguinte código no terminal `npm install`. _É necessário estar na pasta do projeto para que o código funcione de maneira adequada._
- O segundo passo é iniciar um container no Docker que servirá de host para o banco de dados Mongo. Para iniciar este container, digite o comando `docker run --name “nome do banco” --volume /save/mongo:/data/db -p 27017:27017 -d mongo` no terminal. _Lembre-se de estar na pasta do projeto antes de digitar o comando._
-  **Sistema operacional Windows:** antes de rodar o código é necessário abrir o Docker Desktop, portanto é necessário ter este programa instalado na máquina.
-  **Sistema operacional Linux:** basta rodar o código com o Docker instalado na máquina.
- Com os módulos Node instalados e com o container Docker rodando, basta usar o código `npm run dev` para subir o servidor. Se tudo estiver certo, a mensagem _"🚗Server is runing on http://localhost:3000"_ deverá aparecer no terminal.
- Como não há um cliente, para fazer as requisições em nosso servidor web é necessário utilizar uma aplicação auxiliar, neste caso será utilizado **Postman**, portanto é necessário ter esse aplicativo instalado em sua máquina.
- Com o servidor rodando, o próximo passo é realizar requisições na API usando essa aplicação auxiliar, para isso, abra uma nova requisição (request) no Postman. Nessa página iremos fazer requisições no servidor.
### Serviços disponíveis na aplicação
#### Adicionar nova categoria
Para adicionar uma nova categoria é necessário realizar uma requisição do tipo **POST** no endereço: **http://localhost:3000/categories**. No corpo da requisição é necessário conter um JSON seguindo a seguinte estutura:
```
{
	"name": " 'nome-da-categoria' ",
	"icon": " 'icone-da-categoria(pode ser um emoji)' "
}
```
#### Listar categorias existentes
Para listar as categorias existentes basta realizar uma requisição do tipo **GET** no endereço: **http://localhost:3000/categories**. O servidor irá retornar os dados de todas as categorias disponíveis na aplicação, incluindo o _id_, que é incuído pelo serviço de banco de dados utilizado pela API.
#### Adicionar novo produto
Para adicionar um novo produto é necessário realizar uma requisição do tipo **POST** no endereço: **http://localhost:3000/products**. No corpo da requisição é necessário conter um tipo de dado que no aplicativo Postman é denominado _"form-data"_, que seria uma espécie de formulário, este deve ser estruturado da seguinte maneira:
|KEYS|VALUES|
|-|-|
|name|'nome-do-produto' |
|description|'descrição-do-produto' |
|image|**arquivo contendo a imagem do produto** 1*|
|price|'preço-do-produto'|
|category|'id-da-categoria-do-produto' 2*|

1* no Postman, é necessário alterar de 'text' para 'file' e então basta adicionar o arquivo contendo a imagem do produto neste campo.\
2* basta listar as categorias existentes e copiar o 'id' da categoria desejada para este campo.
#### Listar produtos existentes
Para listar os produtos existentes basta realizar uma requisição do tipo **GET** no endereço: **http://localhost:3000/products**. O servidor irá retornar os dados de todos os produtos disponíveis na aplicação, incluindo o _id_, que é incuído pelo serviço de banco de dados utilizado pela API.
#### Listar produtos existentes filtrando por categoria
Para listar os produtos existentes filtrando por categorias, basta realizar uma requisição do tipo **GET** no endereço: **http://localhost:3000/categories/'id-da-categoria-desejada'/products**. Para conseguir o id da categoria, basta listar as categorias e copiar o id desejado. Assim, a API irá retornar os dados de todos os produtos daquela categoria disponíveis na aplicação.
#### Adicionar novo pedido
Para criar um novo pedido é necessário realizar uma requisição do tipo **POST** no endereço: **http://localhost:3000/orders**. No corpo da requisição é necessário conter um JSON seguindo a seguinte estutura:
```
{
	"table": " 'nome/numero-da-mesa-que-realizou-o-pedido' ",
	"products": {
		"product": " 'id-do-produto-desejado' ",
		"quantity": 'quantidade-pedida(em numeral, sem aspas)'
	}
}
```
O retorno desta requisição será algo do tipo:
```
{
	"table": " 'nome/numero-da-mesa-que-realizou-o-pedido' ",
	"status": "WAITING",
	"products": [{
		"product": " 'id-do-produto-desejado' ",
		"quantity": 1,
		"_id": "6473bb5b8c8a08b5c5f42121"
	}],
	"_id": "6473bb5b8c8a08b5c5f42120",
	"creatdAt": "2023-05-28T20:36:43.021Z",
	"__v": 0
}
```
Ou seja, além do id que será atribuído ao pedido, também serão atribuídos "status", que por padrão vem como "WAITING" e data de criação, que por padrão vem a data e a hora atual.
#### Listar pedidos
Para listar os pedidos existentes basta realizar uma requisição do tipo **GET** no endereço: **http://localhost:3000/orders**. O servidor irá retornar os dados de todos os pedidos disponíveis na aplicação, incluindo o _id_, que é incuído pelo serviço de banco de dados utilizado pela API e o _status_ que foi incluso automaticamente no momento que o pedido foi adicionado.
#### Alterar status de um pedido
Para alterar o _status_ de um pedido basta realizar uma requisição do tipo **PATCH** no endereço: **http://localhost:3000/orders/'id-do-pedido-que-se-deseja-alterar'**. No corpo da requisição é necessário conter um JSON seguindo a seguinte estutura:
```
{
	"status": " 'status-que-se-deseja-adicionar-ao-pedido' "
}
```
Esse _status_ deve ser apenas uma dessas três opções: "WAINTING", "IN-PRODUCTION" e "DONE".
#### Deletar um pedido
Para deletar um pedido existente, ou melhor, cancelar um pedido, basta fazer uma requisição do tipo **DELETE** no endereço: **http://localhost:3000/orders/'id-do-pedido-que-se-deseja-cancelar'**. Apesar da API não retornar nada (status 204 - No Content), é possível perceber que este item foi deletado corretamente listando os ainda existentes na aplicação.