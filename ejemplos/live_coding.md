# Guión Live Coding

Tomás de Camino Beck, Ph.D.  
Universidad CENFOTEC

## Datos
* [Descargar `datos_taller_mep.csv`](https://github.com/Universidad-Cenfotec/IAenEd/blob/main/documentos/datos_taller_mep_preview.csv)

Si quieres, subo también una versión en Excel del dataset.

# Guía rápida para facilitar el taller

## Live coding en **Google Sheets** (10–15 min)

1. **Importar el CSV** → Archivo → Importar → Subir → “Reemplazar hoja de cálculo”.
2. **Limpieza mínima**

   * Formatear números con 1 decimal en `asistencia_pct`, `examen_1`, `examen_2`, `proyecto`, `nota_final`.
   * Insertar filtro (Datos → Crear un filtro).
3. **Estadística básica**

   * `=PROMEDIO(F2:F)` para nota final (ajusta rango).
   * `=MEDIANA(F2:F)`, `=MAX(F2:F)`, `=MIN(F2:F)`.
   * Moda (si procede): `=MODA.UNO(F2:F)`.
4. **Visualización**

   * Insertar gráfico → “Histograma de nota\_final”.
   * Gráfico de barras: **Promedio por sección**

     * Insertar Tabla dinámica: Filas = `seccion`, Valores = PROMEDIO de `nota_final`.
     * Insertar gráfico de barras a partir de esa tabla.
5. **Marcado de riesgo (opcional, 1 min)**

   * Columna nueva `en_riesgo`: fórmula en G2 (ajusta columnas):

     ```
     =IF(OR(D2<80,F2<65),1,0)
     ```
   * Formato condicional para resaltar `en_riesgo=1`.

## Live coding en **Python / Colab** (15 min)

1. Abre [`guia_live_coding_colab.ipynb`](https://github.com/Universidad-Cenfotec/IAenEd/blob/main/documentos/guia_live_coding_colab.ipynb) en Colab.
2. Ejecuta celda por celda:

   * Carga de librerías.
   * **Carga del CSV** (subir archivo o ajustar ruta).
   * `df.describe()` + conteos por `seccion` y `sexo`.
   * Gráficos: histograma de `nota_final`, barras por `seccion`, dispersión **asistencia vs. nota\_final**.
   * Crea `en_riesgo` con umbrales (`80%` asistencia, `65` nota) y lista casos para intervención.

