# Wine: particiones y pérdida de información

Trabajo de Carlos para **R1-A3-S12 — Introducción a Machine Learning**, actividad 73638 de la Universidad de Cundinamarca.

[Abrir en Colab](https://colab.research.google.com/github/Salv4tore27/carlos-ml-no-supervisado-vinos/blob/main/Carlos_ML_No_Supervisado_Colab.ipynb) · [Informe en Overleaf](https://www.overleaf.com/project/6ae17814def32a35d66b557e) · [PDF del informe](Carlos_Informe_ML_No_Supervisado_APA.pdf)

## Pregunta y alcance

¿Cómo cambian las particiones de 178 vinos al usar centroides, fusiones o densidades gaussianas? Se comparan K-means, Ward y una mezcla gaussiana sobre trece mediciones químicas. PCA y SVD permiten medir la pérdida de la representación bidimensional. Las clases conocidas se usan únicamente al calcular ARI después del ajuste.

## Ejecutar desde cero

1. Abre el enlace de Colab y elige **Entorno de ejecución > Ejecutar todo**.
2. Espera a que termine la última celda de código; debe indicar que las comprobaciones se superaron.
3. Revisa tablas y gráficos. La carpeta `resultados/` se vuelve a generar con los cálculos de esa ejecución.

No se necesita montar Drive, descargar datos externos ni configurar claves. Colab incluye las bibliotecas utilizadas. Para ejecución local, crea un entorno Python, instala las dependencias y abre el notebook en Jupyter:

```bash
python -m pip install -r requirements.txt
python -m pip install jupyter
jupyter notebook
```

El notebook muestra las versiones de Python y las bibliotecas de cada ejecución. Se conserva semilla 42 y 20 inicializaciones de K-means. El redondeo, la numeración de los clusters y los signos de componentes PCA pueden variar sin alterar la interpretación.

## Resultados del experimento

| Método | Silueta | Davies–Bouldin | ARI externo |
|---|---:|---:|---:|
| K-means | 0,2849 | 1,3892 | 0,8975 |
| Ward | 0,2774 | 1,4186 | 0,7899 |
| Mezcla gaussiana | 0,2844 | 1,3938 | 0,8804 |

La mejor silueta del barrido aparece con k=3. La diferencia de silueta entre K-means y la mezcla es de apenas 0,0005; no demuestra superioridad general. PCA retiene 55,41 % de varianza y SVD de rango dos tiene error relativo 0,6678.

El cuadrado del error relativo coincide con la fracción de varianza descartada. Una proyección clara no demuestra separación perfecta ni capacidad de generalización.

## Contenido del repositorio

| Archivo | Para qué sirve |
|---|---|
| `Carlos_ML_No_Supervisado_Colab.ipynb` | Código, explicación, resultados visibles y comprobaciones de consistencia |
| `Carlos_Informe_ML_No_Supervisado_APA.pdf` | Informe actualizado, figuras, análisis y referencias APA |
| `requirements.txt` | Dependencias para ejecución local |
| `resultados/seleccion_k.csv` | Barrido de grupos e inercia/silueta |
| `resultados/comparacion_metodos.csv` | Métricas de los algoritmos |
| `resultados/resumen.json` | Resumen numérico del experimento |
| `resultados/*.png` | Figuras generadas por el notebook |

## Límites

Las clases de Wine no representan calidad comercial. Los grupos podrían orientar una revisión química exploratoria, pero no validan decisiones sobre lotes reales. No se han realizado pruebas con muestras externas ni un estudio de estabilidad entre semillas. Las comprobaciones automáticas revisan integridad numérica, no validez científica.

## Fuentes

- Scikit-learn developers. (s. f.). [Clustering](https://scikit-learn.org/stable/modules/clustering.html).
- Scikit-learn developers. (s. f.). [PCA](https://scikit-learn.org/stable/modules/generated/sklearn.decomposition.PCA.html).
- Scikit-learn developers. (s. f.). [load_wine](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.load_wine.html).
- Universidad de Cundinamarca. (s. f.). *Guía implementación de Machine Learning no supervisado*. REA 1, material del curso.

Revisión: 28 de octubre de 2026. El cuaderno original se verificó también en Google Colab el 27 de octubre; esta revisión se volvió a ejecutar localmente con todas las salidas guardadas.
