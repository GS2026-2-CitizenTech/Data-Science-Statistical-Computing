# ☕ Global Solution 2026 — CitizenTech: Estratégia de Consumo Consciente de Cápsulas de Café

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg?style=flat&logo=python&logoColor=white)
![Google Colab](https://img.shields.io/badge/Google_Colab-Notebook-F9AB00.svg?style=flat&logo=googlecolab&logoColor=white)
![Data Science](https://img.shields.io/badge/Data_Science-Estatística_Aplicada-2ea44f.svg)

Investigação estatística e análise multicritério desenvolvida para o desafio **Global Solution (CitizenTech)**, com o objetivo de determinar a estratégia mais sustentável e socialmente responsável para o consumo de cápsulas de café.

---

## 📋 Sobre o Projeto

A transição para o consumo consciente exige ir além de análises simplistas baseadas em uma única métrica (como observar apenas as emissões de carbono). Neste projeto, avaliamos um universo amostral de **$5.120$ cápsulas** distribuídas uniformemente entre **8 marcas** (*Aurora, Bravura, Cerrado, Delta, Estação, Flora, Granito e Horizonte*).

Cruzando dados quantitativos ambientais, operacionais e de governança social com relatórios estratégicos, aplicamos testes de hipóteses rigorosos e um modelo de **otimização multicritério** para fundamentar nossa recomendação.

---

## 👥 Integrantes (Turma 2ESPI)

* **Giovana Carnevali** — RM566196
* **Henrique Vicente** — RM564116
* **Murilo Macedo** — RM563397
* **Yasmin Amorim** — RM563645

---

## 🧪 Metodologia e Testes Estatísticos

Toda a análise foi conduzida em ambiente **Google Colab** utilizando `pandas`, `numpy`, `scipy`, `statsmodels` e `scikit-learn`:

1. **Unificação e Tratamento de Dados:** Consolidação das 8 bases de dados ($n = 640$ por marca) e tratamento semântico de valores ausentes (considerando campos nulos em auditorias como *ausência de fiscalização*, e não ausência de irregularidades).
2. **Verificação de Pressupostos:**
   * **Shapiro-Wilk:** Confirmação da normalidade dos dados de emissões totais ($p > 0.05$ em todas as marcas).
   * **Levene:** Confirmação da homocedasticidade / homogeneidade das variâncias ($p = 0.3755$).
3. **Testes de Hipóteses Paramétricos e Não Paramétricos:**
   * **ANOVA de 1 Via & Post-hoc Tukey HSD:** Avaliação de diferenças significativas entre marcas para Pegada de Carbono ($F = 529.80, p < 0.0001$), Pegada Hídrica ($F = 163.61, p < 0.0001$), Desmatamento Atribuído ($F = 35.91, p < 0.0001$) e Remuneração Relativa ($F = 5.30, p < 0.0001$).
   * **ANOVA de Fim de Vida por Material:** Teste que comprovou que o tipo de material da embalagem (alumínio, compostável, fibra mista ou plástico) não altera estatisticamente as emissões de fim de vida ($F = 0.3207, p = 0.8104$).
   * **Kruskal-Wallis:** Avaliação do índice de efluentes tóxicos entre as marcas ($H = 486.22, p < 0.0001$).
   * **Teste Qui-Quadrado ($\chi^2$) de Independência:** Comprovação de que a ocorrência de trabalho infantil na cadeia produtiva depende criticamente da governança de cada marca ($\chi^2 = 40.8728, p = 8.56 \times 10^{-7}$).
   * **Correlação de Pearson:** Identificação do *trade-off* ambiental entre carbono e pegada hídrica ($r = -0.2078, p < 0.0001$).
4. **Score Global Multicritério:** Normalização via `MinMaxScaler` ponderando penalidades ambientais/sociais e bônus de reciclagem efetiva e remuneração justa.

---

## 📊 Resumo dos Resultados

| Marca | Média $\text{CO}_2\text{e}$ (g) | Média Água (L) | Desmatamento ($\text{m}^2$) | Incidência Trabalho Infantil | Reciclagem Efetiva | Score Multicritério |
| :--- | :---: | :---: | :---: | :---: | :---: | :---: |
| **Aurora** | **179.24** | **12.64** | **1.13** | **8.6%** (43/498) | **0.29** | **0.015** *(Recomendada)* |
| Bravura | 145.06 | 15.82 | 1.55 | 12.0% (56/468) | 0.43 | 1.217 |
| Cerrado | 155.19 | 20.28 | 1.43 | 15.1% (73/482) | 0.29 | 1.357 |
| Delta | 215.15 | 11.15 | 1.00 | 6.2% (30/480) | 0.21 | 0.000 |
| Estação | 164.63 | 17.17 | 1.70 | 21.1% (36/171) | 0.35 | 3.286 |
| Flora | 168.69 | 19.59 | 1.32 | 11.0% (53/481) | 0.30 | 1.431 |
| Granito | 194.80 | 12.25 | 1.53 | 12.6% (60/477) | 0.26 | 2.018 |
| Horizonte | 173.57 | 15.65 | 1.68 | 13.9% (67/481) | 0.31 | 1.998 |

---

## 🏆 Conclusão e Escolha Estratégica: Marca Aurora

A **Aurora** foi selecionada como a diretriz recomendada para a CitizenTech por representar o ponto de equilíbrio ideal entre preservação ambiental e responsabilidade social:
* **Governança e Direitos Humanos:** Apresenta alta transparência na cadeia (498 auditorias realizadas) e uma das menores taxas de trabalho infantil ($8.6\%$), evitando o passivo social observado em marcas como *Bravura* ($12.0\%$) e *Estação* ($21.1\%$ de incidência com baixa taxa de auditoria).
* **Eficiência Ambiental Equilibrada:** Controla simultaneamente a pegada hídrica ($12.64\text{ L}$) e o desmatamento ($1.13\text{ m}^2$), superando a *Delta* (que possui baixo uso hídrico, mas falha criticamente nas emissões de carbono e reciclagem efetiva).

---


## 🚀 Como Executar o Notebook

1. Faça o download do arquivo `.ipynb` disponível na pasta `notebooks/`.
2. Abra o [Google Colab](https://colab.research.google.com/) e faça o upload do notebook.
3. Certifique-se de carregar os 8 arquivos CSV correspondentes às marcas (`01_aurora.csv` a `08_horizonte.csv`) no diretório raiz da sessão.
4. Execute as células sequencialmente para reproduzir as estatísticas descritivas, testes de hipóteses e o ranking multicritério.
