# motorista-app

Projeto de portfólio com foco em análise de motoristas e operações de corridas: criação do dataset em CSV, tratamento e consultas no SQL Server (SSMS) e construção de dashboard no Power BI (DAX + visualização).

## O que foi feito (pipeline)
1) **Geração dos CSVs (Google Colab / Python)**  
   Dataset simulado criado no Colab com apoio de IA, para reproduzir um cenário realista de operação (corridas, motoristas, regiões, recusas etc.)

2) **Tratamento e análises no SQL Server (SSMS)**  
   Consultas para entender comportamento e gargalos: aceitação, recusas, variações por empresa/região e faixas (distância/preço)

3) **Dashboard no Power BI**  
   Modelagem, criação de medidas DAX e construção de páginas com indicadores e diagnósticos

---

## Estrutura do repositório
- `data/` → arquivos CSV usados na análise  
  - `data/Motoristas_v3.csv`  
  - `data/corridas_v3.csv`
- `sql/` → consultas SQL (vou incluir aqui os scripts e prints do SSMS)
- `images/` → prints do dashboard e imagens para o README
- `motorista-app.pbix` → arquivo do Power BI

---

## Dashboard (prints)
Abaixo estão algumas telas do Power BI usadas no diagnóstico:

### Página 1 — Visão geral
![Página 1](images/Motorista_BI_01.png)

### Página 2 — Regiões (diagnóstico)
![Página 2](images/Motorista_BI_02.png)

### Página 3 — Perfis e faixas (distância / preço / categoria)
![Página 3](images/Motorista_BI_03.png)

---

## Principais perguntas que guiaram a análise
- Quais **motivos de recusa** mais impactam a operação?
- Como a **taxa de aceitação** varia por **empresa** e **região**?
- Existe relação entre **distância / preço** e aceitação?
- Onde estão os **pontos críticos** que geram perda de eficiência (ex.: baixa aceitação, alto volume de recusa)?

---

## SQL (SSMS)
As consultas e o passo a passo do tratamento vão ficar na pasta `sql/`.

➡️ Acesse: `sql/`

> Observação: aqui eu vou colocar os scripts (.sql) e prints do resultado do SSMS para mostrar o raciocínio e as evidências (consulta + output).

---

## Como reproduzir (bem direto)
1) Baixe os CSVs em `data/`
2) Importe no SQL Server (SSMS) e rode as consultas (quando eu subir os scripts, estarão em `sql/`)
3) Abra o `motorista-app.pbix` no Power BI Desktop
4) Se precisar apontar novamente os caminhos dos CSVs:  
   **Transformar dados (Power Query) → Configurações da fonte → Alterar caminho**

---

## Ferramentas
- **Python (Colab)**: geração do dataset em CSV  
- **SQL Server / SSMS**: consultas e tratamento  
- **Power BI**: modelagem, medidas DAX e dashboard

---

## Autor
Michael Andrade  
GitHub: https://github.com/whatevermic  
LinkedIn: https://www.linkedin.com/in/michaelgsandrade/
