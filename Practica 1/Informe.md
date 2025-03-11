# **Práctica 1**
*Este informe contiene el desarrollo de las partes:*
- *1A. GNU Radio para el procesamiento de señales*
- *1B. Reconociendo equipos*
- *1C. Mediciones de potencia y frecuencia*

### Integrantes
- **Jose Alejandro Barrios Pico** - 2212278
- **Sergio Daniel Velez Santander** - 2202789

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
Del 11 al 25 de febrero del 2025

---

## Declaración de Originalidad y Responsabilidad
Los autores de este informe certifican que el contenido aquí presentado es original y ha sido elaborado de manera independiente. Se han utilizado fuentes externas únicamente como referencia y han sido debidamente citadas.

Se utilizó Chat GPT para consultar algunas preguntas presentes en la introducción y a partir de sus respuestas estructurar la información de manera clara y concisa. Además, se complementa con nuestros conocimientos para asegurar que las explicaciones fueran adecuadas.  

---
## Contenido

### Resumen
El software GNU radio contribuye una útil herramienta con la que cuentan los equipos de cómputo del laboratorio de comunicaciones, este permite desarrollar bloques de procesamiento de señales para implementar en sistemas de radio definida por software. La práctica en cuestión se basó en una introducción de la interfaz principal del programa, donde se pudo trabajar con diferentes tipos de bloques los cuales en conjunto forman el diagrama de flujo, con el cual obtendremos la señal deseada. Una vez dominadas las ideas principales y el funcionamiento de GNU radio, se realizó un reconocimiento de los equipos como el SDR, osciloscopio y analizador de espectros, con los cuales se tomaron mediciones de amplitud, variando la frecuencia de transmisión y ganancia.


**Palabras clave:** GNU-Radio, Amplitud, Transmisión, Ganancia, Diagrama. 

### Introducción
Cada práctica contará con preguntas orientadoras para la elaboración de la introducción. Por ejemplo: 
- ¿Qué tan importante es la teoría de muestreo en el procesamiento de señales?

  El teorema de muestreo es importante porque demuestra que toda la información de una señal contenida en el intervalo temporal entre dos muestras cualesquiera, está descrita por la serie total de muestras, siempre que la señal registrada sea de naturaleza periódica.
- ¿Cuáles son los principales potenciales de GNURADIO en el laboratorio de comunicaciones?
  
  GNU-Radio permite modificar valores claves como amplitud, frecuencia de transmisión y ganancia, todo esto realizando un debido montaje de diagrama de bloques. Por lo cual permite hacer varios análisis relacionados al área de las comunicaciones. 
- ¿Qué pasa cuando se alcanza el límite de Nyquist?
  
  Según el teorema de Nyquist, la frecuencia de muestreo debe ser al menos el doble de la frecuencia máxima presente en la señal, en teoría si estamos en el límite no tendríamos aliasing, por otro lado, si la frecuencia de muestreo es menor, si ocurre aliasing y se puede distorsionar la señal
- ¿Qué tan alta debe ser la relación entre la frecuencia de muestreo y la frecuencia de la señal para visualizar la señal correctamente?
  
  Cuando la relación es alta, se obtiene un muestreo rápido que permite capturar la mayoría de datos de la señal original, evitando el aliasing, sin embargo, la relación depende de qué tan rápido cambia la señal, ya que si la relación es muy alta pero la señal no cambia mucho, podremos estar consumiendo memoria de manera ineficiente.
- ¿Cuándo es importante interpolar una señal?

  Interpolar una señal es importante cuando queremos estimar valores intermedios entre nuestras muestras conocidas, con el fin de reconstruir o mejorar una señal. 
- ¿Cuándo es importante diezmar una señal?
  
  Es importante cuando queremos hacer una señal mas simple, reducir el almacenamiento o procesarla más rápido.
- ¿Qué pasa cuando se asigna una frecuencia de muestreo inadecuada?

  Esto puede llevar a varios problemas, dependiendo de si la frecuencia es demasiado baja o innecesariamente alta. Si la frecuencia es demasiado baja, no estaremos tomando suficientes muestras por segundo para capturar correctamente la señal generando aliasing. Ahora si es muy alta tendremos un mayor uso de memoria y procesamiento, lo cual resulta ineficiente.
- ¿Qué conclusiones se pueden obtener sobre la relación entre la potencia de la señal y la calidad de la comunicación?

  Con una potencia alta, la señal es mas clara y obtenemos menos perdidas, sin embargo, es importante tener en cuenta otros favores como pueden ser el ruido o la interferencia, por lo que lo mas recomendable es buscar un equilibrio.
- ¿Cómo afecta el piso de ruido a la capacidad de detectar señales débiles?

  El piso de ruido básicamente es el nivel mínimo de ruido, por lo cual, si nuestra señal es menor a este, no será posible distinguirla por que se vera mezclada con el ruido de fondo. 
- ¿Qué limitaciones tienen los equipos utilizados en términos de ancho de banda y precisión en las mediciones?

  Ver las imágenes guardadas en la carpeta.
- ¿Cómo se pueden mejorar las mediciones de señal en un entorno con alto nivel de ruido?

  Se podría mejorar aumentando la potencia de la señal, reduciendo el piso de ruido y ajustando parámetros como el RBW.
- ¿Qué aplicaciones prácticas tienen las mediciones de potencia y ancho de banda en sistemas de comunicaciones reales?

  Midiendo la potencia se puede garantizar que la señal sea clara y eficiente sin hacer un uso ineficiente de energía. Por otro lado, el ancho de banda permite transmitir mas datos sin interferencias. Todo esto es esencial en sistemas de comunicación como redes móviles, fibra óptica y satélites. 
- ¿Cómo se puede medir la respuesta en frecuencia de un canal alámbrico?
  
  Ver las imágenes guardadas en la carpeta.
- ¿Cómo se puede obtener un modelo sencillo de las pérdidas (pathloss) en un canal inalámbrico?
  
  Ver las imágenes guardadas en la carpeta.
  
### Procedimiento
Cabe resaltar que la presente práctica se desarrolló en tres partes, teniendo como primera parte realizar mediciones de GNU radio para el procesamiento de señales, reconocimiento de equipos y mediciones de potencia y frecuencia. De ésta manera en la primera parte, se exploró la herramienta GNU radio con una guía realizada en la plataforma, a partir de la cual se tomaron capturas de las señales generadas para analizar su comportamiento al interpolar, diezmar y aplicar el teorema de Nyquis. Luego en la segunda parte se realizó un análisis a cerca de la amplitud medida y generada del osciloscopio, junto con medidas de atenuación de un cable coaxial. Para finalmente realizar en la tercera parte mediciones de potencia y frecuencia.

Adicionalmente en la práctica 1C se realizaron 4 actividades a lo largo de la práctica, en las cuáles se realizaron revisiones de especificaciones de los equipos, simulación de señales en GNU Radio, transmisión y medición de señales con el USRP 2920. Cabe aclarar que cada sección contiene preguntas orientadoras que contribuyeron a mejorar el entendimiento de la práctica.

### Conclusiones
La práctica permitió comprender la funcionalidad de GNU Radio como una herramienta clave para la simulación y análisis de señales en el laboratorio de comunicaciones. Su capacidad para modificar parámetros como amplitud, frecuencia y ganancia facilita la experimentación y el estudio de sistemas de radio definida por software.
Se confirmó la importancia del teorema de muestreo y la frecuencia de Nyquist para evitar aliasing y asegurar una correcta reconstrucción de la señal. Además, se evidenció que una frecuencia de muestreo demasiado alta puede ser ineficiente en términos de procesamiento y almacenamiento.
El reconocimiento y uso de instrumentos como el osciloscopio, el analizador de espectros y el SDR permitieron realizar mediciones clave de amplitud, frecuencia y potencia. Se observó la influencia del piso de ruido en la detección de señales débiles y la necesidad de ajustes adecuados para optimizar las mediciones.
Se evidenció que una mayor potencia de señal mejora la calidad de la comunicación, pero debe mantenerse un equilibrio para evitar interferencias o desperdicio de energía. Asimismo, se comprendió la relevancia del ancho de banda en la transmisión eficiente de datos.
La experimentación con interpolación y diezmo permitió visualizar el impacto de estos procesos en la reconstrucción de la señal. Además, la simulación y transmisión de señales con el USRP 2920 permitió evaluar las variaciones de amplitud y atenuación en diferentes condiciones.
Los conceptos trabajados en la práctica tienen aplicaciones directas en sistemas de comunicación inalámbrica y alámbrica, donde el análisis de potencia, ancho de banda y pérdidas en el canal son fundamentales para garantizar transmisiones eficientes y confiables.
En general, la práctica proporcionó una base sólida para el manejo de GNU Radio y la interpretación de señales en el ámbito de las telecomunicaciones, permitiendo mejorar el criterio en el análisis de sistemas de comunicación y medición de señales en entornos reales.

### Referencias
Ejemplo de referencia:

- GNU Radio. (2024, 19 de febrero). Wikipedia, La enciclopedia libre. Fecha de consulta: 12:04, febrero 19, 2024 desde https://es.wikipedia.org/w/index.php?title=GNU_Radio&oldid=158297509
- Teorema de muestreo de Nyquist-Shannon. (2024, 11 de diciembre). Wikipedia, La enciclopedia libre. Fecha de consulta: 11:07, diciembre 11, 2024 desde https://es.wikipedia.org/w/index.php?title=Teorema_de_muestreo_de_Nyquist-Shannon&oldid=164064264
- ChatGPT. (2025). Respuesta generada por un modelo de inteligencia artificial. OpenAI.
