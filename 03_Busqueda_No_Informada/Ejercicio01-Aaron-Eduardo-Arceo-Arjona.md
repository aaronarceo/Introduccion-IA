# Ejercicio 1 — Comparar BFS, UCS, DFS, DLS e IDS en el mapa de Rumania

## Autor

**Aarón Eduardo Arceo Arjona**

### Configuración Propuesta

El par de ciudades es: `Fagaras-Mehadia`

![Propuesta](/03_Busqueda_No_Informada/Propuesta.png)

### Breadth-First-Search

- **Status**: success
- **Path**: Fagaras → Bucharest → Pitesti → Craiova → Drobeta → Mehadia
- **Depth**: 5 roads
- **Cost**: 645 km
- **Expanded**: 15 nodes
- **Generated**: 39 nodes

![Propuesta](/03_Busqueda_No_Informada/BFS.png)

### Uniform-Cost-Search

- **Status**: success
- **Path**: Fagaras → Sibiu → Rimnicu Vilcea → Craiova → Drobeta → Mehadia
- **Depth**: 5 roads
- **Cost**: 520 km
- **Expanded**: 17 nodes
- **Generated**: 42 nodes

![Propuesta](/03_Busqueda_No_Informada/UCS.png)

### Depth-First-Search

- **Status**: success
- **Path**: Fagaras → Bucharest → Pitesti → Craiova → Drobeta → Mehadia
- **Depth**: 5 roads
- **Cost**: 645 km
- **Expanded**: 6 nodes
- **Generated**: 16 nodes

![Propuesta](/03_Busqueda_No_Informada/DFS.png)

### Depth-Limited-Search (l = 3)

- **Status**: cutoff
- **Detail**: limit=3
- **Expanded**: 9 nodes
- **Generated**: 26 nodes
- **Frontier**: max size 6

### Depth-Limited-Search (l = 6)

- **Status**: success
- **Detail**: limit=6
- **Path**: Fagaras → Bucharest → Pitesti → Craiova → Drobeta → Mehadia
- **Depth**: 5 roads
- **Cost**: 645 km
- **Expanded**: 6 nodes
- **Generated**: 11 nodes

![Propuesta](/03_Busqueda_No_Informada/DLS6.png)

### Iterative-Deeping-Search

- **Status**: success
- **Detail**: last_limit=5
- **Path**: Fagaras → Bucharest → Pitesti → Craiova → Drobeta → Mehadia
- **Depth**: 5 roads
- **Cost**: 645 km
- **Expanded**: 37 nodes
- **Generated**: 100 nodes

![Propuesta](/03_Busqueda_No_Informada/IDS.png)

### Tabla Comparativa

| Algoritmo | Status  | Detail       | Depth   | Cost   | Expanded | Generated | Frontier   |
| --------- | ------- | ------------ | ------- | ------ | -------- | --------- | ---------- |
| BFS       | success | —            | 5 roads | 645 km | 15 nodes | 39 nodes  | —          |
| UCS       | success | —            | 5 roads | 520 km | 17 nodes | 42 nodes  | —          |
| DFS       | success | —            | 5 roads | 645 km | 6 nodes  | 16 nodes  | —          |
| DLS (l=3) | cutoff  | limit=3      | —       | —      | 9 nodes  | 26 nodes  | max size 6 |
| DLS (l=6) | success | limit=6      | 5 roads | 645 km | 6 nodes  | 11 nodes  | —          |
| IDS       | success | last_limit=5 | 5 roads | 645 km | 37 nodes | 100 nodes | —          |

### Conclusiones

Al comparar los algoritmos aplicados al par Fagaras-Mehadia, se observa que BFS y UCS coinciden en la profundidad del camino (5 carreteras), pero difieren en el costo: BFS encuentra la ruta con menos carreteras sin importar los kilómetros recorridos (645 km), mientras que UCS sí logra la ruta de menor costo (520 km) pasando por Sibiu y Rimnicu Vilcea, ya que ordena su frontera por el costo acumulado del camino en lugar de por la profundidad. Esto confirma que BFS es óptimo en número de carreteras, pero no necesariamente en costo, y que UCS logra es resultado a costa de expandir más nodos (17 expandidos, 42 generados).

Por otra parte, DFS también obtuvo el camino de 645 km. DFS siempre expande el primer vecino en orden alfabético y sigue bajando por esa rama hasta el fondo, sin comparar profundidad ni costo, por lo que con otra pareja de ciudades podría devolver un camino mucho más largo que el de BFS aunque el grafo sea exactamente el mismo.

En cuanto a DLS, con l=3 el algoritmo no logra alcanzar la meta y termina en cutoff, porque el límite es menor que la profundidad real de la solución (5 carreteras, la misma que reportan BFS e IDS). Al subir el límite a 6, que ya cubre esa profundidad, DLS sí logra encontrar la solución con el mismo número de nodos expandidos que DFS.

Finalmente, IDS logra encontrar la solución óptima en profundidad sin necesidad de conocer previamente el límite correcto, ya que va aumentando el límite en cada iteración hasta encontrarla; sin embargo, esto tiene un costo en cuanto a nodos expandidos y generados (37 y 100 respectivamente), pues repite la búsqueda desde la profundidad 0 en cada iteración.
