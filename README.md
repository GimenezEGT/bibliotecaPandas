[![Jupyter Notebook](https://img.shields.io/badge/Jupyter-Notebook-orange)](https://github.com/GimenezEGT/bibliotecaPandas/blob/main/Case1%20-%20bibliotecaPandas.ipynb) [![Python](https://img.shields.io/badge/python-3.8%2B-blue)](https://www.python.org/)

# bibliotecaPandas

This repository contains a short case study used during a data training course to practice data analysis with pandas and basic data visualization with seaborn, matplotlib and plotly.

## About the case

The notebook `Case1 - bibliotecaPandas.ipynb` analyzes a retail sales dataset (`varejo.xlsx`) from an online store that operates across Brazil. The dataset contains purchase records with information such as sales channel, price, product department, customer location, and purchase date. The main goal of the exercise is to practice reading, cleaning and exploratory data analysis (EDA) using pandas and to prepare visualizations with common plotting libraries.

Notebook: https://github.com/GimenezEGT/bibliotecaPandas/blob/main/Case1%20-%20bibliotecaPandas.ipynb

## Dataset structure (as observed in the notebook)

- Rows: 80,228
- Columns: 9

Main columns:

- `idcompra` (int) — purchase identifier
- `idcanalvenda` (object) — sales channel (e.g., Mobile, Internet, Aplicativo)
- `bandeira` (object) — segment/flag (e.g., A, B)
- `Data` (datetime) — purchase date
- `Preço` (float) — product price (contains missing values)
- `Preço_com_frete` (float) — price including shipping
- `Nome_Departamento` (object) — product department/category
- `estado` (object) — customer's state (contains missing values)
- `cliente_Log` (int) — customer identifier

Note on missing values: the notebook detects ~302 rows with missing values in `Preço` and `estado`.

## Cleaning and normalization applied

The notebook performs several simple cleaning steps and normalizations:

- Unify sales channel labels: `APP` is replaced with `Aplicativo` to avoid duplicate categories.
- Normalize department names: spaces in `Nome_Departamento` are replaced with underscores (`_`) to facilitate column/label usage.
- Inspect rows with missing `Preço` and `estado` to understand the issue before deciding on removal or imputation.

## Key exploratory analyses performed

- Unique purchases by sales channel (`idcanalvenda`) after unification:
  - Aplicativo: ~21,539 unique purchases
  - Internet: ~24,515 unique purchases
  - Mobile: ~24,732 unique purchases

- Distribution by `bandeira` (segment):
  - A: ~27,679 purchases
  - B: ~38,483 purchases

- Purchases by department (top examples):
  - Telefones_e_Celulares — ~14,495
  - Eletrodomesticos — ~10,501
  - Eletroportateis — ~9,593
  - TVs_e_Acessorios — ~5,326
  - Informatica — ~5,290

- Inspection of rows with missing values: the notebook shows samples of rows with null `estado`/`Preço` for further investigation.

The notebook also lists logical next metrics to compute (mean price by department, monthly sales counts, average customer income per channel, average age by `bandeira`, etc.).

## How to run

1. Place `varejo.xlsx` in the same directory as the notebook or upload it to the environment (e.g., Google Colab).
2. Install dependencies: `pandas`, `seaborn`, `matplotlib`, `plotly`, `openpyxl`.
3. Open `Case1 - bibliotecaPandas.ipynb` in Jupyter or Colab and run the cells in order.

A `requirements.txt` file is included to reproduce the environment locally.

Example (local environment):

pip install -r requirements.txt

## Suggested next steps

- Decide and implement a strategy for missing values in `Preço` and `estado` (drop, impute, or enrich with external data).
- Compute aggregated metrics: average ticket by department, monthly sales and channel performance, customer repeat purchase rates using `cliente_Log`.
- Build an interactive dashboard (Plotly Dash or Streamlit) to monitor sales by department and channel.
- Replace the placeholder figures in `images/` with exported PNG/SVG images generated from the notebook.

---

## Versão em Português / Portuguese version

Este repositório contém um case usado em formação de dados para praticar análise com pandas e visualização de dados com seaborn, matplotlib e plotly.

O notebook `Case1 - bibliotecaPandas.ipynb` analisa o arquivo `varejo.xlsx`, contendo registros de compras de uma loja virtual (canal de venda, preço, departamento, estado do cliente e data). O objetivo é praticar leitura, limpeza e análise exploratória (EDA) e gerar visualizações.

Veja o notebook para o código completo, saídas e gráficos.

---

Analyzed file: `Case1 - bibliotecaPandas.ipynb` — open the notebook for full code, outputs and charts.
