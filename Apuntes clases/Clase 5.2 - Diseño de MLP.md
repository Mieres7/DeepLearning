
Pasos para elaboración de modelos con MLP superficiales.
### Paso 1: Exhaustivo análisis de sistema.
	
Establecer número y tipos de variables de entrada y salida, posibilidad de red. de dimensión. 
Es realmente necesario usar un modelo neuronal?
Si se decide usar un modelo neuronal, se tiene los datos adecuados al fenómeno a modelar? y en la cantidad suficiente?

### Paso 2: Preprocesamiento
- **Datos:** Un modelo neuronal es de tipo ´Caja negra´. Modelos de interpolación, depende fuertemente de calidad y cantidad de datos. Solo infieren sobre los datos de entrenamiento
- **Calidad:** Relacionada con el grado con que los datos disponibles representan la función que se está aproximando. 
- **Cantidad**: Importante, pues solo una cantidad de datos adecuada nos permite identificar en forma correcta los parametros de nuestro modelo. Si la cantidad es pequeña no podemos pretender elaborar un modelo neuronal complejo.
- **Examinar**: Detectar outliers, una atenta examinación permite a veces detectar correlación entre variables por lo tanto reducir dimensionalidad, etc. 
- **Normalización de variables**: Cuando se tienen variables con diferentes unidades y por tanto amplitudes a veces varios ordenes de magnitud diferente.

### Paso 3: Diseños del MLP
- Número de neuronas (entrada y salida)
- Número de neuronas de capa intermedia: 
	-Nc: Lo importante es que dicho número de lugar a una cantidad de parámetros (pesos) Nw tal que:
	$$N_w < numeroEjemplos / 10$$
	El número de pesos Nw de un MLP, con 1 capa de entrada con Ne neuronas, capa oculta con Nc neuronas y salida con Ns neuronas es:
	$$N_w = (N_e + 1)\cdot N_c + (N_c + 1) \cdot N_s$$

![[Pasted image 20251126115906.png]]

- Función de transferencia (activación): Lo lógico es utilizar funciones no lineales (derivables) para facilitar la retro propagación, en la  capa oculta. Para la salida se pueden usar lineales o no lineales según lo requiera el problema. 

### Paso 4: Entrenamiento

Proceso delicado por la complejidad que ostenta la superficie de la función error, la que puede tener multiples mínimos locales, puntos silla, etc.

Hay 3 problemas principales:
- **Sesgo (bias)** -> Es un modelo muy simple para lo que quiero modelar, probablemente la función J quedó en un mínimo local
	- Como reducirlo? : Partir desde pesos iniciales aleatorios y aumentar prudentemente el número de neuronas, que se adapte mejor a los datos
- **Sobre parametrización** 
- **Sobre aprendizaje**
	- (aplica para los 2 anteriores) Problema de gran varianza -> El modelo se aprende de memoria los datos de entrenamiento y para valores nuevos (test) no obtendré buenos resultados.
	- Suele darse cuando tenemos una red con exceso de neuronas, demasiado compleja para lo que queremos modelar
	- Como solucionar? Trabajar con dos conjuntos: entrenamiento y test
		- Early stopping: detener el aprendizaje apenas el error sobre el conjunto de test comience a aumentar
		- Validación cruzada: cuando no tenemos muchos datos disponibles. Fold
		- Poda: Iniciar red con gran cantidad de pesos e ir podando bajo ciertos criterios. Cortar caminos que no me alteran el resultado, análisis de sensibilidad.
		- Regularización: Modificación a la función objetivo, agregar términos a esta de tal manera que al minimizarla se penalice la complejidad del modelo. La idea es simplificar el modelo, considerando pesos lo mas chicos posibles. 
Los ultimo dos dan lugar a un fenómeno similar que afecta a la capacidad de ´generalización´ de la red (alta varianza)


### Paso 5: Generalización

Utilizar un conjunto de generalización para probar esta capacidad del modelo. Este conjunto es distinto a los otros. Debe ser tan representativo como cualquier otro conjunto que se use.


#### Formas de validación de modelos de clasificacion
- Matriz de confusion
- Curva ROC
#### Para regresion
- IA -> Indice de adecuación
- RMS -> Error cuadrático medio
- RSD



PREGUNTA DE PEP: CUALES SON LOS PRINCIPALES PROBLEMAS DEL ENTRENAMIENTO Y QUE HARIA PARA DISMINUIR EL SESGO