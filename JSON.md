![Logo Digital Banks](https://i.imgur.com/LI7isN8.png?raw=true)
# Integração por envio de JSON
O envio de arquivo do tipo JSON se dá por meio de acesso interno na conta do cliente. O arquivo de boletos emitidos deverá ser enviado de acordo com o padrão apresentado no arquivo modelo `modelo_json_boleto.json` na pasta de `exemplos` neste repositório, você pode acessar [clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/tree/master/exemplos).

Os campos são **TODOS OBRIGATÓRIOS** e abaixo você tem mais informações sobre cada campo disponível.


## Campos/Colunas do arquivo
Exemplo de arquivo:
```json
{
  "registros": 1,
  "boletos": [
    {
      "versao": 1,
      "sacador": "JOSE ALFREDO",
      "cpfCnpj": "000.000.000-00",
      "nomeRua": "R EXEMPLO DE RUA",
      "bairro":  "BAIRRO EXEMPLO",
      "cep": "00000-000",
      "cidade": "ITAJAI",
      "estado": "SC",
      "vencimento": "2019-10-01",
      "valor": 19.80,
      "seuId": "ABC000000000123"
    }
  ]
}
```

Perceba que o campo `boletos` é do tipo `array`, aqui você irá enviar todos os registros a serem processados pelo sistema.

A `versao` do boleto, visa identificar os campos obrigatórios para a emissão de boletos. Consulte a versão disponível no momento da sua integração.

[Mais detalhes dos campos você pode acessar clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/blob/master/FIELDS.md)

## Download do retorno
Após o processamento do arquivo, o sistema irá permitir o download de um novo arquivo, também na conta do cliente, de um arquivo `JSON` com as informações do boleto. Você pode baixar o arquivo exemplo com nome `modelo_json_boleto_retorno.json` na pasta de `exemplos` neste repositório, você pode acessar [clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/tree/master/exemplos).

Exemplo de arquivo:
```json
{
  "registros": 1,
  "boletos": {
    "versao": 1,
    "cpfCnpj": "000.000.000-00",
    "banco": "BANCO DO BRASIL",
    "linhaDigitavel": "000000000000000000000000000000000000000",
    "seuId": "ABC000000000123",
    "urlImpressao": "https://server.nomedainstituicao.com/api/exemplo/emissao/boleto?code=473927439s9d8dddaf"
  }
}
```

Exemplo de arquivo contendo registro com erro:
```json
{
  "registros": 1,
  "boletos": {
    "versao": 1,
    "cpfCnpj": "000.000.000-00",
    "banco": "",
    "linhaDigitavel": "",
    "seuId": "ABC000000000123",
    "urlImpressao": "",
    "erro": true
  }
}
```

[Mais detalhes dos campos você pode acessar clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/blob/master/FIELDS.md)
