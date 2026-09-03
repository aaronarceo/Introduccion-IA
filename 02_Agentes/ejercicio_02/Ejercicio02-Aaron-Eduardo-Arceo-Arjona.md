# Ejercicio 2 — Descripción PEAS de agentes inteligentes

## Autor

**Aarón Eduardo Arceo Arjona**

### 1. Asistente Virtual de Voz

- **Performance:**
  - Cantidad de veces que el usuario realiza la misma pregunta (Calidad de la respuesta).
  - Tiempo en resolver la petición del usuario.
  - Información proporcionada vs información correcta.
  - Número de veces que responde "Desconozco la información"
  - Retroalimentación del usuario.

- **Environment:**
  - Recámara en la que se encuentra.
  - Persona con la que interactúa.
  - Ruido de fondo.
  - Temperatura del lugar.
  - Ubicación geográfica.

- **Actuators:**
  - Emitir sonidos por altavoz
  - Realizar búsquedas por internet
  - Modificar información en el celular como crear un evento, alarma.
  - Leer notificaciones.
  - Activar dispositivos de domótica como focos, electrodomésticos, etc.

- **Sensors:**
  - Micrófono.
  - API para conectarse a los modelos de lenguaje.
  - Wifi.
  - Reloj.
  - GPS.

El ambiente es parcialmente observable porque solo puede escuchar la voz del usuario, no puede ver ni reconocer otras características del entorno. Estocástico porque los modelos pueden alucinar de pendiendo de la forma en la que el usuario formule la pregunta. Secuencial porque cada respuesta afecta la anterior, dado que guarda información de las preguntas pasadas. Estático porque el usuario se queda esperando la respuesta y Discreto porque a cada pregunta le corresponde una sola respuesta con una cantidad finita de palabras.

### 2. Robot aspirador doméstico

- **Performance:**
  - Tiempo que se toma en limpiar un metro cuadrado.
  - Número de veces que tiene que limpiar un mismo lugar.
  - Horas de duración de la batería.

- **Environment:**
  - Piso sobre el cual limpiar.
  - Recámara en la que se encuentra.
  - Paredes limite.
  - Objetos que se encuentran ahí, como zapatos, juguetes, ropa, etc.

- **Actuators:**
  - Encender luces identificadoras.
  - Emitir sonidos.
  - Mostrar diagramas de limpieza en celular.
  - Aspirar.
  - Colocar agua y jabón para limpiar una zona.
  - Desplazar con ruedas.
  - Girar.

- **Sensors:**
  - Sensores de proximidad.
  - Cámaras frontales.
  - Sensor de nivel de agua y de jabón.
  - Cantidad de batería del dispositivo.
  - Bluetooth y WiFi para conectar el dispositivo.

El ambiente es parcialmente observable porque si logra ver todo el piso pero no puede ver zonas a las que no tiene acceso como debajo de un mueble. Estocástico porque si ejecuta la acción de limpiar, el espacio puede que no quede limpio al 100%. Secuencial porque se guardan los estados de dónde ya realizó una limpieza. Dinámico porque el suelo puede volverse a ensuciar por algún accidente y Continuo, porque a pesar de que el número de metros cuadrados es finito, el robot podría pasarse dando vueltas sin parar a pesar de haber terminado de limpiar.

### 3. Sistema de recomendación de streaming

- **Performance:**
  - Número de veces que el usuario ve la película recomendada.
  - Rating que se le da a la película sugerida luego de verla.
  - Porcentaje de avance que el usuario vio de la película.
- **Environment:**
  - Interfaz de la plataforma.
  - Bases de datos de las películas.
  - Bases de datos de los usuarios.
- **Actuators:**
  - Leer los géneros de películas que el usuario ya vio.
  - Revisar la lista de "por ver" del cliente.
  - Interactuar con APIs que contengan los modelos de agrupamiento.
  - Mostrar la recomendación en la parte superior de la pantalla.
- **Sensors:**
  - Fecha, permite ofrecer películas de acuerdo con la temporada.
  - Registro de interacción de los usuarios con otras películas.
  - Datos históricos.

El ambiente es parcialmente observable porque no puede ver ni escuchar las expresiones del usuario mientras ve la película. Es Estocástico porque el sistema puede arrojar recomendaciones distintas a clientes con comportamientos similares dependiendo ubicación y otras cosas. Es Dinámico y Secuencial porque el modelo arroja resultados diferentes con forme vaya viendo otras películas previamente.

### 4. Vehículo autónomo en ciudad

- **Performance:**
  - Cantidad de accidentes registrados.
  - Experiencia de usuario.
  - Número de veces que el piloto toma el control del vehículo.
  - Tiempo que se toma en completar el viaje.

- **Environment:**
  - Calles de la ciudad.
  - Peatones transitando.
  - Árboles, camellones, aceras, carreteras.
  - Clima.

- **Actuators:**
  - Acelerar, frenar, girar.
  - Alertar fallos.

- **Sensors:**
  - Cámaras frontales y de reversa.
  - Sensor de proximidad.
  - Niveles de batería del vehículo.

El ambiente es parcialmente observable porque a pesar de que pueda percibir muchas cosas a su alrededor no puede ver mas allá de cierta distancia. Es Estocástico porque pueden suceder imprevistos como caídas de peatones, choques, etc. Es Dinámico porque conforme avanza el vehículo el ambiente va cambiando. Es secuencial porque una decisión tomada ahora afecta en el futuro.

### 5. Agente de trading algorítmico en bolsa

- **Performance:**
  - Retorno de Inversión.
  - Rendimiento generado en un periodo de tiempo.
  - Cantidad de veces que efectuó la compra cuando la acción estaba a precio bajo.
  - Número de veces que el agente está offline.

- **Environment:**
  - Bolsa de valores.

- **Actuators:**
  - Comprar y vender acciones.
  - Interactuar con API.

- **Sensors:**
  - Registro histórico de la serie de tiempo.
  - Listado de acontecimientos históricos.
  - Lector de noticias sobre banca.

El ambiente es parcialmente observable porque solo puede ver lo que tiene conectado mediante APIs, no puede ver lo que sucede en todo el mundo. Es Estocástico porque la probabilidad de que se modifique una acción al día siguiente es muy variable. Secuencial porque una decisión afecta a las demás en el futuro. Es Dinámico porque las acciones se mueven a cada milisegundo a pesar de que el agente esté efectuando una acción. Es continuo porque existen infinitas posibilidades de precios de acciones a cada hora.

### 6. Sistema de diagnóstico médico asistido por IA

- **Performance:**
  - Número de diagnósticos calificados como falsos positivos.
  - Cantidad de Doctores que emplean el sistema.
  - Recomendaciones y calificaciones de los usuarios (doctores, pacientes).
  - Profundidad en el diagnóstico médico emitido.

- **Environment:**
  - Interfaz de captura de síntomas.
  - Historial del paciente.
  - Doctor que interactúa con el sistema.
  - Registro de libros y enfermedades existentes.

- **Actuators:**
  - Mostrar el diagnóstico.
  - Enviar correo con el reporte del diagnóstico
  - Sugerir lugares donde comprar los medicamentos.

- **Sensors:**
  - API con hospitales y clínicas.
  - Bases de datos de historiales clínicos.
  - Lector de imágenes (rayos X).
  - Lector de PDFs (resultados clínicos).

El ambiente es parcialmente observable porque solo puede conocer la información que el usuario proporcione. Es Estocástico porque dos pacientes pueden tener diagnósticos diferentes con los mismos síntomas. Es secuencial porque una acción ahora repercute en los síntomas del paciente. Es dinámico porque el usuario se puede sentir mejor mientras se realiza la evaluación médica. Es discreto porque existe un número finito de posibles enfermedades.

## 7. Dron de inspección de infraestructura

- **Performance:**
  - Calidad de las imágenes.
  - Cantidad de anomalías detectadas.
  - Porcentaje de anomalías detectadas correctamente.

- **Environment:**
  - Espacio aéreo.
  - Aves cerca de la zona.
  - Infraestructura construida.
  - Personal dentro de la infraestructura.

- **Actuators:**
  - Girar hélices.
  - Activar cámara.
  - Tomar fotografía.
  - Enviar imágenes a otro dispositivo (celular).

- **Sensors:**
  - Velocímetro y Giroscopio.
  - Nivel de batería del dispositivo.
  - Altura del equipo.
  - GPS.

El ambiente es parcialmente observable porque hay zonas que las cámaras no pueden detectar. Es estocástico porque pueden suceder eventualidades mientras se efectúa el vuelo. Es secuencial porque si se efectúa una acción hacia adelante el objeto seguirá en movimiento por la decisión tomada anteriormente. Es Dinámico porque la infraestructura puede cambiar en el momento que se toma la foto. Es Discreto porque el Dron toma una cantidad finita de imágenes del lugar.

8. Agente jugador de ajedrez

- **Performance:**
  - Partidas ganadas.
  - Tiempo de respuesta por cada jugada.
  - Retroalimentación del oponente.
  - Cantidad de movimientos inválidos.
  - Número de jugadas con las que finaliza la partida.

- **Environment:**
  - Tablero.
  - Piezas.
  - Cronómetro.
  - Oponente.

- **Actuators:**
  - Mover una pieza en el tablero.
  - Notificar sobre Jaque, Jaque mate, Enroque.
  - Detener el cronómetro.
  - Contar el número de jugadas.
  - Registrar movimientos en sistema.

- **Sensors:** ...
  - Leer historial de jugadas.
  - Cámara del tablero.
  - Ver registro de jugadas del oponente.

El ambiente es observable porque el agente puede ver tanto el tablero como las piezas y los movimientos. Es Determinista porque se puede predecir el movimiento de una pieza antes de ser jugada. Es secuencial porque cada jugada repercute en la siguiente para ambos jugadores. Es Estático, porque el oponente esperará a que el agente termine de efectuar el movimiento. Es discreto porque a pesar de que existe una cantidad muy grande de jugadas, estas son finitas.
