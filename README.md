# Projeto de Testes de API - E-commerce ServeRest

Este repositório contém um conjunto de testes de carga, performance, aceitação e funcionais para a API do e-commerce "ServeRest". Estes testes foram desenvolvidos durante o curso "[Postman do Básico ao Avançado com Projetos](https://www.udemy.com/course/postman-do-basico-ao-avancado-com-projetos/)" da Udemy.

## Visão Geral

ServeRest é uma API pública e testável usada para simulações de e-commerce, permitindo a automação e testes de diversas funcionalidades de compra, usuário e produtos. O objetivo deste projeto é validar a confiabilidade, desempenho e comportamento da API em diferentes cenários.

Os testes foram implementados usando o **Postman** e **Newman**, cobrindo os seguintes aspectos:

- **Testes de Carga**: Verificação da capacidade da API em lidar com um grande número de requisições simultâneas.
- **Testes de Performance**: Medição do tempo de resposta da API sob diferentes níveis de carga.
- **Testes de Aceitação**: Validação de que os endpoints implementam corretamente as regras de negócios esperadas.
- **Testes Funcionais**: Verificação do funcionamento correto dos endpoints de acordo com a documentação da API.

## Tecnologias Utilizadas

- [Postman](https://www.postman.com/): Ferramenta principal para criação, execução e automação dos testes de API.
- [Node.js](https://nodejs.org/): Usado para automação e execução via script dos testes através do Newman.
- [ServRest API](https://serverest.dev/): API pública utilizada para a simulação de funcionalidades de e-commerce.

## Estrutura do Projeto

- **Coleções Postman**: Arquivos `.json` contendo os diferentes cenários de testes agrupados por funcionalidade (usuário, produtos, carrinho, etc.).
- **Ambientes Postman**: Configurações de variáveis de ambiente, como URL base da API e dados dinâmicos para diferentes testes.
- **Scripts de Automação**: Scripts para execução automatizada dos testes usando o JavaScript.

## Testes Implementados

### 1. Testes de Performance
- **Objetivo**: Medir o tempo de resposta dos endpoints críticos da API em condições normais e de alta demanda.
- **Ferramentas**: Postman + Monitoramento via Dashboard.

### 2. Testes de Aceitação
- **Objetivo**: Garantir que a API atende aos critérios de aceitação definidos nos requisitos do e-commerce.
- **Cenários**: Criação de novos usuários, simulação de compras, autenticação e manipulação de carrinhos de compras.

### 3. Testes Funcionais
- **Objetivo**: Verificar se os endpoints estão funcionando corretamente de acordo com a especificação.
- **Endpoints Testados**:
  - Cadastro de usuários (`POST /usuarios`)
  - Autenticação (`POST /login`)
  - Listagem de produtos (`GET /produtos`)
  - Gerenciamento de carrinho (`POST /carrinhos`)
