# Análise da Sazonalidade de Queimadas no Brasil

[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/datarod/brazil-fire-seasonality/blob/main/Sazonalidade_Queimadas.ipynb)
![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![BigQuery](https://img.shields.io/badge/Google-BigQuery-yellow)
![Status](https://img.shields.io/badge/Status-Completed-success)

## Sobre o Projeto

Este repositório documenta uma exploração analítica dos microdados de focos de calor do **INPE (BDQueimadas)**, acessados através da infraestrutura de *datalake* da **Base dos Dados**.

O objetivo foi aplicar **Estatística Circular (Direcional)** em uma série histórica massiva (2006-Presente) para modelar a fenologia do fogo nos estados brasileiros, tratando o tempo como um ciclo contínuo e não como uma variável linear.

### Destaques Técnicos
* **Acesso a Dados:** Utilização do *Google BigQuery* para filtragem e agregação *server-side* de milhões de registros, demonstrando a eficiência do ecossistema de dados abertos brasileiro.
* **Correção Estatística para Big Data:** Implementação da **Aproximação Assintótica de Rayleigh**. As fórmulas estatísticas tradicionais para testes de significância falham (geram *overflow*/infinito) quando aplicadas a milhões de pontos de dados; ajustamos o algoritmo para suportar essa escala.
* **Visualização:** Geração de gráficos polares ("relógios anuais") diagramados automaticamente para publicação em redes sociais (Layout Vertical/Carrossel).

Os gráficos gerados representam a "bússola" da temporada de fogo em cada UF:
* **Linha Vermelha (Vetor Médio):** Aponta para a data exata do pico estatístico de queimadas.
* **Setor Amarelo (Desvio Padrão Circular):** Representa a janela de dispersão (duração da temporada crítica).

## Stack Tecnológica

* **Linguagem:** Python
* **Fonte de Dados:** [Base dos Dados](https://basedosdados.org/) (Tabela tratada `br_inpe_queimadas`)
* **Engine:** Google BigQuery
* **Bibliotecas Principais:**
    * `scipy.stats`: Para cálculos de média e desvio padrão circular.
    * `plotly`: Para renderização vetorial e grids polares.
    * `pandas-gbq`: Conector com o BigQuery.

## Como Executar

O projeto foi otimizado para rodar no **Google Colab**, facilitando a autenticação com o Google Cloud Platform (GCP).

1.  Clone este repositório ou clique no botão "Open in Colab" acima.
2.  Abra o notebook `Sazonalidade_Queimadas.ipynb`.
3.  Insira seu `PROJECT_ID` do Google Cloud na célula de configuração.
4.  Execute o pipeline. O script irá gerar:
    * Análise estatística tabular (com P-valor corrigido).
    * 3 Figuras otimizadas para carrossel (formato 4:5).

## 👨‍🔬 Autor

**Rodrigo Lacerda Brito Neto**
*Cientista de Dados Geoespaciais | Análise da Paisagem*
[LinkedIn](https://www.linkedin.com/in/datarod)
