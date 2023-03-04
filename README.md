<h1 align="center">Varify</h1>

<p align="center">Esse é o backend da aplicação <b>Varify</b>. O objetivo dessa aplicação é ser uma ferramenta que ajude o desenvolvedor na criação das variáveis globais de estilo no CSS.</p>

<p>Esse repositório foi feito utilizando a base de JSON-Server + JSON-Server-Auth já configurada. (https://github.com/Kenzie-Academy-Brasil-Developers/json-server-base)</p>

## **Endpoints**

A API tem um total de 4 endpoints, podendo registrar usuário, realizar login, registrar as cores favoritas do usuário e buscar as cores favoritas do usuário.

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

<h2 align = "center"> Cores favoritadas </h2>

Para buscar as cores favoritadas por aquele usuário em específico, use o ID dele na rota dessa forma:

`GET /colors{id}`

```
Não é necessário um corpo da requisição.
```

Exemplo de resposta com o id {1}:

`GET /colors{1} - FORMATO DA RESPOSTA - STATUS 200`

```json
[
  [
    {
      "name": "azul",
      "color": "#43231",
      "userId": 1,
      "id": 1
    }
  ]
]
```

<h2 align = "center"> Registrar cores </h2>

O campo userId deve ser preenchido com o id do usuário logado

`POST /colors - FORMATO DA REQUISIÇÃO`

```json
{
  "name": "red",
  "color": "#431312",
  "userId": 1
}
```

Caso dê tudo certo, a resposta será assim:

`POST /colors - FORMATO DA RESPOSTA - STATUS 201`

```json
{
  "name": "vinho",
  "color": "#431312",
  "userId": 1,
  "id": 3
}
```

Feito por Vitor Hugo Mendes
