# 📊 Proyecto 11 — Pipeline ETL Pokémon + Dashboard + Modelo de Regresión

**Grupo 11 — Minería de Datos**  
**Estudiante:** Yeison Scarpeta  
**Tecnologías:** Python · Streamlit · PostgreSQL · Supabase · SQLAlchemy · Plotly · Scikit-learn · Jupyter Notebook · GitHub · WSL/Linux

---

## 🎯 Objetivo del Proyecto

Desarrollar un **pipeline ETL completo** que permita:

- Extraer datos reales desde la [PokeAPI](https://pokeapi.co/)
- Transformar y limpiar los datos
- Cargar los datos en una base de datos en la nube (Supabase)
- Visualizar los datos mediante un dashboard interactivo (Streamlit)
- Aplicar un modelo de **aprendizaje supervisado (Regresión Lineal)** para predecir el HP de los Pokémon

---

## 🧱 Arquitectura del Sistema
PokeAPI ──► extractor.py ──► transformer.py ──► Supabase (PostgreSQL)
│
Streamlit Cloud
│
Dashboard Interactivo

| Capa | Servicio | Función |
|------|----------|---------|
| Control de versiones | GitHub | Almacenamiento del código y despliegue automático |
| Frontend / App | Streamlit Cloud | Ejecutar el dashboard con URL pública |
| Base de datos | Supabase (PostgreSQL) | Almacenamiento de datos procesados con SSL |

---

## 🔄 Pipeline ETL

### 1. Extracción (`extractor.py`)

Consumo de la **PokeAPI** (API REST pública). Se extrajeron **1000 Pokémon** con las siguientes variables:

- HP, ataque, defensa, velocidad
- Altura, peso, experiencia base
- Tipo, habilidades, sprites

### 2. Transformación

- Limpieza de valores nulos
- Normalización de columnas
- Conversión de tipos de datos
- Cálculo de estadísticas derivadas

### 3. Carga (`SQLAlchemy` → Supabase)

- Inserción masiva (*bulk insert*)
- Conexión segura con SSL (`sslmode=require`)
- Tiempo aproximado de carga: **~5 segundos**

---

## 🗄️ Base de Datos

### Tabla `pokemon`

| Campo | Descripción |
|-------|-------------|
| `id` | Identificador único |
| `nombre` | Nombre del Pokémon |
| `hp`, `ataque`, `defensa`, `velocidad` | Estadísticas de combate |
| `altura`, `peso` | Datos físicos |
| `tipo`, `habilidades` | Clasificación |
| `es_legendario`, `es_mitico` | Flags especiales |
| `sprite_frente` | URL de imagen |
| `fecha_extraccion` | Timestamp de carga |

> Total: **1000 registros · ~25 columnas**

### Tabla `metricas_etl`

Registra información de cada ejecución del pipeline: registros extraídos, guardados, fallidos y tiempo de ejecución.

---

## 📊 Dashboard Interactivo (Streamlit)

Construido con **Streamlit + Plotly**. Cuenta con 6 secciones:

| Sección | Contenido |
|---------|-----------|
| 📈 Estadísticas | Top 10 por ataque/velocidad, dispersión ataque vs defensa |
| 🔷 Tipos | Distribución de tipos, barras, torta, radar por tipo |
| ⚖️ Comparador | Compara dos Pokémon con gráfico radar dual |
| ⭐ Especiales | Lista de legendarios y míticos con sprites |
| 📖 Pokédex Visual | Galería de 1000 Pokémon con buscador y filtros |
| 📥 Datos y Exportar | Tabla interactiva con exportación a CSV |

---

## 🤖 Modelo de Machine Learning — Regresión Lineal

**Variable objetivo:** HP (vida del Pokémon)  
**Variables predictoras:** ataque, defensa, velocidad

```python
from sklearn.linear_model import LinearRegression
from sklearn.model_selection import train_test_split

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)
model = LinearRegression()
model.fit(X_train, y_train)
```

**Métricas de evaluación:**

| Métrica | Descripción |
|---------|-------------|
| MSE | Error cuadrático medio |
| MAE | Error absoluto medio |
| R² | Coeficiente de determinación |

Se generó una gráfica **HP real vs HP predicho** para visualizar la calidad del modelo.

> Archivo: `notebooks/analisis_pokemon_regresion.ipynb`  
> Entorno: Linux / WSL con Jupyter Notebook

---

## 🔐 Seguridad

- Variables de entorno para credenciales
- Conexión cifrada con `sslmode=require`
- Secrets configurados en Streamlit Cloud

---

## 🚀 Despliegue

El sistema está desplegado completamente en la nube:

- **GitHub** → control de versiones
- **Streamlit Cloud** → ejecución del dashboard
- **Supabase** → base de datos PostgreSQL

---

## 🌐 Enlaces

| Recurso | URL |
|---------|-----|
| Dashboard Streamlit | *(https://grupo-11-miner-a-de-datos-78gbzm6mf4szalkxonjqy8.streamlit.app/* |

---

## 👨‍💻 Autor

**Yeison Scarpeta**
**Nicolas Alvarez** 
Grupo 11 — Minería de Datos · 2026
