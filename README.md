# Práctica SQL 02 — Databricks

Soluciones de dos casos de práctica de SQL en **Databricks SQL · Delta Lake · Unity Catalog**. Cada caso tiene 10 preguntas básicas y 20 intermedias.

| Notebook | Caso | Tablas | Datos |
|---|---|---|---|
| [`caso_01_preguntas.ipynb`](caso_01_preguntas.ipynb) | E-commerce Andino: clientes, pedidos, ventas y devoluciones | 6 | [`source01/`](source01) |
| [`caso_02_preguntas.ipynb`](caso_02_preguntas.ipynb) | Academia Online: estudiantes, cursos, pagos y sesiones | 7 | [`source02/`](source02) |

## Cómo ejecutarlo

1. En Databricks, importa el notebook (**Workspace → Import**) y conéctalo a **Serverless**.
2. Ejecuta la celda **0.1**, que crea los esquemas y el volumen `workspace.sql_practice_raw.datasets`.
3. En **Catalog Explorer**, dentro de ese volumen, crea las carpetas `source01` y `source02` y sube a cada una los `.txt` de la carpeta del mismo nombre de este repositorio.
4. Ejecuta toda la **PARTE 0**. La validación 0.6 debe mostrar `estado = OK` en todas las tablas y `huerfanos = 0` en todas las relaciones.
5. Ejecuta la celda de configuración (`USE CATALOG` / `USE SCHEMA`) y luego las preguntas.

Si tu catálogo no se llama `workspace`, reemplázalo en todo el notebook, también en las rutas `/Volumes/workspace/...`.

## Reglas de negocio aplicadas

- **Caso 01:** venta válida es todo pedido con `estado <> 'cancelado'`. El importe neto de una línea es `cantidad * precio_unitario * (1 - descuento_pct / 100)`.
- **Caso 02:** ingreso es todo pago con `estado_pago = 'aprobado'`. La tasa de finalización es inscripciones completadas ÷ inscripciones totales.

Cuando un enunciado admite más de una interpretación, la decisión tomada está comentada en la propia celda de la consulta.

## Datos

Los archivos `.txt` son CSV con encabezado, en UTF-8. Contienen datos ficticios creados para la práctica (los correos usan el dominio `example.com`).
