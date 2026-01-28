# motorista-app 🚕📊
Pipeline completo: geração de CSV no Python (Colab), modelagem e queries no SQL Server/SSMS e visualizações no Power BI com métricas DAX.

---

## 🎯 Objetivo do projeto
Analisar **qualidade e eficiência da operação de motoristas** em um app de mobilidade, identificando:
- Onde a **taxa de aceitação** é pior
- Quais são os **principais motivos de recusa**
- Quais segmentos (empresa/região/distância/preço/categoria) concentram problemas
- Oportunidades de ação para reduzir recusas e melhorar experiência do usuário

> **Contexto:** este projeto simula um cenário realista de operação (corridas, motoristas, empresas, regiões e motivos de recusa) com foco em diagnóstico e tomada de decisão.

---

## 🧱 Pipeline (fim a fim)
1) **Geração de dados (Python/Colab)**  
   - CSVs gerados com apoio de IA no Google Colab  
   - Dados simulam corridas, motoristas, categorias, preço, distância, região e aceite/recusa

2) **Banco e tratamento (SQL Server / SSMS)**  
   - Importação dos CSVs para SQL Server  
   - Criação de views/queries para indicadores e análises de causa

3) **Dashboard (Power BI)**  
   - Modelagem (relacionamentos)
   - Medidas DAX (KPIs e taxas)
   - Páginas de diagnóstico (Visão Geral / Regiões / Perfis)

---

## 📂 Conteúdo do repositório
- `motorista-app.pbix` → dashboard Power BI
- `/sql` → queries utilizadas nas análises
- `/images` → prints do Power BI e resultados do SQL
- `/data` (opcional) → CSVs (se aplicável)

---

## 🔎 Análises no SQL (com evidência)
Abaixo estão as principais análises usadas para construir os KPIs e direcionar o diagnóstico.

### 1) KPIs gerais (volume, aceitação, valor médio)
📄 Query: [`sql/01_kpis_gerais.sql`](sql/01_kpis_gerais.sql)

✅ Resultado (SSMS):
![KPIs Gerais](images/sql_01_kpis.png)

**Por que isso importa?**  
Define a linha de base do cenário: volume total, aceitação média e ticket médio.

---

### 2) Taxa de aceitação por empresa
📄 Query: [`sql/02_aceitacao_por_empresa.sql`](sql/02_aceitacao_por_empresa.sql)

✅ Resultado (SSMS):
![Aceitação por Empresa](images/sql_02_aceitacao_empresa.png)

**Por que isso importa?**  
Ajuda a entender se o problema é concentrado em uma empresa específica (ex.: MoveX).

---

### 3) Motivos de recusa (ranking)
📄 Query: [`sql/03_recusas_por_motivo.sql`](sql/03_recusas_por_motivo.sql)

✅ Resultado (SSMS):
![Recusas por Motivo](images/sql_03_recusas_motivo.png)

**Por que isso importa?**  
Identifica as causas raiz que mais derrubam a aceitação (ex.: distância longa, valor baixo).

---

### 4) Aceitação por região
📄 Query: [`sql/04_aceitacao_por_regiao.sql`](sql/04_aceitacao_por_regiao.sql)

✅ Resultado (SSMS):
![Aceitação por Região](images/sql_04_aceitacao_regiao.png)

**Por que isso importa?**  
Mostra se existe gargalo operacional por área (ex.: regiões com risco, menor oferta, pior remuneração).

---

### 5) Aceitação por faixa de distância
📄 Query: [`sql/05_aceitacao_por_faixa_distancia.sql`](sql/05_aceitacao_por_faixa_distancia.sql)

✅ Resultado (SSMS):
![Aceitação por Faixa de Distância](images/sql_05_aceitacao_distancia.png)

**Por que isso importa?**  
Valida a hipótese de que corridas muito longas ou muito curtas afetam o aceite.

---

### 6) Aceitação por faixa de preço (opcional)
📄 Query: [`sql/06_aceitacao_por_faixa_preco.sql`](sql/06_aceitacao_por_faixa_preco.sql)

✅ Resultado (SSMS):
![Aceitação por Faixa de Preço](images/sql_06_aceitacao_preco.png)

**Por que isso importa?**  
Ajuda a entender impacto do preço na decisão do motorista (principalmente em distâncias longas).

---

## 📊 Dashboard Power BI (prints)
### Página 1 — Visão Geral
- KPIs (Total Corridas, Taxa Aceitação, Valor Médio)
- Aceitação por empresa
- Motivos de recusa

![Power BI - Página 1](images/Motorista_BI_01.png)

### Página 2 — Regiões (Diagnóstico)
- Aceitação e volume por região
- Empresa mais crítica varia conforme filtros
- Motivo mais crítico e quantidade de recusas

![Power BI - Página 2](images/Motorista_BI_02.png)

### Página 3 — Perfis
- Aceitação por faixa de distância e faixa de preço
- Aceitação por categoria de carro
- Motivos de recusa como causa raiz

![Power BI - Página 3](images/Motorista_BI_03.png)

---

## ✅ Principais insights (resumo executivo)
- O motivo de recusa mais frequente é **Distância longa** (alto impacto no volume de recusas).
- A aceitação varia por **empresa** e por **região**, indicando gargalos localizados.
- **Preço e distância** influenciam diretamente a decisão do motorista, sugerindo ajuste de incentivos ou regras por segmento.

---

## 🧭 Próximos passos (o que eu melhoraria)
- Criar uma tabela de **coorte** (retenção de motoristas: ativos vs. inativos ao longo dos meses)
- Detalhar “distância longa” por **preço/km** (corridas longas com retorno ruim)
- Criar um score de “risco de churn do motorista” com base em recusas e aceitação
