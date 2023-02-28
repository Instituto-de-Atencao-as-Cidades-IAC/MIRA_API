# 📖 Documentação adicional da API do sistema de monitoramento do IGAM.

## 🚩[Issues](https://github.com/Instituto-de-Atencao-as-Cidades-IAC/MIRA_API/issues)


Neste repositório, através da aba "Issues", existe um espaço para que as dúvidas possam ser compartilhadas e discutidas com a equipe IAC e outros Operadores de Telemetria. Sinta-se à vontade para fazer perguntas e compartilhar suas dúvidas, para que possamos ajudar uns aos outros a utilizar a API de forma mais eficiente.


## ⚒️ [Postman](https://www.postman.com/)

A documentação da API está disponibilizada via [Swagger](https://swagger.io/) pelo seguinte endereço: <https://dev.ecosistemas.meioambiente.mg.gov.br/mira/swagger-ui/index.html>. Para facilitar os testes e executar solicitação a API sem ter que escrever código, o operador de telemetria pode utilizar a ferramenta Postman. Além disso, é possível importar a documentação na ferramenta Postman usando os seguintes tutoriais: 
 - [Import Swagger APIs into Postman](https://www.baeldung.com/swagger-apis-in-postman)
 - [Convert Swagger documentation to Postman Collection](https://medium.com/c-sharp-progarmming/convert-swagger-documentation-to-postman-collection-d67fc95c7b14)

 Através do Postman é possível gerar código para executar as requisições em diversas linguagens. Os exemplos apresentados a abaixo foram gerados pela ferramenta.

## 📓 Exemplo de utilização

## 💧 Demanda hídrica 
### Enviar leituras de um Ponto de Captação pela API

Exemplo de solicitação da API para enviar as leituras de um Ponto de Captação. No exemplo em questão, está sendo enviado as leituras das 07:30 e 07:45 do dia 08/01/2023 para uma bomba que capta 1 m³/s durante 30 minutos.


```bash

curl --location --request POST 'https://dev.ecosistemas.meioambiente.mg.gov.br/mira/api/v1/telemetria/demanda-hidrica' \
--header 'API-Key: <<API Key do Operador de Telemetria>>' \
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


## 🏞️ Disponibilidade hídrica  
### Enviar leituras de uma Estação Secundária pela API


Exemplo de solicitação da API para enviar as leituras de uma Estação Secundária. No exemplo em questão, está sendo enviado as leituras das 07:30 e 07:45 do dia 08/01/2023 para um rio que tem o nível 100 cm na primeira leitura e 110 cm na segunda leitura. Além disso, na leitura das 07:45 o foi possível calcular a curva chave do rio e obter a vazão de 10 m³/s para o nível 110 cm.


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
