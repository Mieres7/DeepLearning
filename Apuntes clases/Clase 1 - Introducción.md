Motivación: comprender y emular los mecanismos asociados al éxito de los seres cognitivos:
 - Nacen las Redes Neuronales Artificiales 
 - Paradigma no-algoritmico para el procesamiento de la información: de aprendizaje y adaptación, procesamiento distribuido y paralelo.
 - Nuevas herramientas -> PC y se elimina el uso de hardware.

La neurona artificial: Automata caracterizado por:
1. estado interno
2. señales de entrada
3. funciones de agrupamiento y activación
![[Pasted image 20251008165423.png]]

Introduce el **Bias** (sesgo): permite modelar la componente continua de la información de entrada. 
- Por ejemplo sinusoid, al no estar centrada, permite modelar donde esta montada la información. Esa componente en estadística clásica hay que sacarla, aquí se internaliza en el modelo.

Modelo de McCulloch y Pitts: fn. agregación (sumatorio), fn activación (tipo umbral). Salida unica 0 o 1. Con este modelo se pueden replicar cualquier puerta lógica. Usando pesos convenientes se puede simular cualquier computador digital.

### Aprendizaje:
Capacidad de la neurona de ajustar los pesos para que la respuesta deseada satisfaga ciertos criterios
 
Regle de Hebb (1949) -> Primera regla de aprendizaje conocida
Se baso en como las neuronas transmiten información. Especia de sincronización cuando se comunican. a partir de eso nace el hecho de que los pesos van cambiando, segun la formula.

$$
w_{ij_{new}} = w_{ij_{old}} + \alpha x_iy_i
$$
Donde $w$ son los pesos, $\alpha$ es un factor de aprendizaje, y $x$ e $y$ entradas y salidas correspondientemente.

### Redes neuronales Artificiales (RNA)
Conjuntos de neuronas conectadas.  Caracterizado por:
- Número de neuronas
- Arquitectura de interconexión
- Valor de los pesos
- Funciones de agrupamiento y activación

Trabajan en 2 modos. Primero se entrenan, adaptan pesos, arquitectura, funciones, etc. Para luego ser usadas, por ejemplo en reconocimiento o simulación.

Tipos de aprendizaje: Supervisado, No-Supervizado, Por Refuerzo.

### Aprendizaje profundo

Se enfoca en el uso de redes neuronales multi-capa. Aqui tenemos diferentes ejemplos como CNN, LSTM, Autoencoders, GAN, Transformers, etc.

![[gettyimages-1202474000.webp]]