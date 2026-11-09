# Proyecto Final – Fundamentos de Integración

## 1. Descripción

Este proyecto desarrolla un proceso de integración, limpieza y transformación de datos utilizando la base de datos Northwind.

Se trabaja con dos conjuntos de datos: `orders` (pedidos) y `order_details` (detalles de los pedidos), los cuales presentan inconsistencias relacionadas con valores faltantes, registros duplicados, errores de formato, tipos de datos incorrectos y valores fuera de rango.

El proyecto implementa un pipeline de procesamiento de datos en Python para mejorar su calidad, consolidar las fuentes y generar un dataset estructurado que permita realizar análisis de ventas más confiables.

## 2. Objetivo

Diagnosticar, limpiar, transformar e integrar los datos de pedidos de Northwind para obtener un conjunto de datos consolidado, consistente y verificable.

Se busca:
- Identificar problemas de calidad en las fuentes originales.
- Detectar valores faltantes, duplicados e inconsistencias.
- Aplicar transformaciones justificadas técnicamente.
- Integrar las tablas mediante la clave `order_id`.
- Validar que la integración no genere pérdidas ni duplicaciones de registros.
- Generar archivos CSV con los resultados del procesamiento.

## 3. Fuentes de datos

**Fuente principal: Sales Analysis on Northwind Database**

Origen: Kaggle.

Enlace: https://www.kaggle.com/datasets/emmanueltugbeh/northwind-orders-and-order-details

La base de datos Northwind es una base de ejemplo creada por Microsoft.

Se utilizan dos archivos:

| Archivo | Descripción |
|---|---|
| `orders.csv` | Información de los pedidos. |
| `order_details.csv` | Información de las líneas de cada pedido. |

**Relación entre las fuentes:**

Las tablas se relacionan mediante la columna `order_id`, estableciendo una relación de uno a muchos: un pedido puede contener varias líneas de productos.

Los archivos originales se descargan mediante enlaces de Google Drive utilizando la librería `gdown`.

**Licencia:** La licencia de redistribución de los datos no está especificada en este proyecto. Se debe consultar la licencia y condiciones de uso del dataset original en Kaggle.

## 4. Requisitos

Para ejecutar el proyecto se requiere:

- Python 3.
- Google Colab o Jupyter Notebook.
- Conexión a Internet.
- Librería `pandas`.
- Librería `gdown`.

Instalación de las dependencias:

```python
!pip install pandas gdown
```

Las librerías utilizadas son:

- `pandas`: lectura, manipulación, limpieza e integración de datos.
- `gdown`: descarga de los archivos CSV desde Google Drive.

## 5. Instalación y ejecución

Se recomienda utilizar Google Colab para ejecutar el proyecto sin necesidad de instalar Python localmente.

**Procedimiento:**

1. Ingresar a Google Colab: https://colab.research.google.com/
2. Abrir el notebook `Avance_2_base_de_datos_nueva.ipynb` desde este repositorio de GitHub.
3. Seleccionar el entorno de ejecución de Python.
4. Verificar la conexión a Internet.
5. Ejecutar todas las celdas mediante:

   `Runtime → Run all`

6. Esperar a que finalice el procesamiento de los datos.
7. Verificar los resultados y los archivos CSV generados.

El notebook descarga automáticamente los archivos originales, realiza el diagnóstico, aplica las transformaciones, integra las fuentes y genera los datasets finales.

## 6. Resultados

El proceso genera dos archivos principales:

**1. northwind_consolidado.csv**

Dataset final que contiene la información integrada de pedidos y detalles de pedidos.

- 2.149 registros.
- 19 columnas.
- 830 pedidos integrados.
- Sin duplicaciones de claves `order_id + product_id`.

**2. northwind_huerfanas.csv**

Archivo que conserva las líneas de pedido que no pudieron relacionarse con un pedido correspondiente.

- 6 registros.
- 5 columnas.

**Principales resultados de calidad:**

- Se identificaron y trataron registros duplicados.
- Se estandarizaron formatos de fechas y categorías.
- Se corrigieron valores numéricos y formatos inconsistentes.
- Se trataron valores faltantes mediante reglas documentadas.
- Se conservaron los registros que no podían completarse con información confiable.

**Validaciones finales:**

- Se conservaron las 2.149 líneas de detalle durante la integración.
- Se integraron los 830 pedidos.
- No se generaron duplicaciones de registros durante la unión.
- El importe total antes y después de la integración se mantuvo en 1.249.945,73.

## 7. Limitaciones

- Algunos valores faltantes no pueden recuperarse debido a la ausencia de información confiable en las fuentes originales.
- Los registros huérfanos se conservan por separado para evitar perder información.
- La recuperación de precios utiliza el precio conocido del mismo producto en el pedido más cercano, por lo que depende de la consistencia histórica de los precios.
- La recuperación de descuentos utiliza información de otras líneas del mismo pedido cuando existe un único descuento identificable.
- Los archivos originales dependen de la disponibilidad y los permisos de los enlaces de Google Drive.
- La ejecución requiere conexión a Internet para descargar las fuentes originales.

---

## Reproducibilidad

El proyecto está organizado para que cualquier persona pueda reproducir el proceso siguiendo las instrucciones de instalación y ejecución.

El notebook contiene el código necesario para descargar las fuentes, diagnosticar su calidad, aplicar las transformaciones, integrar los datos, realizar las validaciones y generar los archivos finales.

Los resultados pueden verificarse mediante los archivos CSV publicados en este repositorio.

**Repositorio:** ProyectoFinalFundamentosIntegracion

**Tecnologías:** Python, Pandas, Google Colab y GitHub.
