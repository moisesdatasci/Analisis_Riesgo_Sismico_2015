# 🚀 Análisis de Riesgo Sísmico en Chile (2003-2015)

**Un proyecto de Ciencia de Datos para la Planificación Urbana y la Construcción**
<p align="center">
<img alt="Mapa1" src="https://github.com/user-attachments/assets/ebffde92-b39c-44d2-b5d4-6d42bd79257d" width="246" height="603"/>
<img alt="mapa 2" src="https://github.com/user-attachments/assets/201a25a7-07d7-463b-a0ad-910e24541adb" width="246" height="603"/>
<img alt="Mapa3" src="https://github.com/user-attachments/assets/a9b19b2b-d58d-407f-acb2-52740261e90e" width="246" height="603"/>
</p>

*(Ej: "mapa_sismicidad_chile_v3.png")*

---

## 1. Resumen del Proyecto

Este proyecto realiza un análisis de punta a punta (End-to-End) de la actividad sísmica en Chile utilizando un conjunto de datos actualizado que abarca desde **2003 hasta 2024**, obtenido del **Centro Sismológico Nacional (CSN)**.

El objetivo principal es traducir los datos sísmicos en bruto en inteligencia accionable para un *stakeholder* del sector de la construcción, respondiendo a la pregunta: **"¿Cuáles son las zonas de mayor y menor riesgo sísmico en Chile para la planificación urbana?"**

El entregable clave es un **mapa interactivo multicapa** que visualiza tanto la **frecuencia** (densidad de sismos) como la **severidad** (eventos de alta magnitud), superpuesto con las divisiones regionales del país.

---

## 2. El Problema: Un Contexto de Negocio

Para una empresa constructora que planea expandir sus operaciones en Chile, no basta con saber que "Chile es un país sísmico". Se necesita una **evaluación de riesgo granular** para:

* **Optimizar la asignación de recursos:** ¿Dónde se debe invertir más en ingeniería antisísmica?
* **Evaluar la viabilidad de proyectos:** ¿Existen zonas con un riesgo prohibitivo por frecuencia o por severidad?
* **Planificación Estratégica:** Identificar oportunidades en zonas de riesgo *relativamente* menor.

Este proyecto aborda esa necesidad generando un análisis que diferencia el riesgo sísmico del país.

---

## 3. Stack Tecnológico 🛠️

Este análisis fue realizado enteramente en **Python**. Las principales librerías utilizadas fueron:

* **Análisis y Manipulación de Datos:** `Pandas` y `Numpy`
* **Limpieza de Texto (Regex):** `re`
* **Visualización Estática (EDA):** `Matplotlib` y `Seaborn`
* **Visualización Geoespacial Interactiva:** `Folium`
* **Manejo de Datos Geográficos:** `GeoJSON`

---

## 4. Metodología y Flujo de Trabajo

El proyecto siguió un ciclo de vida estructurado de Ciencia de Datos:

### Paso 1: Definición del Problema y Adquisición de Datos
* **Objetivo:** Identificar zonas de riesgo para una constructora.
* **Fuente:** Catálogo sísmico del Centro Sismológico Nacional (CSN) de la Universidad de Chile.
* **Datos:** [XX.XXX] eventos sísmicos (2003-2024).

### Paso 2: Limpieza y Preprocesamiento de Datos (Data Wrangling)
* Renombrado de columnas para claridad.
* Conversión de tipos de datos (de `object` a `datetime` y `float`).
* **Cirugía de Texto (Regex):** Extracción de la magnitud numérica (ej. `3.1 Ml`) desde una columna de texto contaminada.
* Manejo de valores nulos (NaN).
* **Filtrado Geográfico:** Aislamiento de eventos dentro de los límites continentales de Chile.

### Paso 3: Análisis Exploratorio de Datos (EDA)
Se investigaron las distribuciones y tendencias para entender el "carácter" de la sismicidad chilena.

* **Distribución de Magnitud:** La gran mayoría de los sismos son de baja magnitud (< 4.0), pero existe una "cola larga" de eventos de alta energía.
    *[Inserta aquí tu gráfico de Histograma de Magnitud]*
* **Frecuencia Temporal:** Se observó una línea base constante de sismicidad, interrumpida por picos masivos de réplicas post-terremoto (ej. 27F en 2010).
    *[Inserta aquí tu gráfico de Serie de Tiempo de Frecuencia]*

### Paso 4: Visualización Geoespacial Avanzada
Se consolidaron los hallazgos en un único mapa interactivo (`mapa_sismicidad_chile_v3.html`) con las siguientes capas controlables:

1.  **Capa Base:** `OpenStreetMap`.
2.  **Capa de Regiones:** Fronteras administrativas (GeoJSON) para dar contexto geográfico.
3.  **Capa de Frecuencia (Heatmap):** Un mapa de calor que muestra la *densidad* de sismos (M > 3.0), revelando dónde "tiembla más seguido".
4.  **Capa de Severidad (Marcadores):** Círculos (naranjas y rojos) que marcan la ubicación de sismos de alto riesgo (M > 5.5), mostrando dónde "tiembla más fuerte".

---

## 5. Hallazgos Clave y Conclusiones 💡

El análisis refuta la idea de que "todo Chile tiene el mismo riesgo". Identificamos dos perfiles de riesgo distintos:

1.  **Riesgo por ALTA FRECUENCIA (Norte Grande):**
    * **Regiones:** Arica y Parinacota, Tarapacá, Antofagasta.
    * **Observación:** El `Heatmap` es más intenso en esta zona.
    * **Implicancia:** Riesgo de **fatiga de material** y disrupción operativa debido a la sismicidad constante.

2.  **Riesgo por ALTA SEVERIDAD (Centro-Sur):**
    * **Regiones:** Valparaíso, Maule, Biobío.
    * **Observación:** Mayor concentración de círculos rojos (M > 6.5) y eventos históricos (M 8.8).
    * **Implicancia:** Riesgo de **colapso catastrófico**. El diseño estructural debe superar con creces la norma estándar.

---

## 6. Entregable: Mapa Interactivo

Puedes explorar el mapa interactivo final directamente en tu navegador (requiere un momento para cargar todas las capas y puntos de datos).

➡️ **[Haz clic aquí para ver el Mapa Interactivo]([Pega aquí el enlace de GitHub Pages])** ⬅️

*(Nota: Para que este enlace funcione, debes activar GitHub Pages en la configuración de tu repositorio)*

---

## 7. Cómo Usar este Repositorio

Para replicar este análisis, sigue estos pasos:

1.  **Clona el repositorio:**
    ```bash
    git clone [https://github.com/](https://github.com/)[TuUsuario]/[TuRepositorio].git
    cd [TuRepositorio]
    ```

2.  **Crea un entorno virtual e instala las dependencias:**
    ```bash
    python -m venv venv
    source venv/bin/activate  # En Windows: venv\Scripts\activate
    pip install -r requirements.txt
    ```

3.  **Ejecuta el Notebook o Script:**
    Abre y ejecuta el archivo `[Tu_Notebook.ipynb]` o `[tu_script.py]` para generar los análisis y el mapa `.html`.

4.  **Archivos Clave:**
    * `[Tu_Notebook.ipynb]`: Contiene todo el código de análisis y visualización.
    * `data/`: Carpeta con el set de datos en bruto del CSN.
    * `Regional.geojson`: Archivo de fronteras regionales.
    * `mapa_sismicidad_chile_v3.html`: El mapa interactivo final.

---

## 8. Limitaciones y Próximos Pasos

* **Calidad del Suelo:** Este análisis no incluye datos geotécnicos. El tipo de suelo puede amplificar drásticamente el impacto de un sismo. Un próximo paso sería cruzar este mapa con mapas de suelos.
* **Análisis Predictivo:** Este proyecto es un análisis descriptivo y diagnóstico. No intenta predecir terremotos.

---

## 9. Sobre Mí

¡Hola! Soy [Tu Nombre], un Científico de Datos Junior apasionado por transformar datos en soluciones de negocio.

* **LinkedIn:** [Tu Perfil de LinkedIn]
* **Portafolio:** [Tu Portafolio (si tienes uno)]
