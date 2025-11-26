# Resumen: MLP para Sistemas Dinámicos

**Fuente:** Universidad de Santiago de Chile - Depto. Ingeniería Informática (Dr. Gonzalo Acuña L.)1111.

## 1. Conceptos Fundamentales

### ¿Qué es un Sistema Dinámico?

Un sistema dinámico se define como aquel cuyo **estado actual depende de su historia**2.

- Las salidas (efectos) no dependen solo de las entradas actuales (causas), sino también de las entradas y salidas anteriores3.
    
- **Ejemplo Clásico:** Un circuito RC, descrito por una ecuación diferencial que relaciona voltaje y tiempo4.
    

## 2. Modelos de Sistemas Lineales

Se clasifican en dos grandes categorías según la cantidad de parámetros necesarios para representarlos.

### A. Modelos No-Paramétricos

Requieren una gran cantidad de parámetros (teóricamente infinita) para representar el fenómeno5.

- **Respuesta al Impulso:** Uso de convolución en el tiempo ($h(t)$)6666.
    
- **Respuesta Frecuencial:** Función de transferencia en el dominio de Laplace ($H(s)$) o Z ($H(z)$)7777.
    

### B. Modelos Paramétricos

Utilizan una cantidad reducida de parámetros8. Se basan en ecuaciones de diferencias.

- FIR (Finite Impulse Response): Solo depende de entradas pasadas.
    
    $$y(k) = B(q)u(k) + e(k)$$
    
    9.
    
- ARX (AutoRegressive with eXogenous input): Depende de salidas pasadas y entradas pasadas.
    
    $$y(k) = \sum a_i y(k-i) + \sum b_i u(k-i) + e(k)$$
    
    10.
    
- ARMAX: Agrega un promedio móvil al error (ruido de color).
    
    $$A(q)y(k) = B(q)u(k) + C(q)e(k)$$
    
    11.
    
- Output Error (OE): Modela la relación entrada-salida sin ruido en la autoregresión directa.
    
    $$y(k) = \frac{B(q)}{F(q)}u(k) + e(k)$$
    
    12.
    

## 3. Identificación de Sistemas

El objetivo es encontrar los parámetros que minimicen el error de predicción13.

- Predicción un paso adelante (OSA - One Step Ahead):
    
    $$e(k+1|k) = y(k+1) - \hat{y}(k+1)$$
    
    14.
    
- Función de Costo: Se busca minimizar el error cuadrático medio sobre una secuencia de datos $N$:
    
    $$J_N(\Theta) = \frac{1}{N} \sum_{k=1}^{N} e^2(k)$$
    
    15.
    
- Estructura General:
    
    $$y(k) = G(q)u(k) + H(q)e(k)$$
    
    16.
    
    Donde la predicción óptima $\hat{y}$ se deriva invirtiendo el modelo de ruido $H(q)$17.
    

## 4. Sistemas Dinámicos No Lineales

Cuando el sistema es no lineal, se utilizan **Redes Neuronales (RN)** (como el Perceptrón Multicapa - MLP) para la identificación18.

### Modelos Paramétricos No Lineales

Son extensiones de los modelos lineales, donde las sumas ponderadas se reemplazan por funciones no lineales $f(\cdot)$ (aproximadas por la RN).

#### 1. NARX (Non-Linear ARX) / Equation Error

- **Ecuación:** $y(k) = f(y(k-1), \dots, u(k-1), \dots) + e(k)$19191919.
    
- **Arquitectura:** **Serie-Paralelo (Dirigido)**202020.
    
- **Entradas de la RN:** Entradas pasadas $u(\cdot)$ y **salidas reales pasadas** $y(\cdot)$ (valores deseados)21212121.
    
- **Entrenamiento:** Es más sencillo (feedforward puro) porque se usan los valores reales de $y$ a la entrada, no hay retroalimentación de la predicción durante el entrenamiento22.
    

#### 2. NARMAX

- **Ecuación:** Incluye términos de error pasados $e(k-i)$ en la función no lineal23232323.
    
- **Uso:** Modela sistemas donde el ruido también entra de forma compleja.
    

#### 3. NOE (Non-Linear Output Error)

- **Ecuación:** $w(k) = f(w(k-1), \dots, u(k-1), \dots)$ y $y(k) = w(k) + e(k)$24242424.
    
- **Arquitectura:** **Paralela (No dirigido o Semi-dirigido)**25252525.
    
- **Entradas de la RN:** Entradas pasadas $u(\cdot)$ y **salidas estimadas pasadas** $\hat{y}(\cdot)$ (o $w$)26.
    
- **Características:**
    
    - La red se retroalimenta con su propia predicción27.
        
    - Es necesario para simulación pura cuando no se tiene el dato real futuro.
        

## 5. Arquitecturas de Aprendizaje en RN

Las diapositivas destacan dos modos principales de conectar la red para aprender dinámica:

|**Característica**|**Arquitectura Serie-Paralelo (NARX)**|**Arquitectura Paralela (NOE/Recurrente)**|
|---|---|---|
|**Tipo de Modelo**|Equation Error 28|Output Error 29|
|**Feedback**|Usa salida real $y(k-1)$ (Dirigido) 30|Usa salida estimada $\hat{y}(k-1)$ 31|
|**Estabilidad**|Siempre estable durante entrenamiento (no hay ciclos)|Puede ser inestable (ciclo cerrado)|
|**Entrenamiento**|Backpropagation estándar (estático)|**BPTT (Backpropagation Through Time)** 32|

### Backpropagation Through Time (BPTT)

Para la arquitectura paralela (predicción a múltiples horizontes), el error en el tiempo $t$ depende de las predicciones anteriores debido a la recurrencia.

- Se debe "desenrollar" la red en el tiempo (ver diagrama de predicción a 1, 2 y 3 horizontes)33333333.
    
- El gradiente se propaga hacia atrás a través de las capas y a través de los pasos de tiempo34.
    

---

**¿Te gustaría que genere un ejemplo de código en Python utilizando una librería como PyTorch o Keras para implementar un modelo NARX simple basado en esta teoría?**
C:\Users\vicen\ObsidianVaults\Mieres\Aprendizaje pronfundo\Clase 1 - Introducción.md