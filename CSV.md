![Logo Digital Banks](https://i.imgur.com/LI7isN8.png?raw=true)
# Integração por envio de CSV
O envio de arquivo do tipo CSV se dá por meio de acesso interno na conta do cliente. O arquivo de boletos emitidos deverá ser enviado de acordo com o padrão apresentado no arquivo modelo `modelo_csv_boleto.csv` na pasta de `exemplos` neste repositório, você pode acessar [clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/tree/master/exemplos).

Os campos são **TODOS OBRIGATÓRIOS** e abaixo você tem mais informações sobre cada campo disponível.

## Campos/Colunas do arquivo
Exemplo de arquivo:
```csv
registros;versao;sacado;cpfCnpj;nomeRua;bairro;cep;cidade;estado;vencimento;valor;seuId;
1;1;JOSE ALFREDO;000.000.000-00;R NOME DA RUA;BAIRRO DOMONSTRACAO;00000-000;ITAJAI;SC;2019-06-10;38.91;ABC00000000123;
```

[Mais detalhes dos campos você pode acessar clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/blob/master/FIELDS.md)

O arquivo `CSV` deverá conter obrigatoriamente o campo `registros`, pois antes de iniciar o processo de emissão dos boletos, o sistema irá contar o total de registros identificados no arquivos e irá comparar com o total que você informou para garantir que a quantidade de boletos seja a mesma.

Se todos os registros forem válidos e as informações válidas, o sistema iniciará o procedimento de emissão dos boletos junto a instituição financeira.

## Download do retorno
Após o processamento do arquivo, o sistema irá permitir o download de um novo arquivo, também na conta do cliente, de um arquivo `CSV` com as informações do boleto. Você pode baixar o arquivo exemplo com nome `modelo_csv_boleto_retorno.csv` na pasta de `exemplos` neste repositório, você pode acessar [clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/tree/master/exemplos).

Exemplo de arquivo:
```csv
versao;cpfCnpj;banco;linhaDigitavel;seuId;urlImpressao;
1;000.000.000-00;BANCO DO BRASIL;000000000000000000000000000000000000000;ABC000000000123;https://server.nomedainstituicao.com/api/exemplo/emissao/boleto?code=473927439s9d8dddaf;
```

[Mais detalhes dos campos você pode acessar clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/blob/master/FIELDS.md)
