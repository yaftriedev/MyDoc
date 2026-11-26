# Keras

## Tipos de capas (tf, keras)

### Dense: Capa básica, conecta todas las neuronas de una capa a las de la siguiente.
- **Uso**: Tareas generales (clasificación, regresión...).
- **Ejemplo**: `Dense(64, activation='relu')`

### Capas Convolutivas (para imágenes)
- **Conv2D:** Detecta patrones espaciales (bordes, texturas) en imágenes. Visión por computador (CNN).
    - **Ejemplo**: `Conv2D(32, (3, 3), activation='relu')`
- **MaxPooling2D:** Reduce el tamaño espacial, mantiene características importantes.
    - **Ejemplo**: `MaxPooling2D(pool_size=(2, 2))`
- **Flatten:** Aplana la salida de una CNN (2D → 1D) antes de pasar a capas densas.
    - **Ejemplo**: `Flatten()`

### Capas Recurrentes (para secuencias)
- **LSTM:** Memoria a largo plazo en secuencias. Muy usada en texto y series temporales.
    - **Ejemplo**: `LSTM(128, return_sequences=True)`
- **GRU:** Variante más simple y rápida que LSTM.
    - **Ejemplo**: `GRU(128)`

### Capas de Normalización y Regularización
- **Dropout:** Evita el sobreajuste desactivando aleatoriamente algunas neuronas.
    - **Ejemplo**: `Dropout(0.5)`
- **BatchNormalization**: Normaliza activaciones y mejora la estabilidad del entrenamiento.
    - **Ejemplo**: `BatchNormalization()`

## Compilacion (tf, keras)

### Optimizer: Controla **cómo se actualizan los pesos** durante el entrenamiento.
    
| Optimizador | Uso común |
| --- | --- |
| `'sgd'` | Descenso de gradiente simple |
| `'adam'` | Muy usado, combina momentum + RMSProp |
| `'rmsprop'` | Útil en RNNs y datos secuenciales |
| `'adagrad'` | Bueno para datos escasos (texto, por ejemplo) |

### Loss: Indica qué tan mal lo está haciendo el modelo.
    
| Tipo de tarea | Pérdida recomendada |
| --- | --- |
| Regresión | `'mse'` o `'mae'` |
| Clasificación binaria | `'binary_crossentropy'` |
| Clasificación multiclase (etiquetas one-hot)| `'categorical_crossentropy'` |
| Clasificación multiclase (etiquetas enteros)| `'sparse_categorical_crossentropy'` |

### Metrics: Se usan solo para evaluación (no afectan el entrenamiento).
    
| Métrica | Uso |
| --- | --- |
| `'accuracy'` | Clasificación |
| `'mae'` | Regresión: error absoluto medio |
| `'mse'` | Regresión: error cuadrático medio |

## Estrcutura Básica

```python
from tensorflow.keras.models import Sequential
import tensorflow.keras.layers

# Crear el modelo
model = Sequential([capas])

# Compilar el modelo
model.compile(optimizer='', loss='', metrics=[''])

# Entrenamiento y Pruebas
model.fit(X_train, y_train, epochs=10, batch_size=32)
loss, metric = model.evaluate(X_test, y_test)

# Predecir
result = model.predict(x)
```