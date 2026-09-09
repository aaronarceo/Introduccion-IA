# Ejercicio 1 — Comparar Greedy y A\* en el mapa de Rumania

## Autor

**Aarón Eduardo Arceo Arjona**

### Configuración Propuesta

El par de ciudades es: `Fagaras-Mehadia`

![Propuesta](/04_Busqueda_Informada/Propuesta.png)

Las heurísticas de Fagaras a Mehadia son las siguientes:

| h(n) | Ciudad         | Nota     |
| ---: | -------------- | -------- |
|    0 | Mehadia        | ← meta   |
|   40 | Drobeta        |          |
|   40 | Lugoj          |          |
|   96 | Rimnicu Vilcea |          |
|   99 | Craiova        |          |
|  103 | Timisoara      |          |
|  124 | Sibiu          |          |
|  155 | Pitesti        |          |
|  171 | Arad           |          |
|  176 | Fagaras        | ← inicio |
|  201 | Zerind         |          |
|  218 | Giurgiu        |          |
|  232 | Bucharest      |          |
|  235 | Oradea         |          |
|  288 | Urziceni       |          |
|  310 | Neamt          |          |
|  348 | Iasi           |          |
|  357 | Vaslui         |          |
|  366 | Hirsova        |          |
|  397 | Eforie         |          |

### A\*

- **Problem**: Fagaras -> Mehadia
- **Heuristic**: Euclidean distance to Mehadia (map coordinates)
- **Status**: success
- **Path**: Fagaras -> Sibiu -> Rimnicu Vilcea -> Craiova -> Drobeta -> Mehadia
- **Depth**: 5 roads
- **Cost**: 520 km

![AS](/04_Busqueda_Informada/AS.png)

Tabla `g / h / f` a lo largo del camino:

| Ciudad         |   g |   h |   f |
| -------------- | --: | --: | --: |
| Fagaras        |   0 | 176 | 176 |
| Sibiu          |  99 | 124 | 223 |
| Rimnicu Vilcea | 179 |  96 | 275 |
| Craiova        | 325 |  99 | 424 |
| Drobeta        | 445 |  40 | 485 |
| Mehadia        | 520 |   0 | 520 |

### Greedy best-first search

- **Problem**: Fagaras -> Mehadia
- **Heuristic**: Euclidean distance to Mehadia (map coordinates)
- **Status**: success
- **Path**: Fagaras -> Sibiu -> Rimnicu Vilcea -> Craiova -> Drobeta -> Mehadia
- **Depth**: 5 roads
- **Cost**: 520 km

![GBFS](/04_Busqueda_Informada/GBFS.png)

Tabla `g / h / f` a lo largo del camino:

| Ciudad         |   g |   h |   f |
| -------------- | --: | --: | --: |
| Fagaras        |   0 | 176 | 176 |
| Sibiu          |  99 | 124 | 223 |
| Rimnicu Vilcea | 179 |  96 | 275 |
| Craiova        | 325 |  99 | 424 |
| Drobeta        | 445 |  40 | 485 |
| Mehadia        | 520 |   0 | 520 |

### Comparación

Ambos algoritmos encuentran el mismo camino óptimo (520 km, 5 tramos). La diferencia está en el esfuerzo de búsqueda: A\* expande 13 nodos (y genera 34), mientras que GBFS expande solo 5 (genera 15) al seguir directamente el menor h(n). En este par de ciudades la heurística mueve a GBFS sin desvíos, por lo que llega al mismo resultado con menos trabajo.

### Conclusiones

Para el par Fagaras-Mehadia, A\* sí encontró el camino de menor costo: la ruta Fagaras → Sibiu → Rimnicu Vilcea → Craiova → Drobeta → Mehadia con 520 km, que coincide con la que reporta UCS de la búsqueda no informada, y es el mínimo real entre esas dos ciudades, ya que las rutas alternativas (por Pitesti o por Timisoara y Lugoj) suman más kilómetros. Esto es lo esperado, porque la heurística de distancia en línea recta es admisible y A\* ordena su frontera por `f(n) = g(n) + h(n)`, es decir, toma en cuenta tanto el costo ya recorrido como una estimación del que falta.

En esta corrida Greedy coincidió con A\* y devolvió exactamente el mismo camino de 520 km, pero fue una coincidencia y no se puede decir que siempre sea de esta forma. Lo que pasó aquí es que, en cada paso, la ciudad con el menor valor de `h(n)` resultó ser también una ciudad del camino óptimo (Sibiu con 124, Rimnicu Vilcea con 96, Craiova con 99 y Drobeta con 40), así que seguir la pista de la heurística nunca llevó a Greedy fuera de la mejor ruta. El problema de Greedy es que decide solo mirando `h(n)`, la estimación de lo que falta para llegar a la meta, y no toma en cuenta `g(n)`, los kilómetros que ya lleva recorridos. Por eso puede meterse por una ciudad que en el mapa se ve cerca del destino pero a la que solo se llega por carreteras muy largas, y una vez que avanza por ahí ya no reconsidera esa decisión. A\* no cae en eso porque suma las dos cosas, lo ya recorrido y lo que falta, y siempre elige el camino con menor total. Con otra pareja de ciudades en el mismo mapa, esa diferencia podría hacer que Greedy devolviera un camino bastante más caro que el de A\*.

Sobre los valores de `f` en el camino de A\*, se observa que no disminuyen, a lo largo de la ruta pasan de 176 en Fagaras a 223, 275, 424, 485 y 520 en Mehadia. La razón es que la distancia en línea recta nunca suma más de lo que cuesta el tramo real. Gracias a esa propiedad, A\* no necesita volver sobre ciudades que ya expandió, y el primer valor de `f` con el que saca la meta de la frontera es directamente el costo del camino óptimo.
