# Ejercicio 1 — Más capas en el perceptrón multicapa (Iris)

## Autor

**Aarón Eduardo Arceo Arjona**

Para el desarrollo de esta práctica se empleó la extensión de Colab en VSCode que permite utilizar los kernes de Colab directamente en el proyecto local.

![Colab](/05_Perceptron_Multicapa/evidencias/EjecucionColab.png)

## Notebook 01

### Gráfica de Error

![Grafica1](/05_Perceptron_Multicapa/evidencias/GráficaErrorNotebook01.png)

### Gráfica de Error Modificada

![Grafica1](/05_Perceptron_Multicapa/evidencias/GráficaErrorNotebook01-modificada.png)

## Notebook 02

### Gráfica de Error

![Grafica1](/05_Perceptron_Multicapa/evidencias/GráficaErrorNotebook02.png)

### Gráfica de Error Modificada

![Grafica1](/05_Perceptron_Multicapa/evidencias/GráficaErrorNotebook02-modificada.png)

## Conclusiones

Al comparar las gráficas de error, agregar las dos capas ocultas extra sí bajó el error, pero le costó mucho más trabajo llegar ahí: la red original (4x3x3) baja de forma continua desde 0.7 hasta 0.05 en las 500 épocas, mientras que la de 4 capas (4x3x3x3x3) arranca en 0.8 y se queda prácticamente plana en 0.67 desde la época 3 hasta cerca de la 40, para después caer con una pendiente parecida a la de la red original y terminar en un error casi idéntico, alrededor de 0.05. En Keras el comportamiento es distinto, la red original va bajando de 0.26 a 0.16 sin aplanarse en ningún momento, todavía con pendiente negativa en la época 500, por otra parte, la red de 4 capas se estanca de verdad, pasa de 0.27 a apenas 0.22 y, desde la época 200, la curva queda prácticamente horizontal, es decir, deja de aprender mucho antes de terminar las 500 épocas y se queda con un error claramente peor que el de su propia red original.

Las curvas de la notebook 01 y de Keras con la misma topología (4x3x3x3x3) no se parecen, el error final es muy distinto (0.06 contra 0.22) casi cuatro veces más alto en Keras y la meseta tampoco tiene la misma forma, en la notebook 01 es corta y el error cae rápidamente después, mientras que en Keras la caída inicial es más lenta y luego se aplana para quedarse ahí. Esta diferencia probablemente viene de cómo actualiza los pesos cada modelo. La notebook 01 lo hace ejemplo por ejemplo, mientras que Keras agrupa los datos en lotes de 32 por defecto, además de usar otra inicialización de pesos y mezclar los datos entre épocas. Esas diferencias hacen que el gradiente avance de forma distinta en cada una, aunque la topología sea la misma.

Finalmente, sí tiene sentido que una red más profunda no aprenda mejor en Iris, y es justo lo que muestran las gráficas modificadas. Cada capa oculta que se agrega hace que le tome más tiempo a la red ajustar bien los primeros pesos, por eso se ve esa meseta larga al inicio del entrenamiento en ambas versiones modificadas. Además, Iris es un problema sencillo que una sola capa oculta ya resuelve bien, así que agregar más capas no ayuda, solo hace más lento el aprendizaje. Por eso, en Keras la red de 4 capas ni siquiera alcanza a salir de la meseta en las 500 épocas.
