# Práctica 1

### Integrantes
- **Jose Alejandro Barrios Pico** - 2212278
- **Sergio Daniel Velez Santander** - 2202789

Escuela de Ingenierías Eléctrica, Electrónica y de Telecomunicaciones  
Universidad Industrial de Santander

### Fecha
25 de febrero de 2025

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

### Procedimiento
Debe basarse en las acciones efectivamente realizadas durante el laboratorio, describiendo los procesos realizados y los resultados obtenidos. Para cada práctica se pueden brindar preguntas orientadoras o pasos a seguir para establecer lo que se espera lograr/estudiar/analizar/obtener/comparar. Por ejemplo:
- Describa los procesos realizados en el laboratorio  y los resultados obtenidos.
- ¿Cómo se alcanza el límite de Nyquist y que pasa cuando se disminuye de este?
- ¿Por qué al interpolar una señal en GNURADIO su frecuencia disminuye?
- ¿Por qué al diezmar una señal en GNURADIO su frecuencia aumenta?
- ¿Cómo se puede determinar la frecuencia máxima de una señal desde lo experimental?
- ¿Qué le sucede a una señal de audio cuando no se respeta el teorema de Nyquist?
- Describa las funciones logradas con el Ecualizador desarrollado con GNURadio.

### Conclusiones
Se sintetizan los principales aportes y puntos relevantes de la práctica, evitando repetir lo ya consignado en las otras secciones del informe. 

### Referencias
Ejemplo de referencia:

- GNU Radio. (2024, 19 de febrero). Wikipedia, La enciclopedia libre. Fecha de consulta: 12:04, febrero 19, 2024 desde https://es.wikipedia.org/w/index.php?title=GNU_Radio&oldid=158297509
- Teorema de muestreo de Nyquist-Shannon. (2024, 11 de diciembre). Wikipedia, La enciclopedia libre. Fecha de consulta: 11:07, diciembre 11, 2024 desde https://es.wikipedia.org/w/index.php?title=Teorema_de_muestreo_de_Nyquist-Shannon&oldid=164064264
- ChatGPT. (2025). Respuesta generada por un modelo de inteligencia artificial. OpenAI.
