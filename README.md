# Extracción de Datos desde la API del Banco Mundial

## Descripción del proyecto

Este proyecto consiste en desarrollar un script en Python que permite obtener datos económicos y sociales mediante la API pública del Banco Mundial.

El objetivo es automatizar la extracción de información, procesar las respuestas en formato JSON y almacenar los resultados en un archivo CSV estructurado para su posterior análisis.

## Tecnologías utilizadas

- **Python:** lenguaje de programación utilizado.
- **Requests:** permite realizar peticiones HTTP a la API.
- **Pandas:** se utiliza para procesar, limpiar y combinar los datos.
- **Python-dotenv:** permite cargar variables de entorno desde un archivo `.env`.
- **CSV:** formato utilizado para almacenar los resultados.

## Fuente de datos

Los datos provienen de la API pública del Banco Mundial.

Enlace: https://api.worldbank.org/v2/

Se consultan nueve indicadores:

- Población total.
- Producto Interno Bruto (PIB).
- Inflación anual.
- Tasa de desempleo.
- Esperanza de vida.
- Consumo de energía per cápita.
- Porcentaje de usuarios de Internet.
- Gasto público en educación.
- Gasto en salud.

## Funcionamiento del programa

**1. Extracción de datos**

El script realiza peticiones GET a la API del Banco Mundial para obtener los indicadores seleccionados. Se implementa paginación para recuperar los registros disponibles.

**2. Manejo de errores**

Se utiliza `try-except` y `raise_for_status()` para controlar posibles errores de conexión, respuestas HTTP incorrectas y problemas al procesar los datos.

**3. Transformación**

Las respuestas JSON se convierten en DataFrames mediante Pandas.

Se seleccionan las columnas necesarias, se corrigen los tipos de datos y se eliminan registros inválidos o duplicados.

**4. Integración**

Los diferentes indicadores se combinan mediante operaciones `merge`, utilizando el código del país y el año como claves comunes.

**5. Exportación**

El resultado se guarda en el archivo `data_extracted.csv`, que contiene los indicadores organizados por país y año.

Algunos valores pueden estar vacíos debido a que no todos los indicadores tienen información disponible para todos los períodos.

## Instalación y ejecución

Para instalar las dependencias necesarias:

```bash
pip install -r requirements.txt
```

Crear un archivo `.env` en la carpeta principal del proyecto con el siguiente contenido:

```dotenv
WORLD_BANK_API_URL=https://api.worldbank.org/v2
```

Para ejecutar el programa:

```bash
tp4.ipynb
```

Una vez finalizada la ejecución, se genera el archivo `data_extracted.csv`.

## Seguridad

Se utiliza un archivo `.env` para gestionar la configuración de acceso a la API sin escribirla directamente en el código.

El archivo `.gitignore` evita que `.env` y otros archivos temporales sean incluidos en el repositorio.

La API utilizada es pública y no requiere una clave de autenticación.

## Resultado

Como resultado se obtiene un dataset que integra diferentes indicadores económicos y sociales del Banco Mundial.

Este archivo puede utilizarse posteriormente para análisis estadísticos, visualización de datos y proyectos de ciencia de datos.
