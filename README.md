# Análisis de la abstención electoral en municipios españoles

Proyecto final de la asignatura **Minería de Datos y Modelización Predictiva** del Máster en Big Data, Data Science & Inteligencia Artificial (UCM).

## Objetivo

El proyecto analiza los factores demográficos, económicos y territoriales asociados a la abstención electoral en municipios españoles mediante técnicas de modelización predictiva.

Se desarrollan dos modelos:

- **Regresión lineal** para predecir el porcentaje de abstención (`AbstentionPtge`)
- **Regresión logística** para clasificar municipios con abstención elevada (`AbstencionAlta`)

---

# Estructura del proyecto

```text
.
├── DatosEleccionesEspaña.xlsx
├── EjercicioEvaluación.pdf
├── GuíaElaboraciónTarea.pdf
├── FuncionesMineria.py
├── Tarea_Final.ipynb
├── Tarea_Final_Memoria_Eloy.pdf
├── librerias.txt
└── .gitignore
```

---

# Dataset

El dataset contiene información de **8.117 municipios españoles** con variables de:

- Demografía
- Mercado laboral
- Actividad económica
- Territorio y densidad
- Indicadores electorales

Variables objetivo:

| Variable | Descripción |
|---|---|
| `AbstentionPtge` | Porcentaje de abstención |
| `AbstencionAlta` | 1 si abstención > 30%, 0 en caso contrario |

---

# Preprocesamiento

## Corrección de errores

- Conversión de variables categóricas
- Sustitución de códigos artificiales de missing (`999`, `99999`)
- Corrección de porcentajes fuera de rango
- Reagrupación de categorías poco representadas
- Tratamiento de categorías desconocidas

## Outliers

Detección mediante:

- Desviación típica
- Rango intercuartílico (IQR)

Los valores atípicos se transformaron a missing para su posterior imputación.

## Missing values

- Análisis del patrón de missings
- Creación de variable `prop_missings`
- Imputación aleatoria de variables numéricas y categóricas

---

# Modelos desarrollados

## Regresión lineal

Predicción de:

```python
AbstentionPtge
```

### Métodos de selección

- Forward
- Backward
- Stepwise

Con criterios:

- AIC
- BIC

### Mejor modelo

Forward / Stepwise BIC

### Resultados

| Métrica | Valor |
|---|---|
| R² train | 0.425 |
| R² test | 0.412 |
| Nº parámetros | 61 |

---

## Regresión logística

Clasificación de:

```python
AbstencionAlta
```

### Métricas utilizadas

- Pseudo-R² de McFadden
- AUC ROC
- Accuracy
- Sensitivity
- Specificity

### Mejor modelo

Forward AIC / BIC

### Resultados

| Métrica | Valor |
|---|---|
| pR² test | 0.276 |
| AUC test | 0.835 |
| Accuracy | 0.779 |
| Sensitivity | 0.709 |

Punto de corte óptimo:

```python
0.30
```

---

# Principales conclusiones

- La provincia (`CodigoProvincia`) es el predictor más relevante de la abstención.
- El arraigo territorial (`SameComAutonPtge`) se asocia con mayor participación electoral.
- La estructura económica municipal aporta capacidad explicativa adicional.
- Ambos modelos presentan buena generalización y bajo sobreajuste.

---

# Tecnologías utilizadas

- Python
- pandas
- numpy
- scikit-learn
- statsmodels
- matplotlib
- seaborn

---

# Ejecución

## Instalar dependencias

```bash
pip install -r librerias.txt
```

## Ejecutar notebook

```bash
jupyter notebook Tarea_Final.ipynb
```

---

# Autor

**Eloy Celaya López**

Máster en Big Data, Data Science & Inteligencia Artificial  
Universidad Complutense de Madrid
