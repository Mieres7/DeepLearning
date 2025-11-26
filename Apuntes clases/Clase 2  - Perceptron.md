
## Introducción
Problema transversal -> aproximación de funciones (2 subproblemas: regresión y  clasificación)
- Clasificación: Aproximando una función de densidad de probabilidad de pertenencia a cierta clase. Funciones discriminantes.
- Regresión: Aproximar función generadora (desconocida). Mapear entradas a salidas. Generalmente se usan valores continuos.

## Perceptron
Frank Rosenblatt lo propone. Primero hace un modelo de clasificación, capaz de distinguir una figura entre un cuadrado, triángulo o circulo. 

**Clasificación con perceptron**
Utiliza una función discriminante lineal. Separa clases con un hiperplano (Lo que se busca). Ideal para clases linealmente separables.
![[Pasted image 20251009165855.png]]

**Regla de aprendizaje**: Similar a la de Hebb
![[Pasted image 20251009170413.png]]

*hace un chiste de preguntar en la pep: demostrar que el perceptron converge en tiempo lineal. Ver ppt. 2*


# Adaline 
*ppt. 3*

- Problema de regresión lineal y los mínimos cuadrados: Encontrar un modelo como un problema de optimización

### Redes Monocapa: Adaline
Problema que perseguían (Widrow y Hoff):  Filtro de Wiener adaptativo. Que se adaptara en función de los datos que iban llegando. Usaron mínimos cuadrados para encontrar los parámetros. La idea es que en cada paso se vayan acercando al mínimo. 
Llegan al mismo resultado que Rosenblatt -> Regla de aprendizaje.


