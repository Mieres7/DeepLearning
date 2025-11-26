
### Sistemas dinámico
Sistema cuyo estado actual depende de su historia. Sus salidas dependen no solo de las entradas sino también de las entradas y salidas anteriores.

###  SDL: Modelos no paramétricos
Aquellos que necesitan una gran cantidad de parámetros para representar cierto fenómeno. Puede ser infinita.
- Respuesta al impulso
- Respuestas frecuenciales
###  SDL: Modelos paramétricos
Modelos que necesitan una reducida cantidad de parámetros para representar cierto fenómeno. Idealmente 1.

![[Pasted image 20251126151023.png]]


### SDNL: Modelos de estados -> no los usaremos

### SDNL: Modelos paramétricos
Equivalentes no lineales a los lineales
![[Pasted image 20251126152106.png]]

### Nociones básicas de Identificación de SDL

Identificación: Proceso de identificar un modelo, dado este encontrar los parámetros.

- One Step Ahead (OSA): Pedirle al modelo que prediga un paso inmediatamente adelante. Esto para identificar parámetros, basado en el error de la predicción.
