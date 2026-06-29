Pakistan Fintech & Currency Market Analytics Pipeline

An automated data engineering pipeline that collects live financial market data every 5 minutes using Apache Airflow 3.0, PostgreSQL, and Docker — all orchestrated via Astro CLI.


📊 What It Tracks

PipelineData SourceWhat It Collects🪙 CryptoCoinGecko APIBTC, ETH, USDT prices in USD & PKR💵 ForexExchangeRate APIUSD → PKR, GBP, EUR, AED🥇 GoldGoldAPI.io24k, 22k, 18k prices in PKR📈 PSX StocksYahoo Finance (yfinance)EFERT, FFC, LUCK, MCB, MARI


⚙️ Tech Stack


Apache Airflow 3.0 — DAG orchestration & scheduling
Astro CLI — local Airflow development environment
PostgreSQL — data storage
Docker — containerized infrastructure
Python — ETL logic
DBeaver — database management & querying



🏗️ Architecture

APIs (CoinGecko, ExchangeRate, GoldAPI, Yahoo Finance)
        ↓
   Extract Task (Python)
        ↓
   Transform Task (Python)
        ↓
   Load Task (PostgresHook)
        ↓
   PostgreSQL Database

Each pipeline follows the ETL pattern with 3 Airflow tasks:


extract_*_data() — fetches raw data from API
transform_*_data() — cleans and structures data
load_*_data() — inserts into PostgreSQL via PostgresHook



📁 Project Structure

pakistan-fintech-pipeline/
├── dags/
│   ├── crypto_pipeline.py    # BTC, ETH, USDT prices
│   ├── forex_pipeline.py     # USD exchange rates
│   ├── gold_pipeline.py      # Gold prices in PKR
│   └── psx_pipeline.py       # Pakistan Stock Exchange
├── Dockerfile
├── requirements.txt
├── packages.txt
└── README.md


🚀 Getting Started

Prerequisites


Docker Desktop
Astro CLI


Run Locally

bash# Clone the repo
git clone https://github.com/your-username/pakistan-fintech-pipeline.git
cd pakistan-fintech-pipeline

# Start Airflow
astro dev start

# Open Airflow UI
# Go to: localhost:8080
# Login: admin / admin

Setup Connections in Airflow UI

Go to Admin → Connections and add:

Postgres:

FieldValueConnection Idpostgres_defaultTypePostgresHostpostgresSchemapostgresLoginpostgresPasswordpostgresPort5432


📦 Dependencies

apache-airflow-providers-postgres
apache-airflow-providers-http
yfinance
requests
beautifulsoup4


🗄️ Database Tables

sql-- Crypto prices
SELECT * FROM crypto_prices LIMIT 10;

-- Forex rates
SELECT * FROM forex_rates LIMIT 10;

-- Gold prices
SELECT * FROM commodity_prices LIMIT 10;

-- PSX stocks
SELECT * FROM psx_stocks LIMIT 10;

👨‍💻 Author

Hadin Aslam Sonaly
BS Data Science — Dawood University of Engineering & Technology (DUET), Karachi


📌 Note

This project was built for portfolio purposes to demonstrate real-world data engineering skills including pipeline orchestration, API integration, and database management.
