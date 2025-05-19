# Predicción de reingreso hospitalario a corto plazo

Este repositorio contiene el proyecto de análisis y modelado de la probabilidad de reingreso hospitalario a corto plazo mediante métodos de análisis de supervivencia, aplicado al sistema GRD en Chile citeturn0file1turn0file11.

## Tabla de Contenidos

* [Descripción del Proyecto](#descripción-del-proyecto)
* [Estructura del Repositorio](#estructura-del-repositorio)
* [Datos](#datos)
* [Instalación](#instalación)
* [Uso](#uso)
* [Metodología](#metodología)
* [Resultados Principales](#resultados-principales)
* [Autores](#autores)
* [Licencia](#licencia)

## Descripción del Proyecto

En el sistema hospitalario chileno, los Grupos Relacionados por el Diagnóstico (GRD) permiten clasificar pacientes según criterios clínicos y de uso de recursos. Este estudio:

* Construye una base de datos de más de 700.000 hospitalizaciones.
* Realiza limpieza, exploración descriptiva y análisis de supervivencia (Kaplan–Meier y Cox PH).
* Evalúa la probabilidad de reingreso a 7, 30, 60 y 90 días post-alta.
* Identifica predictores clave (edad, severidad, peso GRD, número de procedimientos) con un C-index moderado (0.59) citeturn0file1.

## Estructura del Repositorio

```
├── data/                   # Datos originales y complementarios
│   ├── grd_2023.csv        # Dataset principal GRD
│   ├── hospitales.csv      # Información de hospitales
│   └── IR-GRD.csv          # Códigos y descripciones GRD
├── notebooks/              # Notebooks de análisis
│   ├── 01_Tratamiento_Datos.ipynb   # Limpieza y preparación de datos
│   ├── 02_Descriptivo.ipynb         # Análisis descriptivo y EDA
│   ├── 03_00_Modelo.ipynb           # Curvas de Kaplan–Meier
│   ├── 03_01_Modelo.ipynb           # Ajuste de Cox PH regularizado L2
│   └── 03_02_Modelo.ipynb           # Análisis por subgrupos (oncología, regiones)
├── reports/                # Informes en PDF
│   ├── TOPD_Tarea03.pdf    # Primer informe de supervivencia
│   └── TOPD_Tarea04.pdf    # Informe con análisis regional oncología
├── requirements.txt        # Dependencias del proyecto
└── README.md               # Archivo de ayuda (este documento)
```

## Datos

* **grd\_2023.csv**: Episodios hospitalarios con variables demográficas y clínicas.
* **hospitales.csv**: Nombres y códigos de hospitales.
* **IR-GRD.csv**: Peso relativo, severidad y mortalidad asociados a cada GRD.

Más detalles de la estructura de datos están en la sección **Estructura del Conjunto de Datos** del informe citeturn0file4.

## Instalación

1. Clonar el repositorio:

   ```bash
   git clone https://github.com/tu_usuario/GRD-Reingreso.git
   cd GRD-Reingreso
   ```
2. Crear y activar un entorno virtual (recomendado):

   ```bash
   python3 -m venv venv
   source venv/bin/activate   # Unix/macOS
   venv\Scripts\activate    # Windows
   ```
3. Instalar dependencias:

   ```bash
   pip install -r requirements.txt
   ```

## Uso

* Lanzar Jupyter Notebook:

  ```bash
  jupyter notebook
  ```
* Ejecutar cada notebook en orden:

  1. `01_Tratamiento_Datos.ipynb`
  2. `02_Descriptivo.ipynb`
  3. `03_00_Modelo.ipynb`, `03_01_Modelo.ipynb`, `03_02_Modelo.ipynb`

Cada notebook está documentado con secciones de **Objetivos**, **Código** y **Resultados**.

## Metodología

1. **Limpieza y Preparación**: Fusión de datos, creación de variables de duración y eventos 7/30/60/90 días.
2. **Exploración Descriptiva**: Histogramas, correlaciones y análisis por grupos de diagnóstico.
3. **Análisis de Supervivencia**:

   * Curvas de Kaplan–Meier estratificadas (grupos GRD, subgrupos oncológicos, regiones).
   * Modelo de Cox Proportional Hazards con penalización L2, validación de supuestos.

## Resultados Principales

* La mayoría de los reingresos ocurre dentro de los primeros 30 días (pico al día siguiente y primera semana).
* Se evidencian diferencias entre grupos diagnósticos: pacientes oncológicos (C81–C96) muestran mayor riesgo temprano.
* El modelo de Cox regularizado logra un C-index de \~0.61, identificando edad, severidad y número de procedimientos como predictores significativos.

Detalles y visualizaciones completas en los informes de la carpeta `reports/`.

## Autores

* Bruno Caro Maturana
* Gabriel Marín Rocuant
* Docente: Carlos Pérez-Pizarro
* Ayudante: Mattias Morales-Ruiz

## Licencia

Este proyecto está bajo la licencia MIT. Consulte el archivo `LICENSE` para más detalles.
