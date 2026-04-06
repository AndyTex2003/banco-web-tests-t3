# Banco Web Tests T3

## Objetivo

Este projeto foi desenvolvido para demonstrar aos alunos da Mentoria 2.0 como automatizar testes de uma aplicação web usando Cypress e JavaScript. O foco está em criar uma estrutura organizada com Custom Commands e gerar relatórios de execução de forma prática.

## Componentes do projeto

- `package.json`: gerencia dependências e scripts do projeto.
- `cypress.config.js`: configuração do Cypress, incluindo `baseUrl`, reportador e plugin do `cypress-mochawesome-reporter`.
- `cypress/e2e/`: suíte de testes automatizados.
  - `login.cy.js`: testes de fluxo de login.
  - `transferencia.cy.js`: testes de transferência entre contas.
- `cypress/fixtures/`: dados de teste utilizados pelos casos.
  - `credenciais.json`: credenciais válidas e inválidas para login.
- `cypress/support/commands.js`: importa os Custom Commands usados pelos testes.
- `cypress/support/e2e.js`: carrega os comandos personalizados e registra o reportador Mochawesome.
- `cypress/support/commands/`: comandos customizados para ações reutilizáveis.
  - `common.js`: comandos genéricos de interação com elementos da interface.
  - `login.js`: comandos de login com credenciais válidas e inválidas.
  - `transferencia.js`: comandos para realizar transferências.

## Requisitos

Antes de executar os testes, execute as aplicações abaixo:

- API: https://github.com/juliodelimas/banco-api
- Aplicação Web: https://github.com/juliodelimas/banco-web

O Cypress está configurado para usar `http://localhost:4000` como `baseUrl`.

## Instalação

1. Abra o terminal na pasta do projeto.
2. Execute:

```bash
npm install
```

## Execução dos testes

- Executar todos os testes em modo headless:

```bash
npm test
```

- Executar testes em modo headful (com janela do navegador):

```bash
npm run cy:headed
```

- Abrir o Cypress Test Runner:

```bash
npm run cy:open
```

## Relatórios

Este projeto usa `cypress-mochawesome-reporter` para gerar relatórios de teste em formato HTML. Após a execução do Cypress, os relatórios são gerados automaticamente no diretório padrão de saída do Mochawesome.

## Testes existentes

- `cypress/e2e/login.cy.js`
  - Verifica login com credenciais válidas.
  - Verifica comportamento com credenciais inválidas.

- `cypress/e2e/transferencia.cy.js`
  - Realiza transferência entre contas usando comandos reutilizáveis.

## Custom Commands

Os comandos personalizados facilitam a leitura dos testes e a reutilização de ações comuns.

### `Cypress.Commands.add('verificarMensagemNoToast', mensagem)`
- Verifica se a mensagem exibida no toast corresponde ao texto esperado.

### `Cypress.Commands.add('selecionarOpcaoNaCombobox', labelDoCampo, opcao)`
- Seleciona uma opção em um componente de combobox a partir do rótulo do campo.

### `Cypress.Commands.add('fazerLoginComCredenciaisValidas')`
- Preenche o formulário de login com credenciais válidas do fixture `credenciais.json` e envia.

### `Cypress.Commands.add('fazerLoginComCredenciaisInvalidas')`
- Preenche o formulário de login com credenciais inválidas do fixture `credenciais.json` e envia.

### `Cypress.Commands.add('realizarTransferencia', contaOrigem, contaDestino, valor)`
- Executa os passos de transferência entre contas, escolhendo origem e destino e preenchendo o valor.

## Observações finais

- Certifique-se de que a API e a aplicação web estão em execução antes de rodar os testes.
- O projeto é um exemplo didático para a Mentoria 2.0 e mostra boas práticas de organização com Cypress e Custom Commands.
