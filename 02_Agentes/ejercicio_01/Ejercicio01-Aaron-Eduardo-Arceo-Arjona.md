# Ejercicio 1 — Cambiar la ubicación del Wumpus y los pits

## Autor

**Aarón Eduardo Arceo Arjona**

### Configuración Propuesta

Mi propuesta de cueva es la siguiente:

![Mi_cueva](/02_Agentes/ejercicio_01/mi_cueva_4x4.png)

### Conclusiones

Luego de ejecutar el código del agente simple, pude observar que este fallaba porque se quedaba dando vueltas en la misma posición (esquina inferior derecha). Como primer paso, el agente se desplazaba a la derecha sin ninguna dificultad hasta llegar a la esquina donde detecta la brisa del pozo que está en la posición (4,2) y da la primera vuelta a la derecha como indica el código, sin embargo al no moverse de su posición, entonces vuelve a percibir la brisa en el siguiente turno y termina girando a la derecha, esta acción es repetida muchas veces hasta que acaba la cantidad máxima de pasos disponibles.

Por otra parte, el agente basado en modelo inicia su recorrido girando a la izquierda y continúa su recorrido hasta estar muy cerca del oro, sin embargo, al tener un pozo en la celda (2,3), no logra avanzar al oro y se queda dando vueltas hasta que se agoten los movimientos en la celda (1,3). Este comportamiento se presenta nuevamente en el agente basado en objetivos.

En cuanto al agente basado en utilidad, se observa que inicia su recorrido hasta la esquina inferior derecha y retorna para encontrar el camino óptimo al oro, lo recoge y regresa a la posición inicial por la ruta más corta y termina escalando con éxito.

Finalmente, el agente basado en aprendizaje fue aquel que logró el objetivo en la menor cantidad de pasos, giró directamente en la dirección del oro, se desplazó hacia él y retornó por el mismo camino seguro, tomándose un total de 11 pasos para realizar la tarea, 10 pasos menos que el agente basado en utilidad.

## Configuración Difícil Propuesta

Mi propuesta de cueva con el camino bloqueado por Wumpus es la siguiente:

![Mi_cueva_dificil](/02_Agentes/ejercicio_01/mi_cueva_4x4_dificil.png)

Aquí se observa que todos los caminos están bloqueados por los pozos y por el Wumpus, por lo que el agente debe eliminar al Wumpus para poder acceder al oro.

### Conclusiones

En la configuración 4x4 difícil, se obliga al agente a eliminar al Wumpus para acceder al oro y cumplir con el objetivo.

Con el agente simple basado en reflejos se observa el mismo comportamiento que con la configuración anterior, es decir, llega a la esquina inferior derecha y se queda dando vueltas repetidas veces hasta que se agotan los turnos. De igual forma tanto el agente basado en modelo como el agente basado en objetivos logran recorrer una ruta más larga, sin embargo, finalizan en la misma posición (esquina inferior derecha) dando vueltas hasta agotar los turnos.

Es hasta el agente basado en utilidad que se logra eliminar al Wumpus y salir satisfactoriamente de la cueva.

Por último, el agente basado en aprendizaje fracasó sin intentarlo, es decir, decidió salir de la cueva sin haberlo intentado, esto puede deberse a que el entorno resultó ser altamente complicado como para efectuar un movimiento y decidió terminar sin antes desplazarse.

## Evidencias

Las evidencias de que se ejecutaron todos los agentes se encuentran en formato .txt en las siguientes carpetas.

- [Mi cueva](/02_Agentes/ejercicio_01/evidencias/)
- [Mi cueva dificil](/02_Agentes/ejercicio_01/evidencias_dificil/)

Todos los archivos tienen los Logs de ejecución de la siguiente forma:

![Evidencia](/02_Agentes/ejercicio_01/evidencias/evidencia_ejecucion.png)
