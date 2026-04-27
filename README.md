# 🚌 Bizkaibus EDA – Análisis Exploratorio de Datos

## 📌 Descripción del proyecto

Este proyecto consiste en un **Análisis Exploratorio de Datos (EDA)** sobre el uso del servicio de transporte público Bizkaibus en Bizkaia.

El objetivo principal es analizar el comportamiento de la demanda en función de:

* Número de viajeros
* Tipo de título de transporte
* Número de expediciones (viajes)
* Evolución temporal

A través de este análisis se buscan **patrones, relaciones entre variables y validación de hipótesis** que permitan entender mejor el uso del servicio.

---

## 📊 Fuente de datos

Los datos han sido obtenidos del portal oficial de Open Data Bizkaia:

* https://www.opendatabizkaia.eus/es/catalogo/bizkaibus

Incluyen información estructurada en formato CSV sobre:

* Viajeros por línea
* Tipos de billetes
* Número de viajes
* Distribución mensual

---

## 🎟️ Tipos de billete

El sistema Bizkaibus utiliza distintos títulos de transporte, principalmente gestionados mediante la tarjeta Barik:

* Billete ocasional
* Barik anónima
* Barik personalizada
* Tarifas especiales (jóvenes, mayores, etc.)

Este análisis permite identificar el peso de cada tipo en el uso total del sistema.

---

## 🛣️ Estructura de las líneas

Las líneas de Bizkaibus se organizan en:

* Líneas troncales (conexiones principales)
* Líneas comarcales (conexión entre municipios)
* Líneas especiales (nocturnas, lanzaderas)

Cada línea tiene una frecuencia distinta, lo que impacta directamente en la demanda.

---

## 🎯 Objetivos del EDA

* Analizar la distribución de viajeros por línea
* Estudiar el uso de los distintos tipos de billete
* Evaluar la relación entre número de viajes y demanda
* Detectar patrones temporales (estacionalidad)
* Validar hipótesis sobre el comportamiento de los usuarios

---

## 🧪 Metodología

El análisis se ha realizado en Python utilizando Jupyter Notebook.

### 1. Carga de datos

Se importan los datasets en formato CSV utilizando `pandas`:

```python
import pandas as pd

df = pd.read_csv("datos.csv")
```

---

### 2. Exploración inicial

* `df.head()`
* `df.info()`
* `df.describe()`

Objetivo: entender la estructura, tipos de datos y posibles problemas.

---

### 3. Limpieza de datos

* Tratamiento de valores nulos
* Conversión de tipos (`astype`, fechas, etc.)
* Normalización de columnas
* Filtrado de datos inconsistentes

```python
df = df.dropna()
df['viajeros'] = df['viajeros'].astype(int)
```

---

### 4. Transformación de datos

Se aplican operaciones de agregación y agrupación:

```python
df_linea = df.groupby('linea')['viajeros'].sum()
df_mes = df.groupby('mes')['viajeros'].sum()
```

También se combinan datasets cuando es necesario (`merge`).

---

### 5. Análisis estadístico

Se calculan métricas descriptivas:

* Media
* Mediana
* Desviación estándar
* Valores extremos

```python
df['viajeros'].mean()
df['viajeros'].std()
```

---

### 6. Visualización

Se utilizan `matplotlib` y `seaborn` para representar:

* Distribución por línea
* Evolución temporal
* Uso por tipo de billete
* Correlaciones

```python
import matplotlib.pyplot as plt

df_linea.sort_values().plot(kind='bar')
plt.show()
```

---

### 7. Análisis de correlaciones

Se estudian relaciones entre variables clave:

```python
df.corr()
```

Especialmente:

* Viajeros vs número de viajes
* Tipo de billete vs volumen total

---

## 🔍 Hipótesis planteadas

1. Los títulos para jovenes representan un 15% del total
2. Las líneas que unen Bilbao están más saturadas
3. Existe estacionalidad en el uso del autobús
4. El subsidio del 50% aplicado en 2022 favoreció el uso del transporte público

---

## ✅ Resultados

* X No supera el umbral del 15%
* ✔ Existe ralación entre la saturación y que la línea conecte con Bilbao
* ✔ Existencia de patrones estacionales
* ✔ El subsidio  favoreció el uso del autobús

---

## 📈 Conclusiones

El análisis muestra que Bizkaibus presenta:

* Un uso intensivo en líneas clave
* Dependencia directa de la oferta (frecuencia de viajes)
* Preferencia clara por sistemas de pago digital (Barik)
* Variaciones temporales relevantes

Este tipo de análisis es útil para:

* Optimización del servicio
* Planificación de rutas
* Toma de decisiones basada en datos

---

## 🚀 Posibles mejoras

* Incluir datos meteorológicos
* Analizar eventos especiales (fiestas, huelgas, etc.)
* Aplicar modelos predictivos (Machine Learning)
* Estudio de segmentación de usuarios

---

## 🛠️ Tecnologías utilizadas

* Python
* pandas
* numpy
* matplotlib
* seaborn
* Jupyter Notebook

---

## 👤 Autor

Proyecto desarrollado por **Rubén Novoa**.

---

## 📎 Estructura del repositorio

```
📁 bizkaibus-eda
 ├── 📄 EDA_biz_final.ipynb
 ├── 📄 README.md
 ├── 📁 data/
 └── 📁 images/ (opcional)
```

---

## ⭐ Notas finales

Este proyecto forma parte de un portfolio de Data Analysis orientado a demostrar habilidades en:

* Limpieza de datos
* Análisis exploratorio
* Visualización
* Interpretación de resultados
