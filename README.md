# ⚽ Football Match Prediction System

![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![CatBoost](https://img.shields.io/badge/CatBoost-ML-yellow?logo=yandex&logoColor=white)
![Selenium](https://img.shields.io/badge/Selenium-Scraping-green?logo=selenium&logoColor=white)
![MySQL](https://img.shields.io/badge/MySQL-Database-orange?logo=mysql&logoColor=white)
![Status](https://img.shields.io/badge/Status-Production-brightgreen)

> **English** · [Español](#sistema-de-predicción-de-partidos-de-fútbol)

Production-grade web scraping and machine learning pipeline that predicts football match outcomes across **17 European and international leagues**. Running autonomously since 2023 with validated results.

---

## 📊 Results

| Metric | Value |
|--------|-------|
| 🏆 Annual ROI | **75.3%** |
| 📈 Sustained yield | **7.5%** |
| 🔮 Predictions per year | **7,000+** |
| 🌍 Leagues covered | **17** |
| ⏱️ In production | **2+ years** |

---

## 🔄 Pipeline Overview

```
Pinnacle (odds) ──────┐
                       ├──► Weekly dataset ──► CatBoost model ──► Predictions
WhoScored (stats) ────┘          │                                     │
                                  │                                     ▼
Historical DB ───────────────────►│                          Results validation
(football-data.co.uk)                                    (football-data.co.uk)
```

1. **Scrape odds** from Pinnacle using Selenium
2. **Scrape match statistics** from WhoScored (80+ metrics per team per match)
3. **Build rolling average datasets** from historical data (2009–present)
4. **Train CatBoost classifiers** with Bayesian hyperparameter optimization
5. **Generate weekly predictions** for three bet types: 1X2, BTTS, Over/Under 2.5
6. **Validate predictions** against real results from football-data.co.uk

---

## 🗂️ Project Structure

```
fut-pred-scrap/
│
├── src/
│   ├── scraping/
│   │   ├── scrap.py               # Pinnacle odds scraper (Selenium)
│   │   ├── dataset_by_league.py   # Per-league historical data scraper (WhoScored)
│   │   └── weekly_dataset.py      # All-leagues current-week scraper (WhoScored)
│   │
│   ├── preprocessing/
│   │   ├── making_average.py      # Rolling statistics aggregator
│   │   └── new_average.py         # Enhanced statistics processor
│   │
│   ├── models/
│   │   └── prediction_1x2.py      # CatBoost match outcome predictor
│   │
│   ├── pipeline/
│   │   ├── total_bets.py          # Consolidates all weekly predictions
│   │   ├── results_week.py        # Validates predictions vs real outcomes
│   │   └── correct_week.py        # Team name normalization utility
│   │
│   └── utils/
│       ├── dict_teams.py          # Team name mappings (3,000+ entries, multi-source)
│       └── lists_links.py         # League identifiers and scraping URLs
│
├── db/
│   ├── crear_bd.py                # MySQL database setup
│   └── crear_tablas.py            # Database schema (80+ stat columns)
│
├── experiments/                   # Model experimentation scripts
├── data/                          # Local data directory (gitignored)
├── requirements.txt
├── .gitignore
└── README.md
```

---

## 🛠️ Tech Stack

| Category | Libraries |
|----------|-----------|
| **Web Scraping** | `selenium` `webdriver-manager` |
| **Data Processing** | `pandas` `numpy` `openpyxl` |
| **Machine Learning** | `catboost` `scikit-learn` `scikit-optimize` |
| **Explainability** | `shap` |
| **Database** | `mysql-connector-python` |
| **Visualization** | `matplotlib` `seaborn` |

---

## 🌍 Leagues Covered

**Europe (15):** Premier League · Championship · League One · League Two · Bundesliga · 2. Bundesliga · La Liga · Serie A · Ligue 1 · Eredivisie · Liga Portugal · Süper Lig · Jupiler Pro League · Scottish Premiership

**Americas (2):** MLS · Brasileirão

---

## 📐 Features per Prediction

Each match prediction uses **80+ per-team statistics**, including:

- **Possession & control** — touches, pass accuracy, dribbles completed
- **Attacking** — shots by zone, type, and body part
- **Defensive** — tackles, clearances, aerial duels, interceptions
- **Passing** — type, length, height, direction, and target zone
- **Set pieces** — corners, free kicks
- **Individual ratings** — 11 starting players per team

---

## ⚙️ Setup

### 1. Clone and install

```bash
git clone https://github.com/braulio2113/fut-pred-scrap.git
cd fut-pred-scrap
pip install -r requirements.txt
```

> Google Chrome must be installed. ChromeDriver is managed automatically via `webdriver-manager`.

### 2. Configure database (optional)

```bash
export DB_HOST=localhost
export DB_USER=root
export DB_PASSWORD=your_password
```

### 3. Initialize database schema

```bash
python db/crear_bd.py
python db/crear_tablas.py
```

### 4. Place your historical data

Place CSV files from [football-data.co.uk](https://football-data.co.uk) in `data/` following the expected directory structure.

---

## 🧠 Model Details

- **Algorithm:** CatBoost Classifier
- **Hyperparameter optimization:** Bayesian search via `scikit-optimize`
- **Targets:** 1X2 result · BTTS (Both Teams to Score) · Over/Under 2.5 goals
- **Feature window:** Rolling averages over configurable match history
- **Validation:** Out-of-sample weekly backtesting against real results

---

## 💼 Freelance Services

I build custom web scraping and data pipelines for:

| Domain | What I deliver |
|--------|---------------|
| **Sports analytics** | Odds monitoring, statistics aggregation, real-time feeds |
| **E-commerce** | Price tracking, product monitoring, competitor analysis |
| **Financial data** | Market data extraction, news aggregation |
| **Business intelligence** | Custom dashboards built from scraped sources |
| **Data engineering** | ETL pipelines, database design, automated reports |

📧 **Contact:** brauliopg96@gmail.com

---

---

# ⚽ Sistema de Predicción de Partidos de Fútbol

> [English](#football-match-prediction-system) · **Español**

Pipeline de web scraping y machine learning para predecir resultados de partidos de fútbol en **17 ligas europeas e internacionales**. En operación autónoma desde 2023 con resultados validados.

---

## 📊 Resultados

| Métrica | Valor |
|---------|-------|
| 🏆 ROI anual | **75.3%** |
| 📈 Yield sostenido | **7.5%** |
| 🔮 Predicciones por año | **7,000+** |
| 🌍 Ligas cubiertas | **17** |
| ⏱️ En producción | **2+ años** |

---

## 🔄 Flujo del pipeline

```
Pinnacle (cuotas) ────┐
                       ├──► Dataset semanal ──► Modelo CatBoost ──► Predicciones
WhoScored (stats) ────┘          │                                        │
                                  │                                        ▼
BD histórica ────────────────────►│                           Validación de resultados
(football-data.co.uk)                                      (football-data.co.uk)
```

1. **Scrapea cuotas** de Pinnacle con Selenium
2. **Extrae estadísticas** de WhoScored (80+ métricas por equipo por partido)
3. **Construye datasets históricos** con promedios móviles (2009–presente)
4. **Entrena clasificadores CatBoost** con optimización bayesiana de hiperparámetros
5. **Genera predicciones semanales** para 1X2, BTTS y Over/Under 2.5 goles
6. **Valida predicciones** contra resultados reales de football-data.co.uk

---

## 🌍 Ligas cubiertas

**Europa (15):** Premier League · Championship · League One · League Two · Bundesliga · 2. Bundesliga · La Liga · Serie A · Ligue 1 · Eredivisie · Liga Portugal · Süper Lig · Jupiler Pro League · Scottish Premiership

**Américas (2):** MLS · Brasileirão

---

## ⚙️ Instalación

```bash
git clone https://github.com/braulio2113/fut-pred-scrap.git
cd fut-pred-scrap
pip install -r requirements.txt

# Variables de entorno para la base de datos
export DB_HOST=localhost
export DB_USER=root
export DB_PASSWORD=tu_contraseña

# Inicializar esquema de base de datos
python db/crear_bd.py
python db/crear_tablas.py
```

> Google Chrome debe estar instalado. ChromeDriver se gestiona automáticamente con `webdriver-manager`.

---

## 💼 Servicios freelance

Construyo pipelines de scraping y procesamiento de datos para:

| Área | Qué entrego |
|------|-------------|
| **Análisis deportivo** | Monitoreo de cuotas, agregación de estadísticas, feeds en tiempo real |
| **E-commerce** | Seguimiento de precios, monitoreo de productos, análisis de competencia |
| **Datos financieros** | Extracción de mercados, agregación de noticias |
| **Business intelligence** | Dashboards construidos desde fuentes scrapeadas |
| **Ingeniería de datos** | Pipelines ETL, diseño de bases de datos, reportes automatizados |

📧 **Contacto:** brauliopg96@gmail.com
