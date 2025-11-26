ppt 4
## 1. Perceptron Multicapa

Veníamos de la base del Adaline en que se buscaba el hiperplano que separa 2 clases linealmente. Pero nos enfrentamos a problemas así, un problema no lineal: 
![[Pasted image 20251112145542.png]]
Problemas como el XOR no podían resolverse con solo 1 capa. Con 2 capas si se puede. Con mas capas se van resolviendo ciertos problemas. Utilizar solo funciones lineales nos limita a tener solo rectas (función de activación). Era complicada implementar las no lineales en hardware. 
El error era un problema para las capas internas (No se sabe que es el error, que se hace con él). En el de 1 sola neurona esto no es problema. 

#### Red multicapa
Red en que las neuronas están ordenadas en capas o estratos sucesivos. Capa capa recibe la entradas desde la capa previa (o entrada externa) y envían sus salidas a la capa siguiente. No hay conexiones internas en cada capa. 

* en el perceptron multicapa se asume que las funciones de agregación son sumatorias 

![[Pasted image 20251112150341.png]]


##  2. Backpropagation

Rumelhart y McClelland -> La hipótesis conexionista

Inicia con la inclusion de una función no lineal como activación. Resultando en un J complicado, y por tanto es complicado encontrar los pesos W, los cuales se buscan para minimizar J. 

El método backprop va modificando los pesos a medida que se le entregan ejemplos a la red. 

#### *esto ideal repasar con el ppt y ver los ejercicios*

