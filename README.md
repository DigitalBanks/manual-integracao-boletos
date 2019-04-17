![Logo Digital Banks](https://i.imgur.com/0eHP030.jpg?raw=true)
# Manual de Integração de Boletos
As integrações de boleto da Digital Banks visam facilitar e padronizar a emissão de boletos e outros tipos de integrações com sistemas de terceiros.

Atualmente existem dezenas de formas de emitir um boleto, dezenas de serviços, por isso, todos os arranjos pertencentes a rede Digital Banks utilizam este padrão, facilitando para desenvolvedores e empresas homologarem e integrarem em suas soluções.

## Tipos de integração
Atualmente a Digital Banks está disponibilizando 3 tipos de integração de boletos, ambos em fase de homologação junto aos clientes, são elas:

* [Emissão em lotes por CSV](https://github.com/DigitalBanks/manual-integracao-boletos/blob/master/CSV.md)
* Emissão em lotes por JSON
* Emissão em lotes por API

Conforme cada um dos tipos for homologado, iremos acrescentar informações aqui no wiki deste repositório do `Github` para facilitar o uso e consulta dos desenvolvedores.

Este repositório irá armazenar algumas demonstrações e arquivos exemplos para utilizar durante sua homologação.

## E se eu tiver dúvidas?
Você pode abrir uma `issue` diretamente neste repositório, desde que já tenha uma conta corrente ativa em qualquer arranjo integrante da rede `Digital Banks`, pois você precisará de um token de emissão de boletos para executar seus `request` para o servidor.

## E se surgir um erro não documentado no manual?
Nosso sistema está em constante evolução e nos preocupamos em manter os manuais atualizados, contudo algum erro pode passar despercebido, nossa equipe trabalha constantemente para melhorar nossas `APIs` e fazer os erros mais amigáveis possíveis.

Se você se deparar com algum erro inesperado, abra uma `issue` neste repositório contendo as seguintes informações:

* URL que utilizou
* Dados enviados para o servidor (não esqueça de ocultar/remover dados confidenciais como o `token de emissao de boletos` se utilizado no tipo de integração escolhida)
* Resposta do servidor
* Linguagem utilizada para o `request`
* O trecho do código que você utilizou para fazer o `request`

E envie um arquivo `.txt` com os dados `EXATOS` para o email homologacao@digitalbankscorp.com para que a equipe possa acompanhar o seu caso, e caso haja a necessidade de reproduzir o seu `request`, os dados do arquivo enviado por email serão utilizados.

## Finalizei a homologação, e agora?
Nós recomendamos que você gere ou solicite um novo `token de emissão de boletos` se for necessário no tipo de integração escolhida antes de colocar em produção para que não haja riscos de durante o desenvolvimento alguém ter comprometido o seu `token`

## Posso contribuir?
Sim! Se você desejar, poderá fazer um `pull request` para este repositório com um código demonstrativo com correções, melhorias ou sugestões.

A Digital Banks preza pela comunidade, vem participando de diversos projetos Open Source pois tem como visão ajudar a comunidade de desenvolvedores a criar coisas novas.

## Como contribuir?
Apenas solicitamos aos desenvolvedores que sigam o seguinte padrão de pastas, na hora de enviar seu `pull request`:

```shell
python  >  emissao_boleto_csv.py
php     >  emissao_boleto_csv.php
README.md
```
