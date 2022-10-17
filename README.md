# HATEOAS
>  *Apresentar uma visão geral sobre o HATEOAS, incluindo um estudo de caso implemenando o HATEOAS no projeto DSMovie*

## Visao Geral HATEOAS

### Introdução

- HATEOAS é um acrônimo para *Hypermedia as the Engine of Application State*, traduzido para Hipertexto como motor de estado da aplicação.
- É um importante princípio/constraint do REST que implica que uma API deve ter uma espécie de guia para mostrar aos clientes e usuários, como percorrer pelos recursos que compõem esta API.
- **Análogia:** Ao navegar em uma página web, podemos acessar diferentes páginas por meio de hyperlinks. Desta forma, podemos a partir de um link inicial, acessar diferentes links relacionados. 
- Desta forma, usamos o HATEOAS com o intuito de saber qual o próximo passo após a requisição em um determinado recurso e qual a URI deste recurso.

### Exemplo

- Requisição do tipo GET ao recurso accounts para solicitar os dados da conta de id 12345
```http
GET /accounts/12345 HTTP/1.1
Host: bank.example.com
```

- Resposta contendo os dados da conta id 12345

```http
HTTP/1.1 200 OK

{
    "account": {
        "account_number": 12345,
        "balance": {
            "currency": "usd",
            "value": 100.00
        },
        "links": {
            "deposits": "/accounts/12345/deposits",
            "withdrawals": "/accounts/12345/withdrawals",
            "transfers": "/accounts/12345/transfers",
            "close-requests": "/accounts/12345/close-requests"
        }
    }
}
```
* Retirado de https://en.wikipedia.org/wiki/HATEOAS

### Características e discussões sobre o HATEOAS
- Em teoria, uma API só pode ser considerada RESTFull, caso a mesma implemente HATEOAS. Isso é o que define Roy Fielding, dentre outros pesquisadores.
- Na prática, o mercado ainda está em um nível de maturidade um pouco menor. A maioria das APIs que nós vamos encontrar, não utilizam HATEOAS. E está tudo certo!





## Estudo de caso: Implementando HATEOAS no projeto DSMovie

