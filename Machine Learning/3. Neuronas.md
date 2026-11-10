# Redes Neuronales: Neuronas

## Neurona artificial básica

Una neurona realiza una **función matemática** que se puede resumir como:

$$
y = f\Big(\sum_{i=1}^{n} w_i x_i + b\Big)
$$

- $x_i$ = entradas de la neurona (features o variables de entrada)
- $w_i$ = pesos asociados a cada entrada (determinan la importancia de cada entrada)
- $b$ = sesgo (bias), que permite desplazar la función
- $f$ = función de activación (en regresión lineal suele ser la identidad (f(x)=x))
- $y$ = salida de la neurona

## Entradas

- Vector de entrada: $X = [x_1, x_2, ..., x_n]$
- Cada $x_i$ representa una característica o variable independiente.
- Todas las entradas se combinan linealmente mediante sus pesos.

## Salidas

| Tipo de salida | Descripción | Ejemplos |
| --- | --- | --- |
| **Continua (regresión)** | Produce un valor numérico real | Precio de una casa, temperatura, nivel de ventas |
| **Discreta (clasificación)** | Produce una categoría o etiqueta | Spam/no spam, tipo de fruta |
| **Probabilística** | Representa probabilidades de cada clase | [0.7, 0.2, 0.1] → 70% manzana, 20% naranja, 10% plátano |
| **Vectorial / multi-output** | Produce varios valores o etiquetas simultáneamente | Predicción de varias variables continuas, clasificación multi-etiqueta |

# Funciones de Activación

### **Lineal (Identity)**

$$
f(x) = x
$$

- **Rango:** $-\infty, +\infty$
- **Uso:** Regresión, neuronas de salida con valor continuo.
- **Características:** No introduce no linealidad; útil cuando queremos que la salida sea un número real directamente.

### **ReLU (Rectified Linear Unit)**

$$
f(x) = \max(0,x)
$$

- **Rango:** [0, ∞)
- **Uso:** Capas ocultas, redes profundas, CNN.
- **Características:** Muy eficiente computacionalmente; evita saturación; puede sufrir **neurona muerta** si x<0 siempre.

### **Sigmoide**

$$
\sigma(x) = \frac{1}{1+e^{-x}}
$$

- **Rango:** $0, \ 1$
- **Uso:** Clasificación binaria, probabilidades.
- **Características:** Convierte valores en probabilidad; saturación en valores extremos puede causar el problema de **vanishing gradient** (gradientes muy pequeños al entrenar).

### **Tangente hiperbólica (Tanh)**

$$
\tanh(x) = \frac{e^x - e^{-x}}{e^x + e^{-x}} = 2\sigma(2x)-1
$$

- **Rango:** $-1, \ 1$
- **Uso:** Capas ocultas, especialmente con entradas centradas en 0.
- **Características:** Similar a sigmoide pero centrada en 0; mejora la convergencia en redes profundas.

### **Softmax**

$$
f(x_i) = \frac{e^{x_i}}{\sum_{j} e^{x_j}}
$$

- **Rango:** $0, \ 1 \ \sum{x_1}=1$
- **Uso:** Clasificación multiclase.
- **Características:** Convierte un vector de valores en **probabilidades** para cada clase; usada en la capa de salida de problemas de clasificación múltiple.

### **Leaky ReLU**

$$
f(x) = \begin{cases} x \ si \ x>0 \\   \alpha x \ si \ x \le 0 \end{cases} \ α≈0.01
$$

- **Rango:** $-∞, ∞$
- **Uso:** Capas ocultas, mejora ReLU.
- **Características:** Evita el problema de neuronas muertas usando un pequeño gradiente para x<0.

### **ELU (Exponential Linear Unit)**

$$
f(x) = \begin{cases} x \ si \ x>0 \\   \alpha(e^x - 1) \ si \ x \le 0 \end{cases} \ α≈0.01
$$

- **Rango:** $-α, ∞$
- **Uso:** Capas ocultas.
- **Características:** Similar a ReLU pero suaviza gradientes negativos; ayuda a mejorar la convergencia y evita neuronas muertas.