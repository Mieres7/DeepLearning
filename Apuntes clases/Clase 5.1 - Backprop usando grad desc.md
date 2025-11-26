
Hasta ahora backprop lo hemos usado con grad. desc. que tiene::
ventajas: implementation simple y es un método estándar que generalmente funciona bien
desventaja: lento, ineficiente, puede quedar atrapado en mínimo locales entregando resultados sub-óptimos

paso de busqueda: cuanto avanzo yo hacia el minimo, generalmente son valores pequeños.
![[Pasted image 20251126105809.png]]  En este ejemplo se ve como elegir un paso (a=1) de búsqueda, nos deja oscilando entre -1 y 1, sin llegar al minimo global de la función.


## Mejoras a gradiente descendente.

1. Momentum: Agrega un término a la función general: 
![[Pasted image 20251126105953.png]]Funcion general sin momentum*
Añade porcentaje del ultimo movimiento al actual. Le agrega un termino de tal forma que le da un empujón cuando nos quedamos atrapados en un mínimo local. Se usa mucho actualmente.

2. Métodos de optimización:
	- Gradiente conjugado
	- Quasi-Newton
	- Simulated Annealing -> Metaheurísticos
	- Algoritmo genéticos
	- etc

	2.1 Gradiente conjugado: consiste en ir encontrando un dirección que no es la máxima pendiente. La cosa no es bajar muy rápido
	![[Pasted image 20251126110453.png]]La Línea achurada es el 'atajo' que toma grad. conjugado. Segun la fórmula, la dirección de bajada utiliza la información de la dirección anterior ($d_{k-1}$) y un parámetro $\beta$ , que hay que encontrar

	2.2 Métodos de segundo orden tipo Newton:
		Consisten en hacer una expansion de Taylor de la J(w)
		![[Pasted image 20251126110910.png]]Esta función, la del final, cambia la amplitud original del problema por $H^{-1}$. De tal forma que esta amplitud del paso de búsqueda va cambiando de acuerdo a la curvatura que vamos encontrando (2da derivada). 
		
	2.2.1 Quasi-Newton: 
		- $H^{-1}$ se aproxima en forma recursiva
		- BFGS  

	2.2.2 Levenberg-Marquardt (2do orden)
		- Modificiacion de Gauss-Newton
		![[Pasted image 20251126111713.png]]
		Se le agrega un término al hessiano en su diagonal principal para que se alejara lo más posible de ser una matriz mal condicionada, es decir que no fuera invertible la matriz (y por tanto su determinando cercano a 0, y que al invertirla genera problemas.)
		- Ventajas: Bien defini aunque J no sea de rango pleno, globalmente convergente. Era bueno en su epoca pero algo costoso (90's- 00's)

Resumen:
![[Pasted image 20251126112022.png]]
El 3ro es grad. descendente. El de momentum va cercano al de grad. descendente.