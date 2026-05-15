# ⚡ ETL Pokémon — Pipeline Completo + Dashboards + Machine Learning

<div align="center">

![Python](https://img.shields.io/badge/Python-3.12-3776AB?style=for-the-badge&logo=python&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-16-336791?style=for-the-badge&logo=postgresql&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-1.28.1-FF4B4B?style=for-the-badge&logo=streamlit&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-2.0.23-D71F00?style=for-the-badge&logo=sqlalchemy&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-5.17.0-3F4F75?style=for-the-badge&logo=plotly&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.1.0-150458?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-1.24.3-013243?style=for-the-badge&logo=numpy&logoColor=white)
![Scikit-learn](https://img.shields.io/badge/Scikit--learn-1.3.2-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-1.0.0-F37626?style=for-the-badge&logo=jupyter&logoColor=white)
![Alembic](https://img.shields.io/badge/Alembic-1.12.1-6BA81E?style=for-the-badge)
![Matplotlib](https://img.shields.io/badge/Matplotlib-3.8.0-11557C?style=for-the-badge&logo=python&logoColor=white)
![Requests](https://img.shields.io/badge/Requests-2.31.0-20232A?style=for-the-badge&logo=python&logoColor=white)

**Pipeline ETL completo para extracción, almacenamiento, visualización y análisis con Machine Learning de 1000 Pokémon usando PokéAPI.**

</div>

---

## 📖 Descripción General

Este proyecto implementa un sistema completo de **Minería de Datos** que integra cuatro grandes componentes:

1. **Pipeline ETL** — Extracción de 1000 Pokémon desde PokéAPI, transformación y carga en PostgreSQL
2. **Base de Datos** — Almacenamiento estructurado con SQLAlchemy ORM y migraciones versionadas con Alembic
3. **Dashboards Interactivos** — Tres dashboards con Streamlit y Plotly para visualización de datos
4. **Machine Learning** — Tres notebooks de Jupyter con modelos supervisados de predicción y clasificación

---

## 🎯 Objetivos

- Implementar un pipeline ETL real usando Python y una API pública
- Almacenar 1000 registros en PostgreSQL con migraciones versionadas
- Crear tres dashboards profesionales e interactivos con Streamlit y Plotly
- Aplicar modelos de Machine Learning supervisado (regresión y clasificación)
- Aplicar buenas prácticas: logging, métricas ETL, manejo de errores, variables de entorno

---

## 🧱 Arquitectura del Sistema

```
PokéAPI
   │
   ▼
extractor_db.py ──► PostgreSQL (pokedb)
                         │
          ┌──────────────┼──────────────────┐
          ▼              ▼                  ▼
  dashboard_app.py  dashboard_advanced.py  dashboard_interactive.py
  (Básico)          (Avanzado)             (Interactivo)
          │
          ▼
     notebooks/
  ├── arbol_decision_pokemon.ipynb      (CB11 - Regresión)
  ├── regresion_logistica_pokemon.ipynb (CB13 - Clasificación)
  └── arbol_clasificacion_pokemon.ipynb (CB14 - Clasificación)
```

---

## 🛠️ Tecnologías

| Herramienta | Versión | Uso |
|---|---|---|
| **Python** | 3.12 | Lenguaje base del proyecto |
| **PostgreSQL** | 16 | Base de datos relacional |
| **SQLAlchemy** | 2.0.23 | ORM para manejo de BD |
| **Alembic** | 1.12.1 | Migraciones versionadas de la BD |
| **Streamlit** | 1.28.1 | Dashboards interactivos |
| **streamlit-lottie** | 0.0.5 | Animaciones Lottie en los dashboards |
| **Plotly** | 5.17.0 | Gráficas interactivas |
| **Pandas** | 2.1.0 | Transformación y análisis de datos |
| **NumPy** | 1.24.3 | Operaciones numéricas |
| **Matplotlib** | 3.8.0 | Gráficas estáticas de análisis |
| **Seaborn** | latest | Gráficas estadísticas en notebooks |
| **Scikit-learn** | 1.3.2 | Modelos de Machine Learning |
| **Jupyter** | 1.0.0 | Notebooks de análisis y ML |
| **Requests** | 2.31.0 | Peticiones HTTP a PokéAPI y animaciones Lottie |
| **psycopg2-binary** | 2.9.9 | Conector Python-PostgreSQL |
| **python-dotenv** | 1.0.0 | Manejo de variables de entorno |
| **openpyxl** | 3.1.2 | Exportación a Excel |
| **PokéAPI** | — | Fuente de datos (API REST pública, sin API key) |
| **WSL Ubuntu** | — | Entorno de desarrollo en Windows |
| **VS Code** | — | Editor de código principal |

---

## 📂 Estructura del Proyecto

```
etl-pokeapi/
├── scripts/
│   ├── database.py              # Configuración de conexión a PostgreSQL
│   ├── models.py                # Modelos SQLAlchemy (Pokemon y MetricasETL)
│   ├── extractor.py             # Extracción desde PokéAPI → CSV/JSON
│   ├── extractor_db.py          # Extracción y carga directa a PostgreSQL (1000 Pokémon)
│   ├── cargador.py              # Carga de CSV a PostgreSQL
│   ├── visualizador.py          # Gráficas con Matplotlib
│   ├── consultas.py             # Consultas analíticas a la BD
│   └── test_db.py               # Prueba de conexión a PostgreSQL
│
├── alembic/
│   └── versions/                # Migraciones versionadas de la BD
│
├── notebooks/
│   ├── arbol_decision_pokemon.ipynb      # CB11 — Árbol de Decisión (Regresión HP)
│   ├── regresion_logistica_pokemon.ipynb # CB13 — Regresión Logística (Legendario)
│   └── arbol_clasificacion_pokemon.ipynb # CB14 — Árbol de Clasificación (Legendario)
│
├── data/
│   ├── pokemon.csv              # Dataset exportado
│   ├── pokemon_raw.json         # Datos crudos de la API
│   └── graficas/                # Gráficas generadas por los notebooks
│       ├── exploracion_datos.png
│       ├── dt_80-20.png
│       ├── dt_70-30.png
│       ├── dt_60-40.png
│       ├── dt_comparativa_splits.png
│       └── dt_arbol_pedagogico.png
│
├── logs/
│   └── etl.log                  # Registro de ejecuciones del ETL
│
├── dashboard_app.py             # Dashboard básico
├── dashboard_advanced.py        # Dashboard avanzado con análisis profundo
├── dashboard_interactive.py     # Dashboard interactivo con control total
├── requirements.txt             # Dependencias del proyecto
├── alembic.ini                  # Configuración de Alembic
├── .env                         # Variables de entorno (NO se sube a GitHub)
├── .gitignore
└── README.md
```

---

## ⚙️ Instalación y Configuración

### Prerrequisitos

- Python 3.12+
- PostgreSQL 16 instalado y corriendo
- WSL Ubuntu (si usas Windows)

### 1. Clonar el repositorio

```bash
git clone https://github.com/NicolasAlvarez25/Grupo-11-Miner-a-de-datos.git
cd "Grupo-11-Miner-a-de-datos/Proyecto 11 Pokemon/etl-pokeapi"
```

### 2. Crear entorno virtual e instalar dependencias

```bash
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```

### 3. Crear la base de datos en PostgreSQL

```bash
sudo -u postgres psql
```
```sql
CREATE DATABASE pokedb;
ALTER USER postgres WITH PASSWORD 'tu_contraseña';
\q
```

### 4. Configurar variables de entorno

Crea un archivo `.env` en la raíz del proyecto:

```env
POKEAPI_BASE_URL=https://pokeapi.co/api/v2
DB_HOST=localhost
DB_PORT=5432
DB_USER=postgres
DB_PASSWORD=tu_contraseña
DB_NAME=pokedb
```

### 5. Aplicar migraciones

```bash
alembic upgrade head
```

### 6. Ejecutar el ETL (extraer 1000 Pokémon)

```bash
PYTHONPATH=. python scripts/extractor_db.py
```

> ⏱️ Este proceso tarda varios minutos ya que extrae uno a uno desde la API

### 7. Verificar la carga

```bash
sudo -u postgres psql -d pokedb
SELECT COUNT(*) FROM pokemon;  -- Debe mostrar 1000
\q
```

---

## 📊 Datos Extraídos

Por cada Pokémon se extraen los siguientes campos:

| Campo | Descripción |
|---|---|
| `id`, `nombre` | Identificador y nombre |
| `tipos`, `habilidades` | Tipos y habilidades (incluyendo ocultas) |
| `hp`, `ataque`, `defensa` | Stats de combate |
| `ataque_especial`, `defensa_especial`, `velocidad` | Stats especiales |
| `es_legendario`, `es_mitico` | Clasificación especial |
| `habitat`, `generacion` | Datos de especie |
| `descripcion` | Descripción del Pokédex |
| `sprite_frente`, `sprite_shiny` | Imágenes del Pokémon (normal y Shiny) |
| `tasa_captura`, `felicidad_base` | Datos de captura |
| `peso`, `altura` | Datos físicos |
| `total_movimientos` | Cantidad de movimientos disponibles |
| `cadena_evolucion_url` | URL de la cadena de evolución |
| `fecha_extraccion` | Timestamp del ETL |

> **Total: 1000 registros · ~25 columnas**

---

## 🗂️ Scripts

| Script | Descripción |
|---|---|
| `extractor_db.py` | Extrae 1000 Pokémon de PokéAPI y los guarda en PostgreSQL. Registra métricas de cada ejecución. |
| `extractor.py` | Extrae datos y los guarda en CSV y JSON localmente. |
| `database.py` | Configura la conexión a PostgreSQL usando SQLAlchemy. |
| `models.py` | Define las tablas `pokemon` y `metricas_etl` con SQLAlchemy ORM. |
| `consultas.py` | Consultas analíticas: top atacantes, velocistas, distribución de tipos, legendarios. |
| `test_db.py` | Verifica que la conexión a PostgreSQL funcione correctamente. |
| `cargador.py` | Carga datos desde CSV a PostgreSQL. |
| `visualizador.py` | Genera gráficas de análisis con Matplotlib. |

---

## 📈 Dashboards

Ejecuta cada dashboard con:

```bash
source venv/bin/activate

# Dashboard básico
PYTHONPATH=. streamlit run dashboard_app.py

# Dashboard avanzado
PYTHONPATH=. streamlit run dashboard_advanced.py

# Dashboard interactivo
PYTHONPATH=. streamlit run dashboard_interactive.py
```

Abre tu navegador en `http://localhost:8501`

---

### 🟢 Dashboard Básico (`dashboard_app.py`)

| Sección | Contenido |
|---|---|
| 📊 Métricas | Total Pokémon, legendarios, mayor HP, mayor ataque, mayor velocidad |
| 📊 Estadísticas | Top 10 por ataque y velocidad, ataque vs defensa, HP vs velocidad |
| 🔥 Tipos | Distribución de tipos en barras y torta |
| ⭐ Legendarios | Lista de legendarios y míticos con sprites |
| 🖼️ Pokédex Visual | Galería de 150 Pokémon con sprites normales y Shiny |
| 📋 Datos | Tabla descargable en CSV |

**Extras:** Filtros por tipo, legendarios y míticos · Animaciones Lottie

---

### 🔵 Dashboard Avanzado (`dashboard_advanced.py`)

| Sección | Contenido |
|---|---|
| 📊 Vista General | Histogramas, diagramas de caja, distribución por hábitat, scatter peso vs altura |
| 🔥 Tipos | Distribución, torta, radar promedio por tipo, promedio de stats por tipo |
| 🏆 Rankings | Ranking dinámico por cualquier stat con podio visual y sprites |
| 🆚 Comparador | Compara dos Pokémon con gráfico radar dual y tabla de ganadores |
| ⭐ Legendarios | Legendarios y míticos con sprites y gráfica de stats especiales |
| 🖼️ Pokédex Visual | Galería de 150 Pokémon con búsqueda, filtro por tipo y modo Shiny |
| 📋 Métricas ETL | Historial de ejecuciones con gráficas de registros y tiempos |

**Extras:** Caché de datos · Animaciones Lottie · Sprites Shiny

---

### 🔴 Dashboard Interactivo (`dashboard_interactive.py`)

| Sección | Contenido |
|---|---|
| 📊 Estadísticas | Top 10 ataque/velocidad, scatter ataque vs defensa, HP vs velocidad, box plot |
| 🔥 Tipos | Distribución, torta, radar por tipo seleccionable |
| 🆚 Comparador | Radar dual, tabla ganador por stat, sprites con modo Shiny |
| ⭐ Especiales | Legendarios y míticos con stats comparativos |
| 🖼️ Pokédex Visual | Galería con búsqueda, filtro de tipo y columnas ajustables (3–6) |
| 📋 Datos y Exportar | Columnas y orden personalizables, descarga CSV completo y filtrado |

**Extras:** Filtros simultáneos por HP, ataque, defensa, velocidad y poder total · Indicadores en tiempo real · Animaciones Lottie · Sprites Shiny desde el panel lateral

---

## 🤖 Machine Learning — Notebooks de Jupyter

### Ejecutar Jupyter

```bash
source venv/bin/activate
PYTHONPATH=. jupyter notebook --no-browser --ip=0.0.0.0
```

---

### 📓 Notebook 1 — Árbol de Decisión para Regresión (CB10 / CB11)
**Archivo:** `notebooks/arbol_decision_pokemon.ipynb`

**Objetivo:** Predecir el **HP** de cada Pokémon a partir de sus características estadísticas.

| | |
|---|---|
| **Modelo** | `DecisionTreeRegressor` (scikit-learn) |
| **Variable objetivo (Y)** | HP — Puntos de vida |
| **Variables predictoras (X)** | Ataque, Defensa, Ataque Especial, Defensa Especial, Velocidad, Peso, Altura, Tasa de Captura, Felicidad |
| **Dataset** | 1000 Pokémon desde PostgreSQL |

**Metodología — Tres Splits para demostrar robustez:**

| Split | Entrenamiento | Prueba | Propósito |
|---|---|---|---|
| 80/20 | 80% | 20% | Estándar — maximiza datos de entrenamiento |
| 70/30 | 70% | 30% | Balanceado |
| 60/40 | 60% | 40% | Exigente — menos datos de entrenamiento |

**Métricas calculadas:** R², MSE, RMSE, MAE

**Contenido del notebook (16 celdas):**
- Importaciones y configuración inicial
- Carga de datos desde PostgreSQL vía `scripts/database.py`
- Exploración visual del dataset (distribución HP, scatter HP vs stats)
- Preparación de vectores X e Y
- Función `evaluar_split()` reutilizable con gráficas integradas
- Entrenamiento con los 3 splits
- Tabla comparativa y gráfico de barras de métricas
- Árbol pedagógico (max_depth=3) completamente visualizado con `plot_tree()`
- Reglas del árbol en formato texto con `export_text()`
- Análisis de overfitting y estrategias de mejora
- Conclusiones finales

**Conceptos explicados (CB10):** nodo raíz, hojas, profundidad, squared_error, samples, value, algoritmo CART, overfitting, `random_state`

---

### 📓 Notebook 2 — Regresión Logística (CB13 / CB14)
**Archivo:** `notebooks/regresion_logistica_pokemon.ipynb`

**Objetivo:** Clasificar si un Pokémon es **legendario o no legendario** usando regresión logística.

| | |
|---|---|
| **Modelo** | `LogisticRegression` (scikit-learn) |
| **Variable objetivo (Y)** | `es_legendario` → 0 = No legendario / 1 = Legendario |
| **Variables predictoras (X)** | HP, Ataque, Defensa, Ataque Especial, Defensa Especial, Velocidad, Peso, Altura |
| **Dataset** | 1000 Pokémon desde PostgreSQL |
| **Tipo de tarea** | Clasificación Binaria (CB14) |

**Métricas calculadas:** Accuracy, AUC-ROC, Matriz de Confusión, Precision, Recall, F1-Score

---

### 📓 Notebook 3 — Árbol de Clasificación (CB14)
**Archivo:** `notebooks/arbol_clasificacion_pokemon.ipynb`

**Objetivo:** Clasificar si un Pokémon es **legendario o no legendario** usando árbol de decisión.

| | |
|---|---|
| **Modelo** | `DecisionTreeClassifier` (scikit-learn) |
| **Variable objetivo (Y)** | `es_legendario` → 0 = No legendario / 1 = Legendario |
| **Variables predictoras (X)** | HP, Ataque, Defensa, Ataque Especial, Defensa Especial, Velocidad, Peso, Altura |
| **Dataset** | 1000 Pokémon desde PostgreSQL |
| **Tipo de tarea** | Clasificación Binaria (CB14) |

**Métricas calculadas:** Accuracy, Gini, AUC-ROC, Matriz de Confusión

---

### 🧠 Resumen de Modelos Implementados

| # | Notebook | Modelo | Tarea | Variable Objetivo | Tema |
|---|---|---|---|---|---|
| 1 | `arbol_decision_pokemon.ipynb` | DecisionTreeRegressor | Regresión | HP (valor numérico) | CB10 / CB11 |
| 2 | `regresion_logistica_pokemon.ipynb` | LogisticRegression | Clasificación Binaria | Legendario (0/1) | CB13 / CB14 |
| 3 | `arbol_clasificacion_pokemon.ipynb` | DecisionTreeClassifier | Clasificación Binaria | Legendario (0/1) | CB14 |

## 🌐 Enlaces

| Recurso | URL |
|---------|-----|
| Dashboard Streamlit | [Ver Dashboard](https://grupo-11-miner-a-de-datos-78gbzm6mf4szalkxonjqy8.streamlit.app/) |
| Repositorio GitHub | [Ver Repositorio](https://github.com/NicolasAlvarez25/Grupo-11-Miner-a-de-datos) |

---

---

## 🔐 Seguridad

- Variables de entorno en `.env` para credenciales (nunca se sube a GitHub)
- `.gitignore` configurado para excluir `.env`, `venv/`, `__pycache__/`, `*.log`

---

## 👥 Autores

| Nombres |
|---|
| Nicolas Gabriel Álvarez Aguirre |
| Yeison Andres Scarpeta Diaz |

**Institución:** CORHUILA — Corporación Universitaria del Huila  
**Programa:** Ingeniería de Sistemas  
**Materia:** Minería de Datos  
**Grupo:** 11  
**Año:** 2026
