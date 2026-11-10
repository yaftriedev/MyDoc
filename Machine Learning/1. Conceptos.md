# Conceptos

## **Regresión vs de Clasificación**

- **Regresión:** Predecir un *valor continuo numérico;* predicción de precios según características, temperatura segun lugar y tiempo, predicciones de resultados deportivos.
- **Clasificación:** Predecir una *clase* o *categoría;* como spam o no spam, clasificación de animales, enfermedades posibles de una persona por sintomas.

## **Modelos vs Red Neuronal**

- **Modelos:** Los modelos tradicionales de Scikit-learn como *regresión lineal, árboles de decisión, máquinas de soporte vectorial (SVM),* entre otros, tienen estructuras mucho más *simples y eficientes* en comparación con las redes neuronales por ello *son mejores para menos datos.*
- **Red Neuronal:** Están inspiradas en el funcionamiento de las neuronas del cerebro humano. Están compuestas por varias *capas* de *nodos*, cada una de las cuales realiza *cálculos complejos*. Y se dividen en capas de *entrada, ocultas y de salida*.

## **Tipos de activaciones**

- **Capas ocultas:** ReLU o variantes (Leaky ReLU, ELU)
- **Capa de salida:**
    - Clasificación binaria: **Sigmoide**
    - Clasificación multiclase: **Softmax**
    - Regresión: **Lineal**