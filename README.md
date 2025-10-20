# 🤖 Chatbot SLA & Productivity Analytics  

**Autor:** Franklin Santana dos Santos  
**Linguagem:** SQL (Databricks / Spark SQL)  
**Tópico:** Análise de performance operacional e atendimento via chat  

---

## 🏁 Objetivo  

Desenvolver uma análise completa da performance de atendimento via **chatbot e agentes humanos**, avaliando:  
- volume de tickets oferecidos e tratados;  
- produtividade por agente e por fila;  
- cumprimento de SLA;  
- tempos médios de resposta e atendimento;  
- backlog acumulado por faixa de tempo.  

O projeto visa mensurar **eficiência operacional** e identificar **gargalos no fluxo de atendimento digital**.

---

## 🧩 Fontes de Dados  

| Fonte | Descrição |
|-------|------------|
| `analytics.chatbot_interactions` | Interações entre clientes e chatbot, incluindo tipo de ação e produtividade. |
| `analytics.chat_sessions` | Sessões de atendimento de chat, com timestamps de início, fim e resposta do agente. |
| `support.ticket_group_history` | Histórico de tickets por fila e momento de entrada. |
| `support.ticket_details` | Detalhes adicionais sobre cada ticket (canal, produto, segmento etc). |

---

## ⚙️ Principais Técnicas SQL Utilizadas  

- **CTEs (Common Table Expressions)** para estruturar o pipeline de análise;  
- **Funções de janela** (`row_number()`, `lead()`) para identificar ações e sessões relevantes;  
- **Case statements dinâmicos** para granularidade diária, semanal e mensal;  
- **Conversão de timestamps** com `unix_timestamp()` e cálculo de minutos de atendimento;  
- **Filtros condicionais com `FILTER (WHERE ...)`** para medir SLA e backlog;  
- **Limpeza e deduplicação** de dados de sessões e tickets.  

---

## 🧮 Métricas Calculadas  

| Métrica | Descrição |
|----------|------------|
| **handled** | Quantidade de tickets tratados. |
| **productive_actions** | Total de ações produtivas realizadas. |
| **productivity_per_agent** | Média de ações produtivas por agente. |
| **avg_response_time** | Tempo médio de resposta (em minutos). |
| **avg_handling_time** | Tempo médio de atendimento do agente. |
| **sla_compliance** | Volume de tickets atendidos dentro do SLA. |
| **backlog_24h / 48h / 72h / +72h** | Volume de tickets pendentes em cada janela de tempo. |
| **avg_total_handling_time** | Tempo médio total de tratamento por ticket oferecido. |

---

## 📈 Exemplo de Resultados  

| Dia | Tickets Oferecidos | SLA Compliance (%) | Produtividade por Agente | Tempo Médio de Atendimento (min) | Backlog +72h |
|-----|--------------------|--------------------|----------------------------|----------------------------------|--------------|
| 2025-03-01 | 1.240 | 87% | 42,3 | 18,5 | 34 |
| 2025-03-02 | 1.130 | 84% | 38,9 | 19,8 | 49 |
| 2025-03-03 | 1.550 | 91% | 44,1 | 17,2 | 27 |

*(dados ilustrativos)*

---

## 💼 Insights de Negócio  

- O tempo médio de atendimento (TMA) mantém-se abaixo de **20 minutos**, indicando boa eficiência.  
- O cumprimento de **SLA** está entre **84–91%**, mas oscila em períodos de pico.  
- A fila **“Complaints”** apresenta o maior backlog acima de 72h, sugerindo redistribuição de headcount.  
- A métrica **handled_per_agent** mostra correlação direta com produtividade geral.  

---

## 🧰 Tecnologias Utilizadas  

- **SQL (Spark / Databricks)**  
- **Azure Databricks Workspace**  
- **Google Sheets + Looker Studio** para visualização dos resultados  

---

## 🧱 Estrutura do Repositório  


📁 chatbot-sla-performance-analysis/
 ├── query.sql
 ├── README.md
 ├── sample_results.csv
 └── dashboard_preview.png


---

## 🚀 Próximos Passos  

1. Automatizar exportação dos resultados para **Google Sheets** via Python;  
2. Criar **dashboard no Looker Studio** para acompanhamento visual;  
3. Adicionar comparação histórica (Mês vs Mês) e análise de sazonalidade;  
4. Publicar artigo no **LinkedIn** explicando o raciocínio e o impacto dos resultados.  

---

## 🧠 Observação Técnica  

A query foi projetada para rodar em **ambiente Databricks (Spark SQL)** e utiliza parâmetros dinâmicos:  
- `:granularity` → define o nível de agrupamento (`Day`, `Week`, `Month`);  
- `:date.min` / `:date.max` → intervalos de data;  

Esses parâmetros permitem que a análise seja flexível e aplicável em diferentes períodos.

---

## 📎 Contato  

👤 **Franklin Santana dos Santos**  
🔗 [GitHub - franklinsts](https://github.com/franklinsts)  
💼 Analista de Customer Experience Sênior • Foco em Análise de Dados  
📊 SQL | Databricks | Looker Studio | Google Sheets | Automação de dados  

--- 
