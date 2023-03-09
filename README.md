<h1 align="center">Varify</h1>

<p align="center">Esse é o backend da aplicação <b>Varify</b>. O objetivo dessa aplicação é ser uma ferramenta que ajude o desenvolvedor na criação das variáveis globais de estilo no CSS.</p>

<p>Esse repositório foi feito utilizando a base de JSON-Server + JSON-Server-Auth já configurada. (https://github.com/Kenzie-Academy-Brasil-Developers/json-server-base)</p>

## **Endpoints**

A API tem um total de 4 endpoints, podendo registrar usuário, realizar login, registrar as cores favoritas do usuário e buscar as cores favoritas do usuário.

A URL base da API é: https://json-server-varify.onrender.com/

<h2 align ='center'> Criação de usuário </h2>

`POST /register - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "teste5@mail.com",
  "password": "123456",
  "name": "vitor"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /register - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRlc3RlNUBtYWlsLmNvbSIsImlhdCI6MTY3Nzg4ODA4OCwiZXhwIjoxNjc3ODkxNjg4LCJzdWIiOiI0In0.Z0t1sK-SAPzu3iW99fGNaTOT5t2qx0jiLFNMmRTybBs",
  "user": {
    "email": "teste5@mail.com",
    "name": "vitor",
    "id": 4
  }
}
```

<h2 align = "center"> Login </h2>

`POST /login - FORMATO DA REQUISIÇÃO`

```json
{
  "email": "kenzinho@mail.com",
  "password": "123456"
}
```

Caso dê tudo certo, a resposta será assim:

`POST /login - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImtlbnppbmhvQG1haWwuY29tIiwiaWF0IjoxNjc3ODg4MjM0LCJleHAiOjE2Nzc4OTE4MzQsInN1YiI6IjEifQ.SxCl0IxctXhM9v-pdalG1jPkVoSqAPV6qUuWHQ7ppRE",
  "user": {
    "email": "kenzinho@mail.com",
    "name": "Kenzinho",
    "id": 1
  }
}
```

## Rotas que necessitam de autorização

Rotas que necessitam de autorização deve ser informado no cabeçalho da requisição o campo "Authorization", dessa forma:

> Authorization: Bearer {token}

<h2 align = "center"> Favoritos </h2>

Para buscar as variáveis favoritadas por aquele usuário em específico, use o ID dele na rota dessa forma:

`GET /favorites?userId={id}`

```
Não é necessário um corpo da requisição.
```

Exemplo de resposta com o id {2}:

`GET /favorites?userId=2 - FORMATO DA RESPOSTA - STATUS 200`

```json
{
  "userId": 2,
  "colors": ["#BCECE0", "#36EEE0", "#F652A0", "#4C5270"],
  "titles": [17, 12],
  "texts": [10],
  "radius": [2],
  "id": 3
}
```

<h2 align = "center"> Registrar cores </h2>

O campo userId deve ser preenchido com o id do usuário logado

`POST /favorites - FORMATO DA REQUISIÇÃO`

```json
{
  "userId": 2,
  "colors": ["#050A30", "#000C66", "#0000FF", "#7EC8E3"],
  "titles": [22, 18],
  "texts": [16, 13, 10],
  "radius": [5, 3]
}
```

Caso dê tudo certo, a resposta será assim:

`POST /favorites - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "userID": 2,
  "colors": ["#050A30", "#000C66", "#0000FF", "#7EC8E3"],
  "titles": [22, 18],
  "texts": [16, 13, 10],
  "radius": [5, 3],
  "id": 3
}
```
