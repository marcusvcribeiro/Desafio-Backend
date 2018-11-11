
# Desafio Backend

O desafio consiste em criar uma API REST para a loja Snoopeh.de que será consumida por um aplicativo (Android e iOS).

Todos os itens serão colocados em um carrinho do lado do aplicativo e passados para a API para realizar uma transação e-commerce.

### Você tem a liberdade de realizar o desafio com a tecnologia que achar melhor.

Deverá informar quais tecnologias foram usadas, como instalar, rodar e efetuar os acessos no arquivo [`details.txt`].

### Extra
- Utilizar Cache
- Autenticação nas requisições

### POST `/snoopehstore/product`
Esse método deve receber um produto novo e inseri-lo em um banco de dados para ser consumido pela própria API.
```json
{
   "titulo":"Blusa do Imperio",
   "preco":7990,
   "cep":"78993-000",
   "categoria":"Blusa",
   "thumbnailHd":"https://cdn.awsli.com.br/600x450/21/21351/produto/3853007/f66e8c63ab.jpg",
   "date":"26/11/2015"
}
```
| Campo        | Tipo   |
|--------------|--------|
| titulo       | String |
| preco        | int    |
| cep          | String |
| categoria    | String |
| thumbnailHd  | String |
| date         | String |


### GET `/snoopehstore/products`
Esse método da API deve retornar o seguinte JSON
```json
[
  {
    "titulo": "Blusa do Imperio",
    "preco": 7990,
    "cep": "78993-000",
    "categoria": "Blusa",
    "thumbnailHd": "https://cdn.awsli.com.br/600x450/21/21351/produto/3853007/f66e8c63ab.jpg",
    "date": "26/11/2015"
  },
  {
    "titulo": "Blusa Han Shot First",
    "preco": 7990,
    "cep": "13500-110",
    "categoria": "Blusa",
    "thumbnailHd": "https://cdn.awsli.com.br/1000x1000/21/21351/produto/7234148/55692a941d.jpg",
    "date": "26/11/2015"
  },
  {
    "titulo": "Sabre de luz",
    "preco": 150000,
    "cep": "13537-000",
    "categoria": "Sabre",
    "thumbnailHd": "http://www.obrigadopelospeixes.com/wp-content/uploads/2015/12/kalippe_lightsaber_by_jnetrocks-d4dyzpo1-1024x600.jpg",
    "date": "20/11/2015"
  }
]
```
| Campo        | Tipo   |
|--------------|--------|
| titulo       | String |
| preco        | int    |
| cep          | String |
| categoria    | String |
| thumbnailHd  | String |
| date         | String |


Após o usuário adicionar todos os itens desejados no carrinho, ele finalizará a compra.
Para isso, você precisará fazer o método `buy` na sua API.

### POST `/snoopehstone/buy`
Esse método irá receber os dados da compra, junto com os dados do usuário.
```json
{
   "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
   "client_name":"Luke Skywalker",
   "total_to_pay":1236,
   "credit_card":{
      "card_number":"1234123412341234",
      "value":7990,
      "cvv":789,
      "card_holder_name":"Luke Skywalker",
      "exp_date":"12/24"
   }
}

```

+ Transaction

| Campo        | Tipo       |
|--------------|------------|
| client_id    | String     |
| client_name  | String     |
| total_to_pay | int        |
| credit_card  | CreditCard |

+ CreditCard

| Campo            | Tipo   |
|------------------|--------|
| card_number      | String |
| card_holder_name | String |
| value            | int    |
| cvv              | int    |
| exp_date         | String |


### GET `/snoopehstore/history`
Esse método deve retornar todos as compras realizadas na API
```json
[
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   },
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   },
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   }
]
```
| Campo            | Tipo   |
|------------------|--------|
| card_number      | String |
| cliend_id        | String |
| value            | int    |
| date             | String |
| purchase_id      | String |

### GET `/snoopehstore/history/{clientId}`
Esse método deve retornar todos as compras realizadas na API por um cliente específico
```json
[
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   },
   {
      "client_id":"7e655c6e-e8e5-4349-8348-e51e0ff3072e",
      "purchase_id":"569c30dc-6bdb-407a-b18b-3794f9b206a8",
      "value":1234,
      "date":"19/08/2016",
      "card_number":"**** **** **** 1234"
   }
]
```





