# bibliotecaPandas

Projeto usado durante formação em dados para estudar a biblioteca pandas e técnicas básicas de visualização com seaborn, matplotlib e plotly.

## Sobre o caso

O notebook `Case1 - bibliotecaPandas.ipynb` analisa um dataset de vendas (arquivo `varejo.xlsx`) de uma loja virtual que atua nacionalmente, com registros de pedidos, canal de venda, preço, departamento e localização do cliente. O objetivo do exercício é praticar leitura, limpeza e análise exploratória de dados (EDA) usando pandas e preparar visuais com bibliotecas de visualização.

## Estrutura do dataset

O dataset carregado no notebook tem as seguintes características (conforme `varejo.info()`):

- Linhas: 80.228
- Colunas: 9

Colunas principais:

- `idcompra` (int) — identificador da compra
- `idcanalvenda` (object) — canal de venda (ex.: Mobile, Internet, Aplicativo)
- `bandeira` (object) — bandeira/segmento (ex.: A, B)
- `Data` (datetime) — data da compra
- `Preço` (float) — preço do produto (possui valores ausentes)
- `Preço_com_frete` (float) — preço com frete
- `Nome_Departamento` (object) — departamento/categoria do produto
- `estado` (object) — estado do cliente (possui valores ausentes)
- `cliente_Log` (int) — código do cliente (usado no notebook como identificador)

Observações sobre valores ausentes: existem 302 linhas com `Preço` nulo e 302 linhas com `estado` nulo (mesmo número), detectadas durante a EDA.

## Limpeza e normalização realizadas

No notebook foram aplicadas algumas transformações simples de limpeza/normalização:

- Unificação de valores do canal de venda: `APP` foi substituído por `Aplicativo` para evitar categorias duplicadas.
- Normalização do nome do departamento: espaços em `Nome_Departamento` foram substituídos por `_` (underscore) para facilitar manipulações e uso em colunas/labels.
- Verificação de linhas com valores nulos em `Preço` e `estado` para análise posterior (decisão de preenchimento ou remoção depende do objetivo analítico).

## Principais análises exploratórias (executadas no notebook)

- Contagem de compras/IDs por canal de venda (`idcanalvenda`): após a unificação, observou-se aproximadamente:
  - Aplicativo: 21.539 compras únicas
  - Internet: 24.515 compras únicas
  - Mobile: 24.732 compras únicas

- Distribuição por bandeira (`bandeira`): aproximadamente 27.679 compras na bandeira A e 38.483 na bandeira B.

- Contagem de compras por departamento (`Nome_Departamento`): os departamentos com maior número de compras incluem (top exemplos):
  - Telefones_e_Celulares — 14.495
  - Eletrodomesticos — 10.501
  - Eletroportateis — 9.593
  - TVs_e_Acessorios — 5.326
  - Informatica — 5.290

- Inspeção de linhas com valores faltantes: o notebook lista amostras das linhas com `estado` nulo para compreensão do problema.

O notebook também propõe (e prepara o ambiente para) métricas adicionais que podem ser calculadas, como média de preço por departamento, quantidade de vendas por mês, e outras segmentações por canal/bandeira. Essas métricas servem como próximos passos naturais para a análise.

## Visualização

O notebook importa seaborn (e pode usar matplotlib/plotly) para criar gráficos que ilustrem as distribuições por canal, bandeira e departamento, além de séries temporais de volume de vendas por mês. As visualizações ajudam a identificar sazonalidade, departamentos prioritários e diferença entre canais.

## Como executar

1. Garanta que o arquivo `varejo.xlsx` esteja no mesmo diretório do notebook ou carregue-o no ambiente (por exemplo, Google Colab).
2. Instale dependências (ex.: `pandas`, `seaborn`, `matplotlib`, `plotly`, `openpyxl`).
3. Abra `Case1 - bibliotecaPandas.ipynb` no Jupyter/Colab e execute as células em ordem.

Comandos úteis (ex.: em um ambiente local):

pip install pandas seaborn matplotlib plotly openpyxl

## Próximos passos sugeridos

- Tratar/implementar estratégia para valores ausentes em `Preço` e `estado` (remoção, imputação, ou investigação com fontes adicionais).
- Calcular métricas agregadas: ticket médio por departamento, vendas mensais e por canal, churn/recorrência por `cliente_Log`.
- Criar dashboards interativos (plotly dash / streamlit) para monitoramento das vendas por departamento e canal.

---

Arquivo analisado: `Case1 - bibliotecaPandas.ipynb` — ver o notebook para passos, código e saídas completas.