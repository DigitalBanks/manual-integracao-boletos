# Integração por envio de CSV
O envio de arquivo do tipo CSV se dá por meio de acesso interno na conta do cliente. O arquivo de boletos emitidos deverá ser enviado de acordo com o padrão apresentado no arquivo modelo `modelo_csv_boleto.csv` na pasta de `exemplos` neste repositório, você pode acessar [clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/tree/master/exemplos).

Os campos são **TODOS OBRIGATÓRIOS** e abaixo você tem mais informações sobre cada campo disponível.

## Campos/Colunas do arquivo
Exemplo de arquivo:
```csv
REGISTROS;VERSAO;SACADOR_STRING;CPF_CNPJ_STRING;NOME_DA_RUA_STRING;BAIRRO_STRING;CEP_STRING;CIDADE_STRING;ESTADO_STRING;VENCIMENTO_DATE(YYYY-MM-DDDD);VALOR_FLOAT;SEU_ID_STRING;
1;1;JOSE ALFREDO;000.000.000-00;R NOME DA RUA;BAIRRO DOMONSTRACAO;00000-000;ITAJAI;SC;2019-06-10;38.91;ABC00000000123;
```

Detalhes dos campos:
* `REGISTROS` - `int` - Total de boletos no arquivo, repetido em todas as linhas.
* `VERSAO` - `string` - Versão da integração e validação do registro CSV
* `SACADOR` - Nome do cliente no formato `string` com até `100 caracteres`
* `CPF_CNPJ` - CPF ou CNPJ no formato `string` com até `18 caracteres`, deve ser enviado **COM MÁSCARA**, ou seja, `000.000.000-00` ou `00.000.000/0000-00`
* `NOME_DA_RUA` - `string` com até `100 caracteres`
* `BAIRRO` - `string` com até `60 caracteres`
* `CEP` - `string` com `9 caracteres` e **COM MÁSCARA**, ou seja, `00000-000`
* `CIDADE` - `string` com até `60 caracteres`
* `ESTADO` - `string` com `2 caracteres`, ex: `SP`, `SC`, `PR`
* `VENCIMENTO` - `date` no formato americano, ex: `2019-01-01`, não pode ser com vencimento inferior ao dia atual ao upload do arquivo.
* `VALOR` - campo do tipo `float`, ex. `128.0`, `11.99`
* `SEU_ID` - campo `string` com até `60 caracteres`, livre, sem validação, para você identificar seu boleto

O arquivo `CSV` deverá conter obrigatoriamente campo `REGISTROS`, pois antes de iniciar o processo de emissão dos boletos, o sistema irá contar o total de registros identificados no arquivos e irá comparar com o total que você informou para garantir que a quantidade de boletos seja a mesma.

Se todos os registros forem válidos e as informações válidas, o sistema iniciará o procedimento de emissão dos boletos junto a instituição financeira.

## Download do retorno
Após o processamento do arquivo, o sistema irá permitir o download de um novo arquivo, também na conta do cliente, de um arquivo `CSV` com as informações do boleto. Você pode baixar o arquivo exemplo com nome `modelo_csv_boleto_retorno.csv` na pasta de `exemplos` neste repositório, você pode acessar [clicando aqui](https://github.com/DigitalBanks/manual-integracao-boletos/tree/master/exemplos).

Exemplo de arquivo:
```csv
VERSAO;CPF_CNPJ;BANCO;LINHA_DIGITAVEL;SEU_ID;URL_IMPRESSAO;
1;000.000.000-00;BANCO DO BRASIL;000000000000000000000000000000000000000;ABC000000000123;https://server.nomedainstituicao.com/api/exemplo/emissao/boleto?code=473927439s9d8dddaf;
```

Detalhes dos campos:
* `VERSAO` - `string` - Versão da integração e validação do registro CSV
* `CPF_CNPJ` - CPF ou CNPJ no formato `string` com até `18 caracteres`, deve ser enviado **COM MÁSCARA**, ou seja, `000.000.000-00` ou `00.000.000/0000-00`
* `BANCO` - `string` com até `60` caracteres com o nome do banco emissor do boleto
* `LINHA_DIGITAVEL` - `string` com a linha completa para pagamento por digitação
* `SEU_ID` - campo `string` com até `60 caracteres`, livre, sem validação, para você identificar seu boleto
* `URL_IMPRESSAO` - Link para exibir o boleto na tela para download ou impressão
