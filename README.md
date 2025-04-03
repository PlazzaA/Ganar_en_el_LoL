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

---

## 🗂 Estructura del repositorio  

> Como_ganar_en_lol/
>> data/ (Todos los dataframe reducidos)
>>>  *DataFrames.csv

>> graphs/ (Todos los gráficos obtenidos)
>>> *gráficos.png

>> EDA_LoL.ipynb (Memoria del EDA, incluyendo además la fuente de los dataframe para poder descargarlos sin reducir)                        
>> README.md (Este markdown que esta leyendo)

---

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

