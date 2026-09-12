# Ejercicio 1 — Cambiar la imagen de predicción en YOLO

## Autor

**Aarón Eduardo Arceo Arjona**

Para este ejercicio decidí emplear las siguiente imagen:

![original](/06_Vision_Computacional/evidencias/Original.JPG)

Dónde se puede observar que hay 5 personas vestidas en traje, algunas con corbatas y otras con moño, algunas corbatas son más difíciles de reconocer por el color de contraste con la camisa.

En cuanto al Notebook se ejcutó en COLAB con GPU

![gpu](/06_Vision_Computacional/evidencias/evidencia_gpu.png)

Y posteriormente se descargó para almacenarlo en este repositorio.

## Evidencia de Ejecución Original

Tras la ejecución del código original se obtuvieron las siguientes imágenes:

![zidane](/06_Vision_Computacional/evidencias/00_zidane_original.jpg)
![bus](/06_Vision_Computacional/evidencias/00_bus_original.jpg)

### Evidencias de Ejecución con Imagen Propuesta

Luego de ejecutar el primer modelo se obtuvo el siguiente resultado:

![corbatas](/06_Vision_Computacional/evidencias/01_corbatas_aaron.jpg)

Mientas que con el segundo modelo de Yolo aplicado a la misma imagen se obtuvo esta imagen:

![corbatas_2](/06_Vision_Computacional/evidencias/01_corbatas_aaron_2.jpg)

Por lo que se puede observar es que prácticamente ambos modelos obtuvieron el mismo resultado. Mismas cajas pero con diferentes probabilidades, en el primer modelo las cajas de las personas tuvieron una probabilidad de confianza mejor, llegando a valores de 0.92 y 0.93 para algunos casos, superando el promedio de 0.88 obtenido en el segundo ejemplo. Sin embargo, otros objetos como las "corbatas" tenían menor probabilidad de confianza en el primer modelo que en el segundo.

Para observar el funcionamiento del modelo YOLO con COCO, se trabajó una segunda imagen, en la que se obtuvieron los siguientes resultados:

![bus_2](/06_Vision_Computacional/evidencias/01_bus_aaron.jpg)

Aquí, el modelo logró encontrar perfectamente el autobus en medio de la calle y también a la persona que se encuentra a su lado. Lo interesante es que YOLO también logró detectar objetos más pequeños como las maletas que carga el transeúnte.

## Conclusiones

En cuanto a las imágenes de muestra de Ultralytics, YOLO detectó sobre Zidane 2 personas y 1 corbata, y sobre Bus, con el segundo modelo, 4 personas, 1 bus y 1 señal de stop. En mi imagen (Corbatas.JPG) el modelo detectó de forma consistente 5 personas y 5 corbatas, tanto con la celda CLI usando yolov8n.pt sin ajustar, como con la celda model() tras el ajuste de 3 épocas. Por eso ambas corridas coinciden en el número de cajas y solo cambian las probabilidades, como se describió antes.

Sobre objetos evidentes que no quedaron etiquetados, el caso más claro son los cinturones, los 5 sujetos de la foto los llevan puestos y se distinguen sin problema a simple vista, pero COCO no incluye una clase para dicho artículo, así que YOLO jamás podrá nombrarlos sin importar qué tan alto o bajo esté el umbral de confianza. Algo parecido pasa con la corbata de la persona de traje verde y camisa negra, el log reporta igualmente 5 corbatas detectadas, pero esa caja en particular tiene una probabilidad tan baja que casi no se alcanza a distinguir en la imagen final, justo el caso de bajo contraste de color entre la corbata y la camisa como posible causa de una detección débil.
