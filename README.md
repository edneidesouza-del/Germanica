# Grupo Germânica × Mercado Livre — Estudo de Resultados

Dashboard HTML interativo (arquivo único, Chart.js) com o desempenho dos anúncios de veículos do Grupo Germânica no Mercado Livre — período jun–set/2026.

**Link ao vivo:** https://edneidesouza-del.github.io/Germanica/

Abrir: [`index.html`](./index.html) (funciona localmente, sem servidor — é um arquivo único).

## Abas

- **Visão Geral** — KPIs, evolução mensal, canais, participação por marca, top modelos, planos Diamante x Plata, Novos x Usados, faixa de preço. Filtro de mês.
- **Por Loja** — ranking das lojas do grupo, KPIs e insights por loja selecionada, download do ranking em CSV.
- **Estoque** — busca e filtro por anúncio individual (marca/modelo/loja/mês/condição), "dias no ar" para usados, download em CSV.

## Nota metodológica

Foi identificado um padrão de outliers extremos nas colunas de visitas e contatos da planilha de origem, consistente com join sem casamento de data em tabela de snapshot diário (uma fração pequena de anúncios concentra parte desproporcional do total, mais forte em anúncios antigos e em meses mais distantes). O dashboard mostra o total sempre ao lado da mediana por anúncio (métrica mais robusta a outliers) e recomenda cautela na leitura de tendência mês a mês até a correção na fonte.

## Regenerar os dados

O dashboard é gerado a partir de `data/raw.csv` (exportado da planilha do cliente) via `aggregate.ps1` (PowerShell, sem dependência de Python/Node), que produz `data/data.json`. O `index.html` é montado injetando esse JSON em `template.html`. Esses arquivos de trabalho (dados brutos e scripts) não fazem parte do publicado — apenas `index.html` é versionado neste repositório.
