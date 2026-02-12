
🎓 Dashboard de Gestão Acadêmica: Frequência Automatizada

## 📌 Introdução

Este projeto moderniza o controle acadêmico da **Tech Institute** através de um ecossistema de dados focado na gestão de frequência. A inovação central é a substituição do registro manual por **Reconhecimento Facial**, garantindo integridade total aos dados escolares.

## 🎯 Objetivos e Funcionalidades

* **Automação de Coleta:** Integração de tecnologia facial para eliminar erros humanos.
* **Dashboard Interativo:** Visualização de indicadores de presença/ausência por período.
* **Análise de Tendências:** Gráficos de evolução temporal para medir o engajamento dos alunos.
* **Gestão de Pendências:** Filtragem por tipo de semana (Alfa/Beta) para controle cruzado.

---

## 📂 Entendimento dos Dados (Data Understanding)

### 2.1. Fontes de Dados

* **Engine:** Microsoft SQL Server.
* **Objeto de Extração:** `vw_frequencia_automatizada_001` (Views).

### 2.2. Dicionário de Dados

| Coluna | Tipo | Descrição |
| --- | --- | --- |
| **ID** | INT | Identificador único do registro (Primary Key). |
| **AreaCurso** | VARCHAR | Disciplina ou módulo específico (ex: SQL). |
| **Matricula** | VARCHAR | Código de identificação único do aluno. |
| **DataAula** | DATE | Data da ocorrência do registro. |
| **StatusPresenca** | VARCHAR | Estado do registro (Presente/Falta). |
| **Turno** | VARCHAR | Período das aulas (Matutino/Vespertino). |

---

## ⚙️ Metodologia e Modelagem

### 4.1. Ferramentas Utilizadas

| Ferramenta | Uso |
| --- | --- |
| **Power BI Desktop** | Desenvolvimento de dashboards e medidas DAX avançadas. |
| **SQL Server (SSMS)** | Conexão, criação de Views e manipulação via queries. |
| **N8N / Power Automate** | Automação do workflow e integração de dados. |
| **Notion** | Gestão de cronograma, documentação e tarefas. |

### 4.2. Exemplo de Consulta para Validação (SQL)

Para garantir a integridade dos dados antes da carga no Power BI, utilizei queries de validação como esta:

```sql
-- Exemplo de contagem de frequência por curso e turno
SELECT 
    CURSO, 
    Turno, 
    COUNT(CASE WHEN StatusPresenca = 'Presente' THEN 1 END) AS Total_Presencas,
    COUNT(CASE WHEN StatusPresenca = 'Falta' THEN 1 END) AS Total_Faltas
FROM TechInstitute_DB.dbo.vw_frequencia_automatizada_001
GROUP BY CURSO, Turno;

```

---

## 📊 Avaliação e KPIs

* **Taxa de Presença:** Percentual de engajamento sobre o total de aulas previstas.
* **Total Faltas:** Volume absoluto de ausências com alertas visuais em vermelho.
* **Evolução Temporal:** Linha de tendência para prever o comportamento dos alunos.

## 🚀 Recomendações Futuras

1. **Alertas Preditivos:** Sistema de notificação automática para alunos com mais de 20% de faltas.
2. **Correlação de Dados:** Cruzar os dados de frequência com o desempenho nas notas.
3. **Expansão:** Inclusão de novos módulos para todos os cursos de tecnologia da instituição.
