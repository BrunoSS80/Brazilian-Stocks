# 📈 Brazilian Stock Market Lakehouse

Bem-vindo ao repositório do **Brazilian Stock Market Lakehouse**!

Este projeto demonstra uma solução completa de Engenharia de Dados para coleta, tratamento, armazenamento e análise de dados da Bolsa de Valores Brasileira (B3), utilizando uma arquitetura **Lakehouse** construída sobre **Databricks**, **Apache Spark** e **Delta Lake**.

Desenvolvido como projeto de portfólio, ele demonstra boas práticas utilizadas em projetos modernos de Engenharia de Dados, contemplando processamento histórico, atualização intraday, orquestração de pipelines e visualização de indicadores através de dashboards.

---

# 🏗️ Arquitetura de Dados

A arquitetura deste projeto segue o modelo **Medallion Architecture (Lakehouse)** dividido em três camadas.

### 🥉 Bronze (Raw)

Armazena os dados exatamente como são retornados pela API do Yahoo Finance, preservando todas as informações originais.

### 🥈 Silver (Trusted)

Responsável pela limpeza, padronização, validação, enriquecimento e preparação dos dados para consumo analítico.

### 🥇 Gold (Analytics)

Contém tabelas analíticas e indicadores consolidados utilizados pelos dashboards e análises de negócio.

---

# 📖 Visão Geral do Projeto

O projeto contempla:

- 📌 Arquitetura Lakehouse utilizando Bronze, Silver e Gold.
- 📈 Coleta de dados históricos e atualizações intraday da B3.
- 🔄 Pipelines ETL desenvolvidos em PySpark.
- ⚡ Processamento utilizando Delta Lake.
- 📊 Dashboards desenvolvidos no Databricks.
- 🚀 Orquestração automática utilizando Databricks Workflows.

---

## 🧩 Diagrama Estrutural

![Diagrama.png](https://github.com/BrunoSS80/Brazilian-Stocks/blob/main/images/Diagrama.png)

---

# 🚀 Orquestração

A execução do pipeline é automatizada através de **Databricks Workflows**, divididos conforme a responsabilidade de cada processo.

### Workflow 1 - Carga Inicial

```text
Bronze Histórico
        │
        ▼
Silver Histórico
        │
        ▼
Gold Histórico
```

Executado apenas uma vez para popular a base histórica.

---

### Workflow 2 - Atualização Intraday

```text
Bronze Microbatch
        │
        ▼
Silver Microbatch
        │
        ▼
Gold Intraday
```

Executado durante o horário de negociação para manter as informações atualizadas.

---

### Workflow 3 - Consolidação Diária

```text
Consolidação
        │
        ▼
Atualização da Silver Histórica
        │
        ▼
Atualização da Gold Histórica
```

Executado após o fechamento da bolsa para consolidar o pregão no histórico.

---

# 📊 Dashboards

O projeto disponibiliza dois dashboards desenvolvidos no Databricks.

## 📚 Dashboard Histórico

- Evolução do preço de fechamento
- Volume negociado
- Variação percentual
- Indicadores consolidados
- Comparativo entre ativos

![Dash-Anual](https://github.com/BrunoSS80/Brazilian-Stocks/blob/main/images/Dash_Anual.png)

---

## ⏱️ Dashboard Intraday

- Cotação em tempo real
- Variação percentual minuto a minuto
- Volume negociado
- Última atualização
- Filtro por ticker

![Dash-Intra](https://github.com/BrunoSS80/Brazilian-Stocks/blob/main/images/Dash_intra.png)

---

# 🛠️ Tecnologias Utilizadas

- Databricks Community Edition
- Apache Spark (PySpark)
- Delta Lake
- Databricks Workflows
- Databricks Dashboards
- Python
- Yahoo Finance API (yfinance)

---

# ▶️ Como Executar

## 1️⃣ Clone o repositório

```bash
git clone https://github.com/seu-usuario/brazilian-stock-market-lakehouse.git

cd brazilian-stock-market-lakehouse
```

---

## 2️⃣ Importe os notebooks

Importe todos os notebooks para o seu Workspace do Databricks preservando a estrutura do projeto.

---

## 3️⃣ Execute a carga inicial

Execute o Workflow responsável pelo carregamento do histórico.

Fluxo:

```text
Bronze Histórico

↓

Silver Histórico

↓

Gold Histórico
```

---

## 4️⃣ Execute o Workflow Intraday

Execute o Workflow responsável pela atualização das cotações durante o pregão.

Fluxo:

```text
Bronze Microbatch

↓

Silver Microbatch

↓

Gold Intraday
```

---

## 5️⃣ Consulte os Dashboards

Após a execução dos Workflows, os dashboards estarão disponíveis diretamente no Databricks.

---

# 🎯 Objetivo

Desenvolver um pipeline moderno de Engenharia de Dados capaz de coletar, processar e disponibilizar dados da Bolsa de Valores Brasileira para análises históricas e monitoramento intraday, utilizando arquitetura Lakehouse, Apache Spark e Delta Lake.

---

# 📌 Especificações

| Item | Descrição |
|------|-----------|
| Fonte de Dados | Yahoo Finance |
| Linguagem | Python |
| Framework | Apache Spark (PySpark) |
| Arquitetura | Lakehouse |
| Armazenamento | Delta Lake |
| Camadas | Bronze, Silver e Gold |
| Orquestração | Databricks Workflows |
| Visualização | Databricks Dashboards |

---

# 📚 Principais Funcionalidades

- Coleta automática de dados históricos da B3.
- Atualização periódica das cotações durante o pregão.
- Limpeza, validação e enriquecimento dos dados.
- Consolidação diária do histórico.
- Geração de indicadores analíticos.
- Dashboards para acompanhamento histórico e intraday.
- Pipeline totalmente automatizado através de Workflows.

---

## 🧑‍💻 Autor

Desenvolvido por **Bruno Severgnini da Silva**

📌 Conecte-se comigo:
- LinkedIn: https://www.linkedin.com/in/bruno-severgnini/
- GitHub: https://github.com/BrunoSS80
