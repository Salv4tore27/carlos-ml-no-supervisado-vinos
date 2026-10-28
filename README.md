# Vinos: tres particiones y una proyección

Ejercicio individual de Carlos Mario Salvatore Ocampo Aguilar para **R1-A3-S12, Introducción a Machine Learning**.

[Abrir el cuaderno en Google Colab](https://colab.research.google.com/github/Salv4tore27/carlos-ml-no-supervisado-vinos/blob/main/Carlos_ML_No_Supervisado_Colab.ipynb)

El cuaderno compara K-means, Ward y una mezcla gaussiana sobre 13 mediciones del conjunto Wine. Calcula inercia, silueta, Davies–Bouldin y ARI; este último usa las clases conocidas únicamente como comprobación posterior. PCA y SVD permiten medir lo que se pierde al pasar de trece variables a dos ejes.

Las celdas ya contienen sus salidas. En Colab se puede pulsar **Entorno de ejecución > Ejecutar todo**; los datos vienen con scikit-learn y `resultados/` se genera otra vez. Para ejecución local, instala `requirements.txt` en Python 3.

Con tres grupos, K-means obtuvo ARI 0,8975 y Ward 0,7899. Las dos primeras componentes conservaron el 55,41 % de la varianza. El informe discute por qué una silueta similar no implica igual acuerdo con las clases y por qué la proyección bidimensional es incompleta.

Datos: `sklearn.datasets.load_wine`. Marco de trabajo: *Guía implementación de Machine Learning no supervisado*, REA 1, Universidad de Cundinamarca.
