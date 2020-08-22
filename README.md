<img alt="GoStack" src="https://storage.googleapis.com/golden-wind/bootcamp-gostack/header-desafios.png" />

<h3 align="center">Desafio 09: Relacionamentos com banco de dados no Node.js</h3>

<p align="center">
  <img alt="GitHub license" src="https://img.shields.io/github/license/andrewdourado/gostack-desafio-typeorm-relations?style=for-the-badge"></a>
</p>

## Descrição 

Nesse desafio foi criado uma aplicação que permite a criação de clientes, produtos e pedidos, onde o cliente pode gerar novos pedidos de compra de certos produtos, como um pequeno e-commerce. Para isso foi necessário fazer uso do Node.js junto ao TypeScript, incluindo o uso de banco de dados com o TypeORM, e relacionamentos ManyToMany!

## Rotas da aplicação

- **`POST /customers`**: A rota recebe `name` e `email` dentro do corpo da requisição, sendo o `name` o 
nome do cliente a ser cadastrado. Ao cadastrar um novo cliente, ele é armazenado dentro do 
banco de dados e retorna o cliente criado. Ao cadastrar no banco de dados, na tabela 
`customers` ele vai possuir os campos `name`,` email`, `created_at`, `updated_at`.

- **`POST /products`**: Essa rota recebe `name`, `price` e `quantity` dentro do corpo da requisição, 
sendo o `name` o nome do produto a ser cadastrado, `price` o valor unitário e `quantity` a quantidade existente em 
estoque do produto. Com esses dados vai ser criado no banco de dados um novo produto com os seguitnes campos: 
`name`, `price`, `quantity`, `created_at`, `updated_at`.

- **`POST /orders/`**: Nessa rota é recebido no corpo da requisição o `customer_id` e um array de `products`, 
contendo o `id` e a `quantity` que você deseja adicionar a um novo pedido. Exemplo de requisição:

```json
{
  "customer_id": "e26f0f2a-3ac5-4c21-bd22-671119adf4e9",
  "products": [
    {
      "id": "ce0516f3-63ae-4048-9a8a-8b6662281efe",
      "quantity": 5
    },
    {
      "id": "82612f2b-3f31-40c6-803d-c2a95ef35e7c",
      "quantity": 7
    }
  ]
}
```

Uma chamada a essa rota retorna os dados do cliente, produtos do pedido e id do pedido, num formato parecido com o seguinte:

```json
{
  "id": "5cbc4aa2-b3dc-43f9-b121-44c1e416fa92",
  "created_at": "2020-05-11T07:09:48.767Z",
  "updated_at": "2020-05-11T07:09:48.767Z",
  "customer": {
    "id": "e26f0f2a-3ac5-4c21-bd22-671119adf4e9",
    "name": "Rocketseat",
    "email": "oi@rocketseat.com.br",
    "created_at": "2020-05-11T06:20:28.729Z",
    "updated_at": "2020-05-11T06:20:28.729Z"
  },
  "order_products": [
    {
      "product_id": "ce0516f3-63ae-4048-9a8a-8b6662281efe",
      "price": "1400.00",
      "quantity": 5,
      "order_id": "5cbc4aa2-b3dc-43f9-b121-44c1e416fa92",
      "id": "265b6cbd-3ab9-421c-b358-c2e2b5b3b542",
      "created_at": "2020-05-11T07:09:48.767Z",
      "updated_at": "2020-05-11T07:09:48.767Z"
    },
    {
      "product_id": "82612f2b-3f31-40c6-803d-c2a95ef35e7c",
      "price": "500.00",
      "quantity": 7,
      "order_id": "5cbc4aa2-b3dc-43f9-b121-44c1e416fa92",
      "id": "ae37bcd6-7be7-47b9-b277-afee35aab4e4",
      "created_at": "2020-05-11T07:09:48.767Z",
      "updated_at": "2020-05-11T07:09:48.767Z"
    }
  ]
}
```

- **`GET /orders/:id`**: Essa rota retorna as informações de um pedido específico, com todas as informações que podem ser recuperadas através dos relacionamentos entre a tabela `orders`, `customers` e `orders_products`.


## Instalação

Para executar este projeto é necessário a instalacão prévia do [Git](https://git-scm.com/downloads "Git download"), 
[Yarn](https://classic.yarnpkg.com/en/docs/install "Yarn download") e 
[NodeJS](https://nodejs.org/ "NodeJS Doc"):

```bash
# Clona este repositório
$ git clone https://github.com/andrewdourado/gostack-desafio-typeorm-relations.git

# Acessa o repositório clonado
$ cd gostack-desafio-typeorm-relations

# Instala as dependências
$ yarn

# Executa o projeto.
$ yarn dev:server
```

## Tecnologias

- <a href="https://nodejs.org/" target="_blank" rel="noopener noreferrer">NodeJS</a>
- <a href="https://www.typescriptlang.org/" target="_blank" rel="noopener noreferrer">TypeScript</a>
- <a href="https://eslint.org/" target="_blank" rel="noopener noreferrer">ESLint</a>
- <a href="https://prettier.io/" target="_blank" rel="noopener noreferrer">Prettier</a>

## Créditos

Este projeto foi desenvolvido durante o Bootcamp GoStack 11 da <a href="https://rocketseat.com.br/" target="_blank" rel="noopener noreferrer">Rocketseat</a>.

## Licença
Esse projeto está sob a licença [MIT](https://github.com/andrewdourado/gostack-desafio-typeorm-relations/blob/master/LICENSE) © [André Dourado](https://github.com/andrewdourado)
