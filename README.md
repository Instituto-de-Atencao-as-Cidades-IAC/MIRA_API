# 📖 API do Monitoramento Remoto Integrado das Águas - MIRA.

## ❓[1. Issues](https://github.com/Instituto-de-Atencao-as-Cidades-IAC/MIRA_API/issues)


Neste repositório, a aba "Issues" possibilita que as dúvidas possam ser compartilhadas e discutidas com a equipe IAC, além de outros Operadores de Telemetria. Sinta-se à vontade para fazer perguntas e compartilhar suas dúvidas.


## ⚒️ [2. Postman](https://www.postman.com/)

A documentação da API está disponibilizada via [Swagger](https://swagger.io/) pelo seguinte endereço: <https://dev.ecosistemas.meioambiente.mg.gov.br/mira/swagger-ui/index.html>. De modo a facilitar os testes de solicitação à API, sem ter que escrever o código, o Operador de Telemetria pode utilizar a ferramenta Postman. Dito isso, é possível importar a documentação na ferramenta Postman usando os seguintes tutoriais: 
 - [Import Swagger APIs into Postman](https://www.baeldung.com/swagger-apis-in-postman)
 - [Convert Swagger documentation to Postman Collection](https://medium.com/c-sharp-progarmming/convert-swagger-documentation-to-postman-collection-d67fc95c7b14)

Ao utilizar a ferramenta Postman é possível gerar um código para executar as requisições na API em diversas linguagens. A seguir, exemplos que foram gerados com a ferramenta:

## 📓 3. Exemplos de Utilização

### 💧 3.1 Demanda Hídrica 
#### Enviar leituras de um Ponto de Captação pela API

Exemplo de solicitação da API para enviar as leituras de um Ponto de Captação. No exemplo em questão, estão sendo enviadas as leituras de 07:30 (UTC-03:00) e 07:45(UTC-03:00) do dia 08/01/2023, considerando uma bomba que iniciou sua captação às 7:15(UTC-03:00) e captou 1 m³/s durante 30 minutos.


```bash

curl --location --request POST 'https://dev.ecosistemas.meioambiente.mg.gov.br/mira/api/v1/telemetria/demanda-hidrica' \
--header 'API-Key: <<API Key do Operador de Telemetria, obtida no MIRA>>' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--data-raw '[
    {
        "rotulo": "<<Rótulo do Ponto de Captação>>",
        "leituras": [
            {
                "horario": "2023-01-08T10:30:00Z",
                "vazao": 1,
                "duracao": 900,
                "volume": 900
            },
            {
                "horario": "2023-01-08T10:45:00Z",
                "vazao": 1,
                "duracao": 900,
                "volume": 1800
            }
        ]
    }
]'


```


### 🏞️ 3.2 Disponibilidade Hídrica  
#### Enviar leituras de uma Estação Secundária pela API


Exemplo de solicitação da API para enviar as leituras de uma Estação Secundária. No exemplo em questão, estão sendo enviadas as leituras de 07:30(UTC-03:00) e 07:45(UTC-03:00) do dia 08/01/2023 para um curso d'água que tem o nível 100 cm na primeira leitura e 110 cm na segunda leitura. Caso também possua os dados de vazão, é possível enviar pela API conforme ilustrado na leitura das 07:45(UTC-03:00):
```bash
curl --location --request POST 'https://dev.ecosistemas.meioambiente.mg.gov.br/mira/api/v1/telemetria/disponibilidade-hidrica' \
--header 'API-Key: <<API Key do Operador de Telemetria>>' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--data-raw '[
    {
        "rotulo": "<<Rótulo da Estação Secundária>>",
        "leituras": [
            {
                "horario": "2023-01-08T10:30:00Z",
                "nivel": 100
            },
            {
                "horario": "2023-01-08T10:45:00Z",
                "nivel": 110,
                "vazao": 10
            }
        ]
    }
]'

```
