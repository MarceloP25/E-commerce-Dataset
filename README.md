# 📊 Análise de E-commerce de Moda — Myntra Dataset

Análise exploratória e avançada de um dataset com ~168.000 produtos de moda e lifestyle extraídos da plataforma **Myntra** (e-commerce indiano), cobrindo padrões de preço, desconto, avaliações e comportamento de portfólio.

---

## 🗂️ Estrutura do Projeto

```
.
├── dados/
│   ├── data.csv               # Dataset original (~168k produtos)
│   └── data_enriched.csv      # Base enriquecida (gerada após analiseAvancada)
├── analiseExploratoria.ipynb  # Análise exploratória completa (EDA)
├── analiseAvancada.ipynb      # Feature engineering + modelos de ML
└── README.md
```

---

## 📁 Dataset

| Campo | Descrição |
|---|---|
| `product_name` | Nome do produto |
| `brand_name` | Marca |
| `rating` | Avaliação média (0–5) |
| `rating_count` | Número de avaliações |
| `marked_price` | Preço original |
| `discounted_price` | Preço com desconto |
| `discount_percent` | Percentual de desconto |
| `product_tag` | Categoria do produto |
| `sizes` | Tamanhos disponíveis |

> ⚠️ **~45% dos produtos têm `rating = 0` e `rating_count = 0`** — produtos sem nenhuma avaliação registrada. Ambos os notebooks tratam esse ponto explicitamente.

---

## 📓 Notebooks

### `analiseExploratoria.ipynb`
Análise exploratória de dados (EDA) com foco em entendimento do portfólio:

- Visão geral e qualidade dos dados
- Distribuição de preços e descontos (com tratamento de outliers)
- Relação desconto × rating (hexbin + boxplot por faixa)
- Análise de avaliações (apenas produtos avaliados)
- Análise por marca: ranking de rating ponderado por volume
- Análise por categoria: preço médio e desconto médio
- KPIs globais do portfólio
- Feature engineering: **Valor Percebido**
- Identificação de produtos supervalorizados e subvalorizados
- Mapa de calor de correlações

### `analiseAvancada.ipynb`
Feature engineering e modelos de Machine Learning:

| Técnica | Objetivo |
|---|---|
| Feature engineering relativo | Preço relativo à categoria, z-score dentro da marca |
| KMeans + Elbow + Silhouette | Clusterização comportamental de produtos |
| PCA | Visualização 2D dos clusters |
| Regressão Linear | Identificar o que explica o rating (com R², RMSE, CV) |
| Regressão Logística | Classificar produtos "bons" vs "fracos" (com ROC-AUC) |
| Isolation Forest | Detecção de anomalias de precificação |
| TF-IDF | Correlação entre termos do nome e rating/preço |

---

## ⚙️ Como Executar

### Pré-requisitos

```bash
pip install pandas numpy matplotlib seaborn scikit-learn jupyter
```

### Passo a passo

```bash
# 1. Clone o repositório
git clone <url-do-repositorio>
cd <pasta-do-projeto>

# 2. Extraia os dados
unzip dados.zip

# 3. Inicie o Jupyter
jupyter notebook

# 4. Execute os notebooks na ordem:
#    analiseExploratoria.ipynb → analiseAvancada.ipynb
```

> Os notebooks usam caminho relativo `./dados/data.csv`. Certifique-se de que a pasta `dados/` está no mesmo diretório dos notebooks.

---

## 🔍 Principais Achados

- **~45% dos produtos não têm avaliação** — dado crítico para qualquer análise de rating
- **Desconto não garante boa avaliação** — correlação fraca/negativa entre desconto e rating
- **Distribuição de preços é fortemente assimétrica** — cauda longa de produtos premium
- **Rating médio ponderado difere significativamente do simples** — marcas com poucos produtos distorcem médias simples
- **Modelos de ML confirmam a hipótese**: preço e desconto explicam pouco do rating (R² baixo na regressão)
- **Isolation Forest** identifica produtos com posicionamento incoerente (caro + mal avaliado)

---

## 🛠️ Tecnologias

![Python](https://img.shields.io/badge/Python-3.10+-blue)
![Pandas](https://img.shields.io/badge/Pandas-2.x-green)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.x-orange)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-yellow)
![Seaborn](https://img.shields.io/badge/Seaborn-Visualization-lightblue)

---

## 📄 Licença

Este projeto é de uso educacional e demonstrativo. O dataset é de domínio público.
