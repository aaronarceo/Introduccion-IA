# Ejercicio 1 — Cambiar la ubicación del Wumpus y los pits

## Autor

**Aarón Eduardo Arceo Arjona**

### Configuración Propuesta

Mi propuesta de cueva es la siguiente:

![Mi_cueva](/02_Agentes/ejercicio_01/mi_cueva_4x4.png)

#### Conclusiones

```
Luego de ejecutar el código del agente simple, pude observar que este fallaba porque se quedaba dando vueltas en la misma posición (esquina inferior derecha). Como primer paso el agente se desplazaba a la derecha sin ninguna dificultad hasta llegar a la esquina donde detecta la brisa del pozo que está en la posición (4,2) y el da la primera vuelta a la derecha como indica el código, sin embargo al no moverse de su posición, entonces vuelve a percibir la brisa en el siguiente turno y volverá a girar a la derecha, esta acción es repetida muchas veces hasta que acaba la cantidad máxima de pasos disponibles.

```

## Configuración Difícil Propuesta

Mi propuesta de cueva con el camino bloqueado por Wumpus es la siguiente:

![Mi_cueva_dificil](/02_Agentes/ejercicio_01/mi_cueva_4x4_dificil.png)

Aquí se observa que todas los caminos están bloqueados por los pozos y por el Wumpus, por lo que el agente debe eliminar al Wumpus para poder acceder al oro.

### Conclusiones

```
Conclusiones
```

## Evidencias

Las evidencias de que se ejecutaron todos los agentes se encuentra en formato .txt en las siguientes carpetas.

- [Mi cueva](/02_Agentes/ejercicio_01/evidencias/)
- [Mi cueva dificil](/02_Agentes/ejercicio_01/evidencias_dificil/)
