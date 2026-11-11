# Cuaderno de apuntes
Jimmy Ontaneda
## 1. Microcontroladores y microprocesadores

Un **microcontrolador** es un circuito integrado que contiene CPU, memoria RAM, memoria Flash y periféricos de entrada y salida. Está diseñado para realizar tareas específicas en sistemas embebidos. Su frecuencia de funcionamiento depende del modelo y generalmente se encuentra en rangos de MHz.

Un **microprocesador** contiene principalmente la unidad central de procesamiento (CPU) y puede requerir componentes adicionales para funcionar, como memoria y periféricos. Se utiliza en sistemas de mayor capacidad de procesamiento, como computadoras.

Los sistemas embebidos son dispositivos electrónicos diseñados para cumplir funciones específicas mediante hardware y software, como sistemas de control, alarmas y automatización.

## 2. Tipos de memoria

Las memorias permiten almacenar instrucciones y datos necesarios para el funcionamiento del microcontrolador. Entre las principales encontramos:

- **RAM:** memoria volátil que almacena información temporal durante la ejecución.
- **SRAM:** tipo de RAM rápida que conserva datos mientras existe alimentación eléctrica.
- **Flash:** memoria no volátil utilizada para almacenar programas y firmware.
- **ROM:** memoria no volátil que contiene información permanente.
- **EEPROM:** permite almacenar y modificar datos que deben conservarse incluso sin alimentación.
- **EPROM:** memoria que puede borrarse mediante luz ultravioleta y posteriormente programarse.
- **HDD y SSD:** dispositivos de almacenamiento; el HDD utiliza discos magnéticos y el SSD utiliza memoria Flash.

## 3. Arquitectura del ESP32

El ESP32 es un microcontrolador utilizado en sistemas embebidos e Internet de las Cosas (IoT). Integra procesamiento, memoria, conectividad Wi-Fi y Bluetooth, además de diferentes periféricos.

Dependiendo de la variante, puede disponer de dos núcleos de procesamiento, memoria SRAM, memoria Flash, convertidores ADC y pines GPIO. Su capacidad permite desarrollar aplicaciones de comunicación, automatización y control electrónico.

## 4. Buses y registros

Los **buses** son medios de comunicación que permiten intercambiar información entre la CPU, la memoria y los periféricos. Se clasifican en:

- **Bus de datos:** transporta la información.
- **Bus de direcciones:** identifica la ubicación donde se desea acceder.
- **Bus de control:** coordina las operaciones de lectura, escritura y sincronización.

Las operaciones principales son *Read* (lectura) y *Write* (escritura).

Los **registros** son pequeñas unidades de almacenamiento que permiten guardar temporalmente datos y configuraciones. Se clasifican en registros de propósito general y registros de función especial, estos últimos utilizados para controlar periféricos y funciones del microcontrolador.

## 5. GPIO, PIN y sistemas numéricos

GPIO significa *General Purpose Input/Output* y representa los pines configurables como entradas o salidas. Los pines de entrada reciben señales de componentes externos, mientras que los de salida envían señales para controlar dispositivos.

Los estados digitales principales son HIGH (nivel lógico alto) y LOW (nivel lógico bajo). En el ESP32 se trabaja habitualmente con niveles de 3.3 V.

También se utilizan diferentes sistemas numéricos:

- **Binario:** base 2, utiliza 0 y 1.
- **Decimal:** base 10, utiliza los números del 0 al 9.
- **Hexadecimal:** base 16, utiliza números del 0 al 9 y letras de la A a la F.

Un byte está compuesto por 8 bits y puede representar valores entre 0 y 255 sin signo.

## 6. Comunicación y conexiones

La conexión USB permite transmitir datos y proporcionar alimentación eléctrica al microcontrolador. Generalmente utiliza 5 V para alimentación, aunque el ESP32 trabaja internamente con niveles lógicos de 3.3 V.

Los pines principales de alimentación son:

- **3.3 V:** alimentación lógica.
- **GND:** referencia eléctrica o tierra.
- **VIN/5V:** entrada de alimentación, dependiendo de la placa.

El pin GPIO 0 está relacionado con el botón BOOT y permite seleccionar el modo de programación. El GPIO 2 puede utilizarse para controlar un LED y el GPIO 12 puede intervenir en la configuración de arranque de determinados modelos ESP32.

## 7. Programación del ESP32

Existen diferentes entornos de desarrollo, entre ellos Arduino IDE y ESP-IDF.

Arduino IDE facilita la programación mediante las funciones `setup()` y `loop()`. La primera se ejecuta una sola vez para configurar el sistema, mientras que la segunda repite continuamente las instrucciones.

ESP-IDF es el entorno oficial de Espressif y permite un mayor control sobre el hardware, los periféricos y las funciones internas del microcontrolador.

## 8. Interrupciones y temporizadores

Las **interrupciones** permiten atender eventos sin esperar a que termine el ciclo normal del programa. Pueden originarse por señales externas, como pulsadores, o por eventos internos, como temporizadores.

La detección de flancos permite identificar cambios en señales digitales:

- **RISING:** cambio de LOW a HIGH.
- **FALLING:** cambio de HIGH a LOW.
- **CHANGE:** cualquier cambio de estado.

Los **temporizadores (Timers)** permiten medir intervalos de tiempo y generar alarmas o interrupciones. Sus elementos principales son la frecuencia, resolución, contador y valor de alarma. La autorrecarga permite reiniciar automáticamente el contador después de alcanzar el valor establecido.

El bus APB (*Advanced Peripheral Bus*) permite la comunicación con determinados periféricos. Un período de 12.5 ns corresponde a una frecuencia de 80 MHz.

## 9. Cálculos de temporización

Las principales fórmulas utilizadas son:

- Período: \(T=1/f\)
- Frecuencia: \(f=1/T\)
- Resolución: \(R=1/f\)
- Tiempo de alarma: \(t=N\times R\)
- Número de ticks: \(N=t\times f\)

Por ejemplo, una frecuencia de 10 000 Hz tiene una resolución de 0.1 ms. Si la alarma está configurada en 2500 ticks, el tiempo será:

\[
t=2500\times0.1=250\,ms
\]

## 10. Funciones de tiempo y bajo consumo

La función `millis()` permite conocer el tiempo transcurrido desde el inicio del programa en milisegundos, facilitando la ejecución de tareas sin bloquear el sistema, a diferencia de `delay()`.

El modo **Deep Sleep** reduce considerablemente el consumo energético del ESP32, desactivando gran parte de sus componentes internos mientras espera una condición de activación.

Finalmente, los pulsadores pueden presentar rebotes eléctricos al presionarse. Para evitar múltiples detecciones de una misma pulsación se utiliza la técnica de antirrebote (*Debouncing*), mediante software o circuitos electrónicos. En los apuntes se considera un intervalo de referencia de 80 ms.

---

## Declaración de uso de inteligencia artificial

Se utilizó una herramienta de inteligencia artificial como apoyo para organizar, complementar y precisar las ideas de los apuntes originales, así como para mejorar su redacción y estructurar el contenido en formato Markdown. Se mantuvo como referencia principal la información recopilada durante las clases, sin modificar la finalidad académica del material.
