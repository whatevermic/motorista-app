# SQL (SSMS) — Consultas e resultados (Storyline)

Base: `mobilidade_urbana`  
Tabelas: `dbo.corridas`, `dbo.motoristas`  
Relacionamento: `corridas.motorista_id = motoristas.motorista_id`

---

## 01) KPIs gerais

**Query**
```sql
SELECT
    COUNT(*) AS total_corridas,
    SUM(CASE WHEN aceita_corrida_int = 1 THEN 1 ELSE 0 END) AS total_aceitas,
    SUM(CASE WHEN aceita_corrida_int = 0 THEN 1 ELSE 0 END) AS total_recusas,
    CAST(
        100.0 * SUM(CASE WHEN aceita_corrida_int = 1 THEN 1 ELSE 0 END) / COUNT(*)
        AS DECIMAL(5,2)
    ) AS taxa_aceitacao_pct
FROM dbo.corridas;
Print: https://github.com/whatevermic/motorista-app/blob/main/images/SQL_PRINT_01.png

--Resultado (o que esse output diz):
Total de corridas: 100.000
Corridas aceitas: 79.110
Corridas recusadas: 20.890
Taxa de aceitação: 79,11%--

