# Documentação do Projeto de Teste de Nivelamento

## Índice
1. [Introdução](#1-introdução)  
2. [Objetivos](#2-objetivos)  
3. [Tecnologias Utilizadas](#3-tecnologias-utilizadas)  
4. [Estrutura do Projeto](#4-estrutura-do-projeto)  
5. [Teste 1: Web Scraping](#5-teste-1-web-scraping)  
    1. [Objetivo](#51-objetivo)  
    2. [Detalhamento das Tarefas](#52-detalhamento-das-tarefas)  
6. [Teste 2: Transformação de Dados](#6-teste-2-transformação-de-dados)  
    1. [Objetivo](#61-objetivo)  
    2. [Detalhamento das Tarefas](#62-detalhamento-das-tarefas)  
7. [Teste 3: Banco de Dados](#7-teste-3-banco-de-dados)  
    1. [Objetivo](#71-objetivo)  
    2. [Detalhamento das Tarefas](#72-detalhamento-das-tarefas)  
8. [Teste 4: API](#8-teste-4-api)  
    1. [Objetivo](#81-objetivo)  
    2. [Detalhamento das Tarefas](#82-detalhamento-das-tarefas)  
9. [Conclusão](#9-conclusão)  

---

## 1. Introdução

Este projeto de **teste de nivelamento** tem como objetivo a aplicação de diversos conceitos e práticas de desenvolvimento, com foco em manipulação de dados, integração de APIs, web scraping, e manipulação de banco de dados. As tarefas são divididas em quatro testes principais, cada um abordando uma área distinta de conhecimento. Este documento descreve a estrutura e o planejamento para o desenvolvimento das soluções propostas.

**Nome do projeto:** *HealthDataProcessor*

Esse nome comunica de forma simples que o projeto envolve o processamento de dados de saúde, o que abrange tanto a parte de web scraping (extração de dados), quanto a transformação e organização desses dados em banco de dados e API.

---

## 2. Objetivos

O objetivo principal deste projeto é demonstrar competência nas áreas de:

- **Web Scraping:** Coletar e manipular dados da web.
- **Transformação de Dados:** Realizar o processamento de informações extraídas de documentos PDF e estruturá-las em um formato adequado para análise.
- **Banco de Dados:** Criar e manipular banco de dados, além de executar consultas analíticas.
- **Desenvolvimento de API:** Criar uma interface web para interação com servidores Python e integração de APIs.

---

## 3. Tecnologias Utilizadas

### **Python**
![Python Logo](https://upload.wikimedia.org/wikipedia/commons/c/c3/Python-logo-notext.svg)
- **Uso:** Web Scraping, transformação de dados e criação de servidor.
- **Bibliotecas:** requests, BeautifulSoup, Selenium, Flask, FastAPI.

### **Vue.js**
![Vue.js Logo](https://upload.wikimedia.org/wikipedia/commons/9/95/Vue.js_Logo_2.svg)
- **Uso:** Desenvolvimento da interface web.
- **Framework:** Vue.js.

### **SQL (MySQL/PostgreSQL)**
![MySQL Logo](https://upload.wikimedia.org/wikipedia/commons/6/67/MySQL_logo.png)
- **Uso:** Estruturação e manipulação de banco de dados.
- **SGBD:** MySQL ou PostgreSQL.

### **Postman**
![Postman Logo](https://upload.wikimedia.org/wikipedia/commons/8/84/Postman-logo.png)
- **Uso:** Testar APIs.

---

## 4. Estrutura do Projeto

A estrutura do projeto será dividida em diretórios e arquivos conforme as áreas abordadas. Abaixo segue uma sugestão de estrutura:

/HealthDataProcessor
    /web_scraping
        scraper.py
        utils.py
        README.md
    /transformacao_dados
        extract_data.py
        process_data.py
        zip_data.py
        README.md
    /banco_de_dados
        /scripts
            create_tables.sql
            import_data.sql
            queries.sql
        /data
            operadoras.csv
            demonstracoes_contabeis.zip
        README.md
    /api
        /server
            app.py
            api_utils.py
        /frontend
            /components
                Search.vue
            /views
                Home.vue
            App.vue
            main.js
        /postman
            collection.json
        README.md
    README.md


---

## 5. Teste 1: Web Scraping

### 5.1 Objetivo

O objetivo do **Teste 1** é realizar a extração de dados a partir de um site oficial da ANS, baixando dois anexos em PDF, compactando-os e realizando o download de forma automatizada.

### 5.2 Detalhamento das Tarefas

- **Tarefa 1.1:** Acessar o site [https://www.gov.br/ans/pt-br/acesso-a-informacao/participacao-dasociedade/atualizacao-do-rol-de-procedimentos](https://www.gov.br/ans/pt-br/acesso-a-informacao/participacao-dasociedade/atualizacao-do-rol-de-procedimentos).
- **Tarefa 1.2:** Baixar os **Anexos I e II** em formato PDF.
- **Tarefa 1.3:** Compactar os PDFs em um único arquivo **ZIP**.

**Ferramentas e Bibliotecas:**
- requests, BeautifulSoup, selenium (para scraping)
- zipfile (para compactação)

---

## 6. Teste 2: Transformação de Dados

### 6.1 Objetivo

O objetivo do **Teste 2** é extrair e processar os dados de uma tabela contida no PDF Anexo I, e então estruturá-los em um arquivo CSV.

### 6.2 Detalhamento das Tarefas

- **Tarefa 2.1:** Utilizar bibliotecas de parsing de PDF para extrair os dados da tabela *"Rol de Procedimentos e Eventos em Saúde"* do **Anexo I**.
- **Tarefa 2.2:** Salvar os dados extraídos em formato **CSV**.
- **Tarefa 2.3:** Compactar o arquivo **CSV** em um arquivo ZIP com o nome `Teste_{seu_nome}.zip`.
- **Tarefa 2.4:** Substituir abreviações de colunas (como **OD** e **AMB**) por suas descrições completas.

**Ferramentas e Bibliotecas:**
- PyPDF2, pdfplumber, ou outras bibliotecas de extração de PDF.
- csv, pandas (para manipulação de dados).

---

## 7. Teste 3: Banco de Dados

### 7.1 Objetivo

O objetivo do **Teste 3** é realizar a configuração de um banco de dados, importar os dados e desenvolver consultas SQL analíticas.

**Modelo Entidade-Relacionamento (ER) para o Projeto**

Abaixo está a proposta de um modelo básico para o seu banco de dados, considerando os seguintes pontos-chave:

- **Operadoras de Plano de Saúde:** Informações das operadoras extraídas do arquivo CSV.
- **Demonstrativos Contábeis:** Dados das operadoras com as despesas relacionadas aos **"EVENTOS/SINISTROS CONHECIDOS OU AVISADOS DE ASSISTÊNCIA A SAÚDE MÉDICO HOSPITALAR"**.
- **Procedimentos e Eventos em Saúde:** Tabela extraída do **Anexo I**, com detalhes sobre os procedimentos.

#### Entidades do Modelo

1. **Operadora:** Contém informações das operadoras de plano de saúde.
2. **Demonstrativo Contábil:** Dados financeiros das operadoras.
3. **Sinistro:** Representa os eventos de sinistro ou despesas registradas para cada operadora.
4. **Procedimento:** Tabela que contém os procedimentos médicos e hospitalares.
5. **Procedimento_Operadora:** Relaciona as operadoras aos procedimentos que elas cobrem.

### 7.2 Detalhamento das Tarefas

#### Tarefas de Preparação:
- **Tarefa 3.1:** Baixar os arquivos dos últimos 2 anos do repositório de dados públicos.
- **Tarefa 3.2:** Baixar os dados cadastrais das operadoras ativas na ANS em formato **CSV**.

#### Tarefas de Código:
- **Tarefa 3.3:** Criar as tabelas necessárias para importar os dados CSV.
- **Tarefa 3.4:** Criar queries para importar os arquivos CSV para o banco de dados, garantindo o encoding correto.
- **Tarefa 3.5:** Desenvolver queries analíticas para responder às questões sobre as operadoras com maiores despesas.

---

## 8. Teste 4: API

### 8.1 Objetivo

O objetivo do **Teste 4** é criar uma interface web usando **Vue.js** e um servidor **Python** para realizar buscas textuais nos dados das operadoras.

### 8.2 Detalhamento das Tarefas

- **Tarefa 4.2:** Criar um servidor Python com uma rota para realizar buscas textuais na lista de cadastros de operadoras.
- **Tarefa 4.3:** Criar uma coleção no **Postman** para testar e demonstrar o resultado da API.

**Ferramentas e Tecnologias:**
- Flask ou FastAPI (para o servidor Python)
- Vue.js (para o front-end)
- Postman (para testar a API)

---

## 9. Conclusão

Este projeto visa demonstrar habilidades em diversas áreas de programação e manipulação de dados, desde a coleta automatizada de informações até a criação de interfaces interativas para o usuário. Ao seguir as etapas e implementar as soluções propostas, será possível avaliar as competências em **web scraping**, **processamento de dados**, **banco de dados** e **desenvolvimento de APIs**.

