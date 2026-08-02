# Modelos para estimación del valor de glucosa intersticial a partir de variables biométricas en deportistas

## Trabajo Fin de Grado - Grado en Matemáticas - Universidad Complutense de Madrid

## 👤 Tutores Académicos

* **Begoña Vitoriano Villanueva** (Departamento de Estadística e Investigación Operativa).
* **José Ignacio Hidalgo Pérez** (Facultad de Informática).

## 📋 Descripción del Proyecto

Se ha demostrado una clara influencia entre los niveles de glucosa en sangre y la actividad física, especialmente en personas con diabetes. 
En la actualidad no existen muchos estudios que expliquen si existe relación entre variables fisiológicas derivadas del deporte como el ritmo cardiaco, los pasos, impactos y desplazamientos y la glucosa intersticial, lo que constituye la motivación principal de este proyecto. 
En este estudio se investigará la aplicación de técnicas de estadística, optimización e inteligencia artificial para obtener modelos de la relación entre variables biométricas y la glucosa intersticial en deportistas. 

Este repositorio implementa el flujo de trabajo completo para el procesamiento, análisis y modelización de los conjuntos de datos experimentales y del dataset CGMacros. El objetivo principal es desarrollar de forma documentada y reproducible cada fase del pipeline, desde la ingesta de datos crudos hasta la generación de modelos predictivos y artefactos analíticos.

El trabajo combina dos líneas de fuentes de datos:

1. **Datos experimentales recogidos con sensores**
   - Proceden de personas monitorizadas con dispositivos de actividad y glucosa.
   - El flujo de trabajo sigue las fases:
     - `Data/Raw`: datos originales.
     - `Data/Staging`: datos tratados y unificados.
     - `Data/Trusted`: datos validados y listos para consumo externo.

2. **Datos públicos del dataset CGMacros**
   - Dataset disponible en **PhysioNet** para descargar en `Data/CGMacros/`.
   - No se incluyen los archivos en el repositorio por su tamaño.
   - Deben descargarse desde la fuente original y colocarse en la ruta esperada por los notebooks para reproducir los análisis.

El núcleo del proyecto en cuanto a modelización es el Jupyter Notebook `CGMacros.ipynb`. Este archivo centraliza para los datos de CGMacros las tareas de:
*   **Carga y Preprocesado:** Limpieza, unificación temporal y estructuración de los datos de entrada.
*   **Análisis Exploratorio de Datos (EDA):** Identificación de patrones, distribuciones y visualizaciones clave.
*   **Modelización:** Entrenamiento, optimización de hiperparámetros, evaluación y exportación de modelos.
*   **Resultados:** Generación de métricas de rendimiento, curvas de evaluación y gráficos predictivos.

---

## 📂 Estructura del repositorio

```text
├── Data/                   # Carpeta para el almacenamiento de datos (sólo experimentales)
│   ├── Raw/                # Datos reales originales
│   ├── Staging/            # Datos intermedios preprocesados
│   └── Trusted/            # Datos finales validados y aptos para el uso
├── Analysis/               # Resultados de análisis previos a la modelización
│   ├── CGMacros/           # Resultados de análisis del dataset CGMacros
│   ├── ...         
│   ├── ...                 # Resultados de análisis de datos experimentales
│   └── ...         
├── Modeling/               # Gráficas de modelado, Clarke y SHAP
├── TFG.pdf                 # Memoria final del TFG a LaTeX en PDF
├── TFG.pptx                # Presentación de la defensa (modo sólo visualización)
├── Data Processing.ipynb   # Procesado inicial de datos crudos experimentales
├── Data Analysis.ipynb     # Análisis de datos trusted experimentales
├── CGMacros.ipynb          # Preprocesado, análisis y modelado de CGMacros
└── requirements.txt        # Lista de dependencias del proyecto
```

## Archivos principales

### `TFG.pdf`
Memoria completa del trabajo elaborada en LaTeX.  
No incluye la declaración de uso responsable de IA para no hacer públicos datos personales.

### `TFG.pptx`
Presentación de diapositivas utilizada para la defensa del proyecto.  
Está configurada en modo visualización para evitar su edición externa.

### `Data Processing.ipynb`
Notebook de procesado inicial de los datos crudos experimentales.

### `Data Analysis.ipynb`
Notebook de análisis de los datos experimentales ya tratados en `Data/Trusted`.  
Los resultados generados se guardan en `Analysis/`.

### `CGMacros.ipynb`
Notebook principal para el trabajo con el dataset CGMacros.  
Incluye preprocesado, análisis exploratorio, modelado, evaluación, y generación de resultados.

Sus salidas se almacenan en:
- `Analysis/CGMacros/`
- `Modeling/`

## Carpetas de resultados

### `Analysis/`
Contiene los resultados de las pruebas y análisis sobre los datos experimentales y de CGMacros.  
Incluye subcarpetas organizadas por tipo de análisis y una carpeta específica para `CGMacros` con la misma subdivisión.

### `Modeling/`
Incluye las salidas gráficas y de evaluación de los modelos sobre CGMacros, entre ellas:
- gráficas de predicción,
- evaluación de Clarke,
- interpretabilidad con SHAP.

---

## 🛠️ Requisitos e Instalación

El archivo `requirements.txt` incluye todas las dependencias necesarias. Instale todas las dependencias ejecutando:
```bash
pip install -r requirements.txt
```

### Entorno de Ejecución
*   **Python:** Versión 3.8 o superior.

### Librerías Principales Requeridas
*   **Manipulación de datos:** `pandas`, `numpy`
*   **Visualización:** `matplotlib`, `seaborn`
*   **Cálculo y Modelos:** `scipy`, `statsmodels`, `numba`, `scikit-learn`, `xgboost`
*   **Optimización e Interpretabilidad:** `optuna`, `shap`
*   **Persistencia:** `pickle`

---

## 🚀 Uso y orden cronológico del desarrollo del código

1. Primero se preprocesaron los datos experimentales en `Data Processing.ipynb` para prepararlos para el análisis.
2. Después con `Data Analysis.ipynb` se analizaron los datos obtenidos en la recogida experimental. Tras el análisis se descubrieron las limitaciones de los datos experimentales, por lo que se consideró el uso del dataset público CGMacros.
3. Para CGMacros, se desarrolló `CGMacros.ipynb`, buscando adaptar lo previamente desarrollado a los nuevos datos, y que contiene todo el flujo de preprocesado, análisis, modelado, y exportación de resultados. Se recomienda seguir estrictamente el orden de las secciones para garantizar la correcta persistencia de las variables en memoria:
    1.  *Imports y Constantes:* Carga de librerías y definición de rutas del sistema.
    2.  *Carga y Preprocesado:* Transformación y limpieza de los datos base.
    3.  *Análisis Exploratorio:* Generación de gráficos y estadísticas iniciales.
    4.  *Modelización y Evaluación:* Pipeline de entrenamiento y exportación de artefactos.

---

## 📝 Notas de desarrollo, buenas prácticas y observaciones

* **Documentación del código:** Las funciones clave incluyen un formato estructurado con descripción, argumentos (`Args`), retornos (`Returns`), ejemplos prácticos y recomendaciones de uso.
* **Los resultados generados** por los notebooks, la documentación y los artefactos del TFG se almacenan en carpetas específicas dentro del propio repositorio actual (existentes o creadas en el momento de la ejecución) para facilitar su reproducibilidad y trazabilidad.
* **⚠️PRECAUCIÓN⚠️:** Las direcciones que aparecen en los notebooks son las direcciones completas utilizadas en local para el desarrollo. Si se quiere aplicar en otros dispositivos es necesario recortar dichas direcciones para mantener sólo las direcciones relativas que apuntan dentro de este mismo repositorio (sólo es encesario eliminar la raíz común).

---

## 📦 Artefactos Generados

Al completar la ejecución del pipeline, el sistema exportará de forma automática:
*   Modelos serializados en formato `.pkl` listos para entornos de producción.
*   Gráficos estáticos e interactivos sobre las predicciones y tendencias del dataset.
*   Tablas de rendimiento estructuradas para su posterior integración o consulta.

El entorno genera y organiza automáticamente sus salidas en los siguientes subdirectorios dentro de `MODELIZACION_DIR`:
*   `PREDICCIONES_DIR`: Almacenamiento de gráficos de predicción visuales.
*   `METRICAS_PKL_DIR`: Almacenamiento de archivos serializados con métricas cuantitativas.
*   `CURVAS_PKL_DIR`: Curvas de rendimiento y evaluación del modelo (ej. ROC, Precision-Recall).
*   `MODELOS_PKL_DIR`: Modelos entrenados y serializados listos para inferencia.
*   `MATRICES_PKL_DIR`: Matrices de confusión y datos estructurados de evaluación.