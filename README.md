# 🚀 Hunter API Automation Tests

Projeto de automação de testes de API utilizando **Postman**, **Newman**, **GitHub Actions** e **Data Driven Testing (CSV)**.

O objetivo deste projeto é validar os principais fluxos da API Hunter de forma automatizada, possibilitando execução local e integração contínua através do GitHub Actions.

---

# 📋 Tecnologias Utilizadas

- 📮 Postman
- ⚡ Newman
- 📊 Newman HTML Extra Reporter
- 🔄 GitHub Actions
- 📄 CSV (Data Driven Testing)
- 🟢 Node.js

---

# 🎯 Objetivo

Automatizar os principais fluxos da API Hunter:

- Cadastro de Leads
- Consulta de Leads
- Atualização de Leads
- Exclusão de Leads
- Cadastro de Lead Lists
- Consulta de Lead Lists
- Atualização de Lead Lists
- Exclusão de Lead Lists

Além disso:

- Execução local via Newman
- Execução automática via GitHub Actions
- Relatórios HTML automatizados
- Massa de dados externa utilizando CSV

---

# 📁 Estrutura do Projeto

```text
📦 hunter-api-postman
│
├── 📁 .github
│   └── 📁 workflows
│       └── 📄 ci.yaml
│
├── 📁 Dados
│   ├── 📄 dados_csv.csv
│   └── 📄 dados_lead_list_csv.csv
│
├── 📁 Projeto
│   ├── 📄 API_Hunter_postman_collection.json
│   └── 📄 HOMOL_postman_environment.json
│
├── 📁 Templates
│   └── 📄 customHtml.hbs
│
├── 📁 Resultado
│   ├── 📄 leads.html
│   └── 📄 leads-lists.html
│
├── 📁 newman
│   ├── 📄 execution.json
│   ├── 📄 report.html
│   └── 📄 logs
│
└── 📄 README.md
```

---

# 📚 Estrutura da Collection

```text
📦 API Hunter
│
├── 📁 Leads
│
│   ├── 📄 POST - Criar Novo Lead
│   ├── 📄 GET - Buscar Todos os Leads
│   ├── 📄 GET - Buscar Lead Específico
│   ├── 📄 PUT - Editar Lead
│   └── 📄 DELETE - Excluir Lead
│
└── 📁 Leads_Lists

    ├── 📄 POST - Criar Nova Lead List
    ├── 📄 GET - Buscar Todas as Lead Lists
    ├── 📄 GET - Buscar Lead List Específica
    ├── 📄 PUT - Editar Lead List
    └── 📄 DELETE - Excluir Lead List
```

---

# 📊 Massa de Dados

O projeto utiliza Data Driven Testing através de arquivos CSV.

### Leads

```text
dados_csv.csv
```

### Lead Lists

```text
dados_lead_list_csv.csv
```

Essa abordagem permite executar o mesmo cenário diversas vezes utilizando diferentes conjuntos de dados.

---

# ⚙️ Instalação

## Instalar Node.js

https://nodejs.org

---

## Instalar Newman

```bash
npm install -g newman
```

---

## Instalar HTML Reporter

```bash
npm install -g newman-reporter-htmlextra
```

---

# ▶️ Execução Local

## Executar apenas Leads

```bash
newman run Projeto/API_Hunter_postman_collection.json ^
-e Projeto/HOMOL_postman_environment.json ^
-d Dados/dados_csv.csv ^
--folder Leads
```

## Executar apenas Lead Lists

```bash
newman run Projeto/API_Hunter_postman_collection.json ^
-e Projeto/HOMOL_postman_environment.json ^
-d Dados/dados_lead_list_csv.csv ^
--folder Leads_Lists
```

---

# 📈 Gerando Relatórios HTML

## Leads

```bash
newman run Projeto/API_Hunter_postman_collection.json ^
-e Projeto/HOMOL_postman_environment.json ^
-d Dados/dados_csv.csv ^
--folder Leads ^
-r cli,htmlextra ^
--reporter-htmlextra-export Resultado/leads.html
```

## Lead Lists

```bash
newman run Projeto/API_Hunter_postman_collection.json ^
-e Projeto/HOMOL_postman_environment.json ^
-d Dados/dados_lead_list_csv.csv ^
--folder Leads_Lists ^
-r cli,htmlextra ^
--reporter-htmlextra-export Resultado/leads-lists.html
```

---

# 🔄 Integração Contínua (CI)

O projeto possui integração contínua através do GitHub Actions.

### Disparadores

- ✅ Push
- ✅ Pull Request
- ✅ Execução Manual (Workflow Dispatch)

---

# 🚀 Fluxo da Pipeline

```text
📄 Checkout do Repositório
        │
        ▼
📄 Setup Node.js
        │
        ▼
📄 Instalação do Newman
        │
        ▼
📄 Instalação do HTML Reporter
        │
        ▼
📄 Execução da Pasta Leads
        │
        ▼
📄 Execução da Pasta Leads_Lists
        │
        ▼
📄 Geração dos Relatórios HTML
        │
        ▼
📄 Publicação dos Artifacts
```

---

# 📂 Relatórios

Após a execução da pipeline, os relatórios podem ser baixados através da aba **Actions** do GitHub.

```text
Actions
 └── API Tests
      └── Artifacts
           └── api-reports
```

Arquivos gerados:

```text
leads.html
leads-lists.html
```

---

# ✅ Validações Implementadas

- Status Code
- Tempo de Resposta
- Estrutura do Response Body
- Criação de Variáveis de Ambiente
- Fluxos CRUD completos
- Data Driven Testing
- Execução Automatizada em Pipeline

---

# 👨‍💻 Autor

**Olavo Luiz Tavares Júnior**

QA Engineer | Test Automation | API Testing | Postman | Newman | GitHub Actions | Cypress | Robot Framework

---

⭐ Se este projeto foi útil para você, deixe uma estrela no repositório.
