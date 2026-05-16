# ⚽ Minería de Datos — English Premier League (2000–2025)
 
![Python](https://img.shields.io/badge/Python-3.10+-blue?logo=python&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange?logo=jupyter&logoColor=white)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.x-F7931E?logo=scikit-learn&logoColor=white)
![Status](https://img.shields.io/badge/Estado-Completado-brightgreen)
 
Proyecto de minería de datos sobre **9,380 partidos de la Premier League inglesa** entre las temporadas 2000/01 y 2024/25. Se aplican técnicas de análisis exploratorio, clasificación y regresión para predecir resultados y goles.
 
---
 
## 📁 Contenido del repositorio
 
```
📦 mineria-datos-epl
 ├── 📓 epl_mineria_datos_KNN_Arbol.ipynb   ← Notebook principal
 ├── 📊 epl_final.csv                        ← Dataset (9,380 registros)
 └── 📄 README.md
```
 
---
 
## 🎯 Objetivos
 
- Explorar y visualizar los patrones estadísticos de la EPL en 25 temporadas
- Predecir el **resultado del partido** (Local gana / Empate / Visitante gana)
- Estimar el **total de goles** por partido
- Comparar el rendimiento de múltiples algoritmos de ML
---
 
## 📊 Dataset
 
| Característica | Detalle |
|---|---|
| **Fuente** | Kaggle / Estadísticas oficiales EPL |
| **Registros** | 9,380 partidos |
| **Variables originales** | 22 |
| **Variables derivadas** | 6 (TotalGoals, GoalDiff, ShotAccuracy, TotalCards…) |
| **Período** | Temporadas 2000/01 → 2024/25 |
| **Equipos únicos** | 49 |
 
---
 
## 🔬 Metodología
 
### 1. Comprensión y Limpieza de Datos
- Dataset sin valores nulos ni duplicados
- Conversión de fechas y creación de variables derivadas
- Codificación del resultado para análisis de correlación
### 2. Análisis Exploratorio (EDA)
- Distribución de resultados: 46% local · 25% empate · 29% visitante
- Histogramas, boxplots y scatterplots por resultado
- Matriz de correlación de Pearson
- Tendencias históricas de goles y ventaja de localía
### 3. Modelos implementados
 
| Modelo | Problema | Accuracy | F1 (weighted) |
|---|---|---|---|
| Regresión Logística | Binario (gana local / no gana) | ~77% | ~74% |
| KNN (k=26) | Multiclase (H / D / A) | 62.3% | 59.5% |
| Árbol de Decisión | Multiclase (H / D / A) | 63.1% | 61.3% |
| Random Forest | Multiclase (H / D / A) | 61.6% | 61.9% |
| Regresión Lineal | Regresión (goles totales) | R²=0.51 | MAE=0.93 |
 
### 4. Reducción de Dimensionalidad
- PCA aplicado a KNN, Random Forest y Regresión Lineal
- 11 componentes retienen el 95% de la varianza
- Resultado: sin mejora de rendimiento → las 14 variables originales son todas relevantes
---
 
## 💡 Hallazgos principales
 
1. **El marcador al descanso es el predictor más poderoso** — `HalfTimeHomeGoals` y `HalfTimeAwayGoals` dominan en todos los modelos
2. **Los empates son estadísticamente difíciles de predecir** — sus métricas se solapan con victorias ajustadas
3. **El escalado es crítico para KNN** — sin `StandardScaler`, el modelo ignora variables de escala pequeña
4. **La ventaja de localía disminuyó en 2020/21** — temporada sin público por COVID-19
5. **El promedio de goles se mantiene estable** — ~2.7 goles/partido durante 25 años
6. **PCA no aportó ventaja** — con 14 variables bien seleccionadas, la reducción no mejora el rendimiento
---
 
## 🛠️ Tecnologías utilizadas
 
```python
pandas · numpy · matplotlib · seaborn · scipy
scikit-learn (LogisticRegression, KNeighborsClassifier,
              DecisionTreeClassifier, RandomForestClassifier,
              LinearRegression, PCA, StandardScaler)
```
 
---
 
## 🚀 Cómo ejecutar el notebook
 
1. Clona el repositorio:
```bash
git clone https://github.com/TU_USUARIO/mineria-datos-epl.git
cd mineria-datos-epl
```
 
2. Instala las dependencias:
```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy
```
 
3. Abre el notebook:
```bash
jupyter notebook epl_mineria_datos_KNN_Arbol.ipynb
```
 
> Si usas **Google Colab**, sube el CSV a tu Google Drive en la ruta `MyDrive/Mineria_Datos/epl_final.csv` antes de ejecutar.
 
---
 
## 📌 Estructura del notebook
 
```
01 · Instalación e importación de librerías
02 · Comprensión de los datos
03 · Limpieza y preparación
04 · EDA — Análisis Exploratorio
05 · Regresión Logística (binario)
06 · KNN — sin escalado vs con escalado
07 · Selección del k óptimo
08 · KNN final (k=26)
09 · Árbol de Decisión
10 · Comparación KNN vs Árbol
11 · Regresión Lineal (goles totales)
12 · Random Forest
13 · PCA + comparación final de todos los modelos
14 · Conclusiones
```
 
---
 
*Proyecto desarrollado para la clase de Minería de Datos*
