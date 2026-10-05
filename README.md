# Descuentos, precio y rentabilidad en un e-commerce

Proyecto final · Módulo 4 — Estadística y Probabilidad para Data Science orientada a Machine Learning.

Análisis estadístico de **397,569 líneas de pedido** de un e-commerce (2021–2025), para entender qué factores —precio, descuento, categoría, proveedor, calificación— se relacionan con la ganancia por línea de pedido (`profit`).

## Dataset

- Fuente: [E-Commerce Sales Analytics Dataset](https://www.kaggle.com/datasets/datascikhan/e-commerce-sales-and-customer-analytics) (Kaggle).
- De las tablas disponibles se usan solo dos:
  - `order_items.csv` — 397,569 líneas de pedido (cantidad, precio, descuento, impuesto, envío, costo, ganancia).
  - `product_catalog.csv` — 1,175 productos (categoría, subcategoría, marca, proveedor, calificación).
- Los CSV están incluidos en este repositorio

## Estructura del repositorio

```
proyecto/
├── data/
│   └── raw/
│       ├── order_items.csv       
│       └── product_catalog.csv   
├── notebooks/
│   └── Proyecto_final_mod4.ipynb
└── README.md
```

> El notebook carga los datos con rutas relativas (`../data/raw/...`), así que debe ejecutarse **desde dentro de `notebooks/`** y con los CSV ya colocados en `data/raw/`.

## Instalación

Requiere Python 3.10+.

```bash
pip install pandas numpy matplotlib seaborn scipy statsmodels scikit-learn jupyter ipykernel
```

## Cómo ejecutarlo

1. Clona el repositorio y entra a la carpeta del proyecto.
2. Abre `notebooks/Proyecto_final_mod4.ipynb` (Jupyter, VS Code o JupyterLab) y ejecuta todas las celdas en orden (*Run All*).
   - Con ~400,000 filas, el ANOVA + Tukey y las figuras tardan un par de minutos.

## Contenido del notebook

1. Introducción y planteamiento de la problemática
2. Objetivo general y objetivos específicos
3. Descripción del dataset y diccionario de variables
4. Carga de datos y revisión inicial (tipos, nulos, duplicados)
5. Limpieza y preparación (unión de tablas, resolución de columnas duplicadas, verificación de fórmulas, variables derivadas)
6. Análisis exploratorio (estadística descriptiva, distribuciones, categóricas, relaciones iniciales)
7. 5 hipótesis estadísticas, con su prueba correspondiente
8. Intervalo de confianza al 95% para la ganancia media
9. Pruebas estadísticas: t-test (Welch), ANOVA + Tukey, correlación de Spearman
10. Matriz de correlación
11. Regresión lineal simple (`profit ~ unit_price`) con validación train/test
12. Análisis de residuos (heterocedasticidad, normalidad)
13. Interpretación general, conexión con Machine Learning, glosario en lenguaje sencillo
14. Conclusiones y recomendaciones

## Principales hallazgos

- La **categoría del producto** es el factor más determinante en la ganancia: Electronics (~$535 por línea) y Jewelry (~$447) frente a Books & Media (~$50) y Grocery (~$63).
- Los productos de **precio por encima de la mediana** generan una ganancia ~4 veces mayor que los de precio bajo.
- El **descuento** se asocia con menor ganancia; a partir de 40–60% de descuento, 1 de cada 5 líneas termina en pérdida.
- La calificación del producto y el proveedor **no** muestran relación significativa con la cantidad comprada ni con el costo de envío, respectivamente.
- Un modelo de regresión simple con `unit_price` explica ~44% de la variabilidad de `profit`; los residuos muestran heterocedasticidad, lo que sugiere que un modelo multivariable (o basado en árboles) sería más adecuado para un futuro proyecto de Machine Learning.

## Integrantes

| Nombre | 
|---|
| Richard Feliciano 
| Johan Mercedes Dotel
| Yelitza Santana Rivas
