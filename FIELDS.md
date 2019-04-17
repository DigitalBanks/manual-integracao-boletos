![Logo Digital Banks](https://i.imgur.com/LI7isN8.png?raw=true)
# Campos padrões para troca de arquivos

## Arquivo de remessa
**Detalhes dos campos**
* `registros` - `int` - Total de boletos no arquivo, repetido em todas as linhas.
* `versao` - `string` - Versão da integração e validação do registro CSV
* `sacador` - Nome do cliente no formato `string` com até `100 caracteres`
* `cpfCnpj` - CPF ou CNPJ no formato `string` com até `18 caracteres`, deve ser enviado **COM MÁSCARA**, ou seja, `000.000.000-00` ou `00.000.000/0000-00`
* `nomeRua` - `string` com até `100 caracteres`
* `bairro` - `string` com até `60 caracteres`
* `cep` - `string` com `9 caracteres` e **COM MÁSCARA**, ou seja, `00000-000`
* `cidade` - `string` com até `60 caracteres`
* `estado` - `string` com `2 caracteres`, ex: `SP`, `SC`, `PR`
* `vencimento` - `date` no formato americano, ex: `2019-01-01`, não pode ser com vencimento inferior ao dia atual ao upload do arquivo.
* `valor` - campo do tipo `float`, ex. `128.0`, `11.99`
* `seuId` - campo `string` com até `60 caracteres`, livre, sem validação, para você identificar seu boleto

## Arquivo de retorno
**Detalhes dos campos**
* `versao` - `string` - Versão da integração e validação do registro CSV
* `cpfCnpj` - CPF ou CNPJ no formato `string` com até `18 caracteres`, deve ser enviado **COM MÁSCARA**, ou seja, `000.000.000-00` ou `00.000.000/0000-00`
* `banco` - `string` com até `60` caracteres com o nome do banco emissor do boleto
* `linhaDigitavel` - `string` com a linha completa para pagamento por digitação
* `seuId` - campo `string` com até `60 caracteres`, livre, sem validação, para você identificar seu boleto
* `urlImpressao` - Link para exibir o boleto na tela para download ou impressão
