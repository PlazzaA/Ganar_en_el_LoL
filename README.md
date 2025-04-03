# README - Análisis EDA de Partidas de League of Legends (LoL)  

## 📌 Descripción  
Proyecto de **Análisis Exploratorio de Datos (EDA)** enfocado en partidas de *League of Legends* para identificar factores determinantes en el resultado (victoria/derrota).  

**Objetivo principal**:  
🔍 Determinar si existe un conjunto de condiciones que predigan el resultado de una partida.  

**Hipótesis secundarias**:  
- Relación entre asesinatos y victorias.  
- Impacto del primer dragón/torre o cantidad de minions.  
- Campeones u objetos desbalanceados.  
- Influencia de la visión (wards) en el resultado.  

---

## 🗂 Estructura del repositorio  

EDA_LoL/
├── data/ # Datos brutos y procesados
│ ├── raw/ # Datos originales (sin procesar)
│ │ ├── champs.csv # Información de campeones (ID, nombre)
│ │ ├── matches.csv # Metadatos de partidas
│ │ ├── participants.csv # Relación jugador-partida-campeón
│ │ ├── stats1.csv # Stats equipo azul
│ │ ├── stats2.csv # Stats equipo rojo
│ │ ├── teambans.csv # Bans por equipo
│ │ └── teamstats.csv # Estadísticas globales por equipo
│ │
│ └── processed/ # Datos transformados
│ ├── clean_matches.parquet # Partidas limpias
│ ├── champion_stats.csv # Stats agregados por campeón
│ └── match_features.csv # Features para modelado
│
├── notebooks/ # Jupyter Notebooks
│ ├── 01_EDA_Initial.ipynb # Análisis exploratorio inicial
│ ├── 02_Feature_Engineering.ipynb # Creación de features
│ └── 03_Statistical_Analysis.ipynb # Pruebas de hipótesis
│
├── src/ # Código fuente Python
│ ├── data_processing.py # Funciones para limpieza de datos
│ ├── visualization.py # Helpers para gráficos
│ └── analysis.py # Funciones analíticas
│
├── reports/ # Resultados y reportes
│ ├── figures/ # Gráficos exportados
│ │ ├── winrate_by_champ.png
│ │ └── objectives_impact.png
│ └── insights_report.pdf # Reporte final en PDF
│
├── .gitignore # Archivos excluidos de Git
├── requirements.txt # Dependencias Python
├── README.md # Este archivo
└── LICENSE # Licencia MIT

1. **`data/`**
   - **`raw/`**: Datos originales sin modificar
     - Cada CSV corresponde a una tabla relacional
     - Preservar formato original para trazabilidad
   - **`processed/`**: 
     - Datos limpios y listos para análisis
     - Formatos optimizados (Parquet para grandes datasets)

2. **`notebooks/`**
   - Flujo de análisis secuencial:
     1. `01_EDA_Initial`: Limpieza y primeras visualizaciones
     2. `02_Feature_Engineering`: Creación de métricas clave
     3. `03_Statistical_Analysis`: Validación de hipótesis

3. **`src/`**
   - Código modularizado:
     - `data_processing.py`: Funciones para ETL
     ```python
     def clean_matches(df):
         """Elimina partidas inválidas y normaliza columnas"""
         return df.dropna().reset_index(drop=True)
     ```
     - `visualization.py`: Templates para gráficos recurrentes

4. **`reports/`**
   - Resultados exportados:
     - Figuras en alta resolución (PNG/SVG)
     - Reporte final con conclusiones clave

---

## ⚙️ Configuración  
1. **Clonar repositorio**:  
   ```bash  
   git clone https://github.com/tu-usuario/EDA_LoL.git  
   cd EDA_LoL

2. **Instalar dependencias**:
   ```bash
   pip install -r requirements.txt  # pandas, numpy, matplotlib, seaborn, requests

3. **Ejecutar**:
   ```bash
   jupyter notebook EDA_LoL.ipynb

## 🔍 Hallazgos Clave

### 🏆 Factores con Mayor Impacto en la Victoria

| Factor               | Impacto en Winrate | Correlación |
|----------------------|--------------------|-------------|
| Primer Dragón        | +15%               | 0.32        |
| Primera Torre        | +20%               | 0.41        |
| Wards colocados      | +65% winrate       | 0.58        |
| Oro por minuto       | +12%               | 0.27        |
| Asesinatos tempranos | +18%               | 0.35        |

## ⚖️ Desbalance en Campeones

Top 5 Campeones con Mayor Winrate:

|Campeón |	Winrate|	Pick Rate |	KDA|
|--------|--------|-----------|----|
|Jax     |	58.2%  |	12.3%	    |3.2 |
|Fiora   |	56.8%  |	8.7% 	    |2.9 |
|Warwick |	55.4%  |	15.1%	    |3.5 |
|Draven  |	54.9%  |	9.2% 	    |3.1 |
|Malzahar|	45.1%  |	6.5% 	    |2.4 |

**Visualización**:
```python
plt.figure(figsize=(10,6))
sns.barplot(x='factor', y='winrate', data=impacto_df)
plt.title('Impacto de Factores en Winrate')
plt.xticks(rotation=45)
plt.show()
