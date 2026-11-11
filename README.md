# Taller 2 · Predicción de abandono de clientes

MINE-4101 Ciencia de Datos Aplicada · Universidad de los Andes · 2026-20

Sergio Perez (202314506) · Samuel Charry (202313509)

Modelo que predice qué clientes de un banco van a abandonar, para enfocar la campaña de retención de FinAlpes y estimar cuánto valor le deja al banco. El proceso sigue las [Prácticas de Machine Learning](https://datascience-uniandes.github.io/PracticasMachineLearning/) del curso.

## Archivos

| Archivo | Contenido |
|---|---|
| `Taller2_CDA (2).ipynb` | Notebook principal: puntos 1 a 5 y 7 del taller. |
| `Taller2_Modelos.ipynb` | Actividades 3, 4 y 5 de la Práctica 2: ocho modelos entrenados y comparados para elegir los dos que se documentan en el notebook principal. |
| `Documento_ejecutivo_Taller2.pdf` | Informe ejecutivo (punto 6). |
| `churn.csv` | Dataset original: 10.045 clientes y 11 columnas, con duplicados, nulos, valores inválidos y categorías mal escritas. |
| `churn_train.csv`, `churn_val.csv`, `churn_test.csv` | Conjuntos de entrenamiento (6.000), validación (2.000) y prueba (2.000) ya limpios, generados en la sección 2.1 del notebook principal. |

## Dónde está cada punto del taller

| Punto | Ubicación |
|---|---|
| 1. Entendimiento y preparación de los datos | Notebook principal, sección 1 |
| 2. Entrenamiento del modelo | Notebook principal, sección 2, y `Taller2_Modelos.ipynb` |
| 3. Análisis cuantitativo | Notebook principal, sección 3 |
| 4. Análisis cualitativo | Notebook principal, sección 4 |
| 5. Generación de valor | Notebook principal, sección 5 |
| 6. Insights e informe ejecutivo | `Documento_ejecutivo_Taller2.pdf` |
| 7. Declaración de uso de IA generativa | Notebook principal, sección 7 |

## Cómo ejecutar

1. Instalar las dependencias (Python 3.11 o 3.12):

   ```bash
   pip install jupyter pandas numpy matplotlib seaborn scipy scikit-learn statsmodels lime shap tensorflow
   ```

2. Abrir los notebooks desde esta carpeta, porque leen los CSV con rutas relativas.
3. Ejecutar en orden, con Restart & Run All:
   1. `Taller2_CDA (2).ipynb`: lee `churn.csv` y en la sección 2.1 vuelve a generar los tres conjuntos.
   2. `Taller2_Modelos.ipynb`: lee `churn_train.csv`, `churn_val.csv` y `churn_test.csv`. Como los conjuntos ya vienen en la carpeta, también se puede ejecutar por separado.

Los resultados de Random Forest pueden cambiar levemente con otra versión de scikit-learn. Las salidas guardadas en los notebooks son las que se citan en el análisis y en el informe.

## Resultados principales

- El abandono depende sobre todo de la edad (el riesgo sube entre los 40 y los 50 años), del número de productos, de si el cliente es activo y de si es de Alemania.
- Se eligió Random Forest. En prueba detecta 7 de cada 10 clientes que abandonan (recall 0,705) con F1 de 0,598, frente a 0,568 de la regresión logística. La diferencia es significativa (bootstrapping pareado, p = 0,014).
- Con umbral 0,6, para un banco de 20.000 clientes con 15 % de abandono anual, el modelo deja unos 20 millones de pesos al mes. La inversión de 160,4 millones se recupera en 8 meses, con un ROI a 12 meses de 49 %.
- El resultado depende sobre todo del éxito real de la campaña: con 15 % de éxito en vez del 30 % supuesto, la inversión tardaría casi 4 años en recuperarse.
