# Documentação da API do sistema de monitoramento do IGAM.


Exemplo de solicitação da API para envio de leituras de um ponto de captação:


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
