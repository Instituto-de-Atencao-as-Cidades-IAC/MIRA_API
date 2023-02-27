# Documentação da API do sistema de monitoramento do IGAM.


Exemplo de solicitação da API para envio de leituras de um Ponto de Captação:


```bash

curl --location --request POST 'https://dev.ecosistemas.meioambiente.mg.gov.br/mira/api/v1/telemetria/demanda-hidrica' \
--header 'API-Key: <<SUA API Key>>' \
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

Exemplo de solicitação da API para envio de leituras de uma Estação Secundária:

```bash
curl --location --request POST 'http://localhost:8082/api/v1/telemetria/disponibilidade-hidrica' \
--header 'API-Key: 527607340001727cea3aa5-8f97-442c-972c-e9f9313e71c6' \
--header 'Content-Type: application/json' \
--header 'Accept: */*' \
--data-raw '[
    {
        "rotulo": "OPN3-00001",
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



