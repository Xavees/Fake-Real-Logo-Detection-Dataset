# Detección de Logos Reales y Falsos con Inteligencia Artificial

Este proyecto tiene como objetivo entrenar un modelo de Inteligencia Artificial capaz de clasificar imágenes de logos como **reales** o **falsos** utilizando Python, Google Colab, TensorFlow/Keras y un dataset de Kaggle.

El proyecto fue desarrollado como parte de una actividad académica enfocada en el entrenamiento de modelos de IA en Google Colab, con énfasis en la documentación del proceso, el análisis de los resultados y la identificación de las limitaciones del modelo.

---

## Objetivo del Proyecto

El objetivo principal de este proyecto es crear un modelo de clasificación binaria para analizar imágenes de logos y clasificarlas en dos categorías:

* **Real**: logos considerados reales u originales dentro del dataset.
* **Fake**: logos considerados falsos o generados dentro del dataset.

La propuesta no es crear un verificador oficial de autenticidad de marcas, sino entrenar un modelo capaz de aprender patrones visuales a partir de un conjunto de datos previamente etiquetado.

---

## Dataset Utilizado

El dataset utilizado fue **Fake/Real Logo Detection Dataset**, disponible en Kaggle.

Enlace del dataset:

```text
https://www.kaggle.com/datasets/prosperchuks/fakereal-logo-detection-dataset
```

Durante el análisis de la estructura de los archivos, se identificaron dos carpetas principales:

```text
genLogoOutput/
output/
```

Para el desarrollo del modelo, esas carpetas fueron reorganizadas de la siguiente manera:

```text
dataset_final/
  fake/
  real/
```

La cantidad final de imágenes quedó así:

```text
fake: 550 imágenes
real: 275 imágenes
```

Esto muestra que el dataset está desbalanceado, ya que posee más ejemplos de la clase `fake` que de la clase `real`.

---

## Tecnologías Utilizadas

* Python
* Google Colab
* Kaggle API
* TensorFlow/Keras
* NumPy
* Matplotlib
* Scikit-learn
* Pandas

---

## Etapas del Proyecto

### 1. Descarga del Dataset

El dataset fue descargado directamente desde Kaggle utilizando la API de Kaggle en Google Colab.

```python
!kaggle datasets download -d prosperchuks/fakereal-logo-detection-dataset
```

Luego, el archivo fue descomprimido:

```python
!unzip fakereal-logo-detection-dataset.zip -d logos_dataset
```

---

### 2. Organización de los Datos

Las imágenes fueron reorganizadas en dos clases principales:

```text
fake
real
```

Esta organización facilitó la carga de las imágenes mediante TensorFlow.

---

### 3. Preprocesamiento de las Imágenes

Las imágenes fueron redimensionadas a:

```text
70x70 píxeles
```

Este tamaño fue utilizado para reducir el costo computacional y facilitar el entrenamiento del modelo en Google Colab.

También se realizó la separación automática de los datos en:

```text
80% para entrenamiento
20% para validación
```

---

### 4. Creación del Modelo

Se creó un modelo de red neuronal convolucional, también conocido como **CNN**.

Este tipo de modelo es ampliamente utilizado en problemas de visión computacional, ya que permite analizar patrones visuales en imágenes, como formas, bordes, colores y estructuras.

La arquitectura utilizada estuvo compuesta por:

* Capa de normalización de píxeles.
* Capas convolucionales.
* Capas de pooling.
* Capa flatten.
* Capa densa.
* Capa de salida con activación sigmoid.

La salida del modelo corresponde a una clasificación binaria:

```text
real o fake
```

---

## Entrenamiento

El modelo fue entrenado durante 10 épocas.

Resultado aproximado obtenido:

```text
Precisión de entrenamiento: 89%
Precisión de validación: 90%
```

Estos resultados indican que el modelo tuvo un buen desempeño general dentro del conjunto de validación.

---

## Matriz de Confusión

La matriz de confusión mostró que el modelo tuvo un mejor desempeño al identificar logos falsos que logos reales.

Resultado observado:

```text
121 logos fake clasificados correctamente como fake.
0 logos fake clasificados incorrectamente como real.

28 logos reales clasificados correctamente como real.
16 logos reales clasificados incorrectamente como fake.
```

Esto indica que el modelo aprendió bien los patrones de la clase `fake`, pero presentó mayor dificultad con la clase `real`.

Una posible explicación es el desbalance del dataset, ya que había más imágenes falsas que reales.

---

## Pruebas con Imágenes Externas

También se realizaron pruebas con imágenes externas al dataset.

Durante estas pruebas, se observó que el modelo siempre intenta clasificar la imagen como `real` o `fake`, incluso cuando la imagen no pertenece al dominio esperado.

Esto ocurre porque el modelo fue entrenado solamente con dos clases. No posee una tercera categoría, como:

```text
no es logo
imagen inválida
no reconocido
```

Por lo tanto, una limitación importante del modelo es que no debe ser utilizado como un verificador oficial de autenticidad de marcas.

---

## Limitaciones del Modelo

El modelo presentó buenos resultados en el conjunto de validación, pero posee algunas limitaciones:

* El dataset está desbalanceado.
* Las imágenes tienen baja resolución.
* El modelo solo clasifica imágenes entre `real` y `fake`.
* El modelo no verifica si un logo es oficialmente verdadero o falso.
* Imágenes muy diferentes a las del dataset pueden generar predicciones incorrectas.
* El modelo no posee una clase para imágenes fuera del dominio, como paisajes, personas u objetos.

---

## Posibles Mejoras Futuras

Algunas mejoras posibles para futuras versiones del proyecto serían:

* Utilizar un dataset más grande.
* Equilibrar mejor la cantidad de imágenes reales y falsas.
* Utilizar imágenes con mayor resolución.
* Crear una tercera clase para imágenes que no sean logos.
* Probar modelos más avanzados de visión computacional.
* Aplicar técnicas de data augmentation.
* Usar transfer learning con modelos preentrenados.

---

## Conclusión

El proyecto logró alcanzar su objetivo principal: entrenar un modelo de Inteligencia Artificial capaz de clasificar logos como reales o falsos con base en los patrones aprendidos en el dataset.

El modelo alcanzó una precisión de validación cercana al 90%, lo que representa un resultado satisfactorio para una primera aproximación académica.

Sin embargo, las pruebas también mostraron limitaciones importantes. El modelo no debe interpretarse como una herramienta definitiva para validar la autenticidad de marcas, sino como una demostración práctica de clasificación de imágenes utilizando redes neuronales convolucionales.

El análisis de los errores y limitaciones hace que el proyecto sea más completo, ya que permite proponer mejoras futuras y comprender mejor los desafíos involucrados en el entrenamiento de modelos de IA.

---

## Observación de Seguridad

Archivos de credenciales, como `kaggle.json` o tokens de la API de Kaggle, no deben ser enviados a GitHub.

En caso de utilizar la API de Kaggle, mantén estos archivos fuera del repositorio y agrégalos al `.gitignore`.

Ejemplo:

```text
kaggle.json
```

---

## Estado del Proyecto

```text
Finalizado para fines académicos.
```
