# Modelos SKLearn

## **Modelos de Regresion**

- **`sklearn.linear_model.LinearRegression`**: Regresión lineal, uno de los modelos más simples para predecir variables continuas.
- **`sklearn.linear_model.Ridge`** y **`sklearn.linear_model.Lasso`**: Variantes de la regresión lineal que incluyen regularización para evitar sobreajuste.
- **`sklearn.linear_model.ElasticNet`**: Combina las regularizaciones de Ridge y Lasso.
- **`sklearn.svm.SVR`** **(Support Vector Regressor)**: Regresión basada en máquinas de soporte vectorial.
- **`sklearn.tree.DecisionTreeRegressor`**: Árboles de decisión para tareas de regresión.
- **`sklearn.ensemble.RandomForestRegressor`**: Ensamble de múltiples árboles de decisión para mejorar la precisión y evitar el sobreajuste.
- **`sklearn.ensemble.GradientBoostingRegressor`**: Modelo basado en boosting, combina múltiples modelos débiles para mejorar el rendimiento.
- **`sklearn.neighbors.KNeighborsRegressor`**: Basado en los vecinos más cercanos, predice en función de los datos más cercanos en el espacio de características.

## **Modelos de Clasificación**

- **`sklearn.ensemble.RandomForestClassifier`**: Ensamble de árboles de decisión para clasificación.
- **`sklearn.linear_model.LogisticRegression`**: Regresión logística, muy utilizada para tareas de clasificación binaria.
- **`sklearn.neighbors.KNeighborsClassifier`**: Clasificación basada en los K vecinos más cercanos.
- **`sklearn.svm.SVC`(Support Vector Classifier)**: Máquinas de soporte vectorial para clasificación.
- **`sklearn.tree.DecisionTreeClassifier`**: Árboles de decisión para clasificación.
- **`sklearn.ensemble.GradientBoostingClassifier`**: Algoritmo de boosting basado en árboles de decisión, muy efectivo para clasificación.
- **`sklearn.naive_bayes`** (**`GaussianNB`**, **`MultinomialNB`**, **`BernoulliNB`**): Clasificadores basados en el teorema de Bayes.
- **`sklearn.ensemble.AdaBoostClassifier`**: Algoritmo de boosting que combina varios modelos débiles.

## **Redes Neuronales**

- **`sklearn.neural_network.MLPClassifier`**: Utilizado para tareas de clasificación, este modelo puede manejar problemas multiclase. Permite especificar múltiples capas ocultas y nodos, además de funciones de activación como ReLU y la función sigmoide.
- **`sklearn.neural_network.MLPRegressor`**: Similar al anterior, pero orientado a problemas de regresión, permitiendo predecir valores continuos.

## **Entrenamiento, Test y Prediccion**

- **`fit(X, y)`**: Entrena el modelo ajustando la línea a los datos.
- **`score(X, y)`**: Calcula la precisión del modelo utilizando la R² (coeficiente de determinación).
- **`predict(X)`**: Hace predicciones sobre nuevos datos.