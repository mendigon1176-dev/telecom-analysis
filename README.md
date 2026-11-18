# telecom-analysis
analisis de ConnectaTel
# Análisis Exploratorio y Segmentación de Clientes — ConnectaTel

## Objetivo del Proyecto
Realizar un análisis exploratorio de datos (EDA) sobre la base de clientes y registros de consumo de **ConnectaTel** para identificar patrones de comportamiento, limpiar inconsistencias en los datos, segmentar a los usuarios por edad y nivel de uso, y generar recomendaciones comerciales accionables para optimizar la oferta de planes.

---

## Datasets Utilizados
El análisis integra dos fuentes principales de información:
* **`users` (Perfil de usuarios):** Contiene los datos demográficos y contractuales de **4,000 clientes**, incluyendo su identificador único (`user_id`), edad (`age`), fecha de registro (`reg_date`) y tipo de plan contratado (`plan`: Básico o Premium).
* **`usage` (Registros de consumo):** Contiene el historial detallado de eventos de comunicación (`type`: llamadas `call` y mensajes `text`), junto con la duración en minutos de las llamadas (`duration`) y la longitud en caracteres de los mensajes (`length`).

---

##  Etapas del Análisis Realizadas
1. **Exploración inicial y diagnóstico:** Revisión de tipos de datos, estadísticas descriptivas y evaluación de valores faltantes (`NaN`).
2. **Limpieza y transformación de datos:**
   * Marcado de fechas futuras inválidas (> 2024) en `reg_date` como `NaT`.
   * Conservación justificada de valores nulos estructurales (MAR) en `duration` y `length` según el tipo de evento.
   * Agregación del consumo por usuario (`cant_mensajes`, `cant_llamadas`, `cant_minutos_llamada`) y cruce con la tabla de perfiles (`user_profile`).
3. **Análisis visual y detección de *outliers*:**
   * Visualización de distribuciones por plan mediante histogramas (`Seaborn`).
   * Identificación de valores extremos mediante *boxplots* y el método del Rango Intercuartílico (**IQR**), conservando los *outliers* superiores al representar usuarios reales de alto consumo (*heavy users*).
4. **Segmentación de clientes:** Clasificación de la base en grupos de uso (`Bajo uso`, `Uso medio`, `Alto uso`) y grupos etarios (`Joven`, `Adulto`, `Adulto Mayor`).
5. **Insight ejecutivo:** Síntesis de hallazgos y propuestas de *upselling*, nuevos paquetes de voz y estrategias de retención.

---

##  Cómo Ejecutar el Notebook
Puedes ejecutar este proyecto fácilmente en la nube sin instalar nada en tu computadora usando **Google Colab**:

1. Haz clic en el archivo del notebook (`.ipynb`) dentro de este repositorio o descárgalo.
2. Abre [Google Colab](https://google.com).
3. Selecciona **Archivo > Subir cuaderno** (o abre directamente desde la pestaña **GitHub** pegando la URL de este repositorio).
4. Asegúrate de subir los archivos de datos (`users` y `usage`) en el panel izquierdo de archivos de Colab si las rutas son locales.
5. Ejecuta todas las celdas en orden haciendo clic en **Entorno de ejecución > Ejecutar todas**.



## Cómo Ejecutar el Notebook
Puedes ejecutar este proyecto fácilmente en la nube sin instalar nada en tu computadora usando **Google Colab**:

1. Haz clic en el archivo del notebook (`.ipynb`) dentro de este repositorio o descárgalo.
2. Abre [Google Colab](https://google.com).
3. Selecciona **Archivo > Subir cuaderno** (o abre directamente desde la pestaña **GitHub** pegando la URL de este repositorio).
4. Asegúrate de subir los archivos de datos (`users` y `usage`) en el panel izquierdo de archivos de Colab si las rutas son locales.
5. Ejecuta todas las celdas en orden haciendo clic en **Entorno de ejecución > Ejecutar todas**.

---

##  Entorno Local
Si prefieres reproducir el análisis de forma local en tu equipo:


1. **Instala las dependencias necesarias:**
   Asegúrate de tener Python 3.8+ instalado y ejecuta:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```
2. **Verifica la ubicación de los datos:** Coloca los archivos CSV originales en la misma carpeta que el notebook (o ajusta la ruta en `pd.read_csv()`).
3. **Inicia Jupyter Notebook:**
   ```bash
   jupyter notebook
   ```
   Abre el archivo `.ipynb` y ejecuta las celdas secuencialmente de principio a fin.

