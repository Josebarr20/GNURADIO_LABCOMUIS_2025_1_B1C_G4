# **Práctica 2A**
*Este informe contiene el desarrollo de las partes:*
- *Actividad 1. Simulación de canal en GNU Radio*
- *Actividad 2. Fenómenos de canal en el osciloscopio*
- *Actividad 3. Fenómenos de canal en el analizador de espectros*
- *Actividad 4. Efectos de los fenómenos de canal en la conversión de frecuencia*

### Integrantes
- **Jose Alejandro Barrios Pico** - 2212278
- **Sergio Daniel Velez Santander** - 2202789

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
Del 4 al 18 de marzo del 2025

---

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas. 

Se utilizo la IA Copilot para redactar textos y consultar algunas preguntas orientadoras y a partir de sus respuestas estructurar la información de manera clara y concisa. Además, se complementó con nuestros conocimientos para asegurar que las explicaciones fueran adecuadas.  

---
## Contenido

### Resumen
- *Actividad 1. Simulación de canal en GNU Radio*

  Se dio inicio a la practica cargando el flujograma propuesto por el docente, un aspecto clave fue configurar la frecuencia de muestreo (samp_rate) en 25e6 / 2´n Hz, donde n es un numero entero mayor a 2, en nuestro caso en particular se selecciono un valor de n de cinco. 
Se continúo generando diferentes señales y observando el efecto de variar las frecuencias de corte del filtro, además de analizar el efecto del ruido haciendo uso del osciloscopio y analizador de frecuencia, todo esto para dos tipos de ondas distintas. 
En general la práctica se enfocaba en observar el efecto que genera el canal a la señal transmitida, aspectos claves en la relación señal – ruido y la eficiencia en la transmisión de datos. 

- *Actividad 2. Fenómenos de canal en el osciloscopio*

  El objetivo de esta práctica busca analizar los comportamientos característicos de un canal cableado real en el dominio del tiempo, utilizando el USRP 2920 y GNU Radio. Se Continúa transmitiendo una señal mediante el flujograma filters_flowgraph.grc, y se activan o desactivan bloques clave (Channel Model, Throttle, USRP Sink, USRP Source y Virtual Sink), asegurando una frecuencia de muestreo de 25e6 / 2´n Hz, donde n es mayor que 2, en nuestro caso seleccionamos un n igual a cinco 
Luego, se conecta un osciloscopio a la salida del USRP usando distintos cables coaxiales para visualizar los efectos del canal. Se varía la frecuencia de portadora de 50 MHz a 500 MHz para analizar y comparar el comportamiento de la señal bajo diferentes condiciones. 

- *Actividad 3. Fenómenos de canal en el analizador de espectros*

  El objetivo de esta práctica es estudiar el comportamiento de un canal cableado en el dominio de la frecuencia y observar sus efectos en el analizador de espectros. Se utiliza el USRP 2920 y se ejecuta un flujograma filters_flowgraph.grc en GNU Radio que incluye bloques ajustables como Channel Model, Throttle, USRP Sink, USRP Source y Virtual Sink, con una frecuencia de muestreo de 25e6 / 2´n Hz con un n mayor a dos, en nuestro caso seleccionamos un n con valor de cinco.
Luego se configura y conecta un analizador de espectros, utilizando cables coaxiales, a la salida del USRP. Esto nos permite observar y analizar los efectos del canal real, facilitando el estudio práctico de fenómenos de transmisión. 

- *Actividad 4. Efectos de los fenómenos de canal en la conversión de frecuencia*

  En esta práctica hacemos uso del USRP 2920 y GNU Radio para transmitir y recibir una señal. Configuramos el flujograma filters_flowgraph.grc, activando o desactivando bloques como Channel Model y Throttle, y fijamos la frecuencia de muestreo en 25e6 / 2´n Hz, con n mayor a 2, en nuestro caso seleccionamos un n de valor cinco. 
El objetivo es ver cómo los fenómenos de un canal real afectan la conversión de frecuencia. Comparamos los resultados al recibir la señal a través de diferentes medios, ya sea por aire o usando un cable coaxial, para notar las variaciones en la señal según el medio de transmisión. 


**Palabras clave:** Canal, Frecuencia, Filtro, Ruido, Eficiencia, Cable coaxial,. 

### Introducción
Cada práctica contará con preguntas orientadoras para la elaboración de la introducción. Por ejemplo:

*Actividad 1. Simulación de canal en GNU Radio*

•	¿Cuál es el efecto de filtrar las frecuencias altas de una señal? 

Respuesta: Cuando filtramos las altas frecuencias equivale a aplicar un filtro pasa bajas, por lo cual obtenemos una señal con menos ruido y una forma de onda un poco mas suavizada.  

•	¿Qué sucede al filtrar muy cerca de la frecuencia fundamental de la señal? 

Respuesta: Esto puede generar que la señal se pierda o se modifique la forma en la que es percibida 

•	¿Cuál es el efecto de filtrar las frecuencias bajas de una señal? 

Respuesta: Esto es como si aplicáramos un filtro pasa altas, cuyo objetivo es eliminar las componentes de baja frecuencia. Al eliminar estas frecuencias se puede llegar a eliminar la componente DC. 

•	¿Qué ocurre al eliminar armónicos de una señal? 

Respuesta: Al eliminar los armónicos de una señal, estamos suprimiendo los componentes enteros de la frecuencia fundamental, por lo cual se modificará la representación en el dominio de la frecuencia y la forma de onda en el dominio del tiempo. 

•	¿Qué efecto tiene la desviación de frecuencia en la señal recibida? ¿Qué efectos produce el filtro cuando la señal recibida se ve afectada por desviación de frecuencia? 

Respuesta: Desplaza la señal de la banda esperada, lo que genera errores en la demodulación y perdida de la información. 
 
•	¿Como cuantificar la degradación de la señal al aumentar los niveles de ruido?
 
Respuesta: Principalmente se puede usar la relación SNR, a medida que aumenta el ruido, el SNR disminuye. 

•	¿Como se puede mejorar la relación a ruido en una señal? 

Respuesta: Podemos mejorarla aumentando la potencia de la señal y también aplicando filtros. 

•	¿Como podría cuantificar la calidad de la señal recibida? Considere el caso de señales analógicas y digitales. 

Respuesta: Para las señales analógicas, se utiliza la relación señal – ruido (SNR). En el caso de señales digitales, investigando encontramos que se puede cuantificar a través de la tasa de error de bits (VER). 

*Actividad 2. Fenómenos de canal en el osciloscopio*

  •	¿Cuál es el efecto del ruido sobre la amplitud de las señales medidas en el osciloscopio? ¿Conservan las mismas relaciones que se evidencian en la simulación?

Respuesta: El ruido genera fluctuaciones aleatorias en la amplitud, haciendo que la onda varie de forma menos estable. En la simulación no se asumen algunas efectos e imperfecciones que están presenten en la práctica.

  •	Demuestre ¿cómo se puede mejorar la relación señal a ruido en una señal? 

Respuesta: Se puede mejorar aumentando la potencia de la señal, también es útil aplicar filtros.  

  •	Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? 

Respuesta: Usando cables coaxiales largos, la señal se debilita por las perdidas inherentes en el cable, es decir que entra mayor distancia entre el transmisor y receptor, mayor es la atenuación, esto generaría una menor amplitud. 

*Actividad 3. Fenómenos de canal en el analizador de espectros*

  •	¿Cuál es el efecto del ruido sobre la respuesta en frecuencia de las señales medidas en el analizador de espectro? ¿Conservan las mismas relaciones que se evidencian en la simulación? 

Respuesta: El ruido añade fluctuaciones y distorsiones, haciendo que la grafica no se vea tan suavizada. En la simulación no se asumen algunas efectos e imperfecciones que están presenten en la práctica

•	¿La relación señal a ruido creada intencionalmente desde el computador se amplifica o se reduce en la señal observada en el analizador de espectro?

Respuesta: En la práctica, al transmitir, el hardware y el canal agregan ruido extra, lo que baja la SNR en lo medido.

  •	Usando cables coaxiales de diferentes longitudes, ¿cómo afecta la distancia entre el transmisor y el receptor a la amplitud de la señal medida? 

Respuesta: Usando cables coaxiales largos, la señal se debilita por las perdidas inherentes en el cable, es decir que entra mayor distancia entre el transmisor y receptor, mayor es la atenuación, esto generaría una menor amplitud. 

*Actividad 4. Efectos de los fenómenos de canal en la conversión de frecuencia*
  
  Ver las figuras edjuntadas en la carpeta.

### Referencias
Ejemplo de referencia:

- GNU Radio. (2024, 19 de febrero). Wikipedia, La enciclopedia libre. Fecha de consulta: 12:04, febrero 19, 2024 desde https://es.wikipedia.org/w/index.php?title=GNU_Radio&oldid=158297509
- Microsoft Corporation. (2025). Copilot [Large language model]. Microsoft Corporation.
- ChatGPT. (2025). Respuesta generada por un modelo de inteligencia artificial. OpenAI.
