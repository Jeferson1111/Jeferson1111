# Control Digital
En el control rutinario, se toman muestras o señales analógicas que representan el comportamiento del sistema o proceso en el día a día. Sin embargo, para procesar y analizar estas señales en sistemas digitales, es necesario convertirlas en señales digitales, que solo pueden tomar valores de 1 o 0.
Este proceso se conoce como digitalización o conversión analógico-digital (CAD). La digitalización permite que los sistemas digitales, como computadoras y microcontroladores, puedan procesar y analizar los datos del mundo real.
La digitalización se logra mediante un conversor analógico-digital (ADC), que muestrea la señal analógica y la convierte en una secuencia de bits (1 y 0) que representan el valor de la señal en ese momento.

Algunos beneficios de la digitalización son:

1. Mayor precisión y exactitud en la medición.
2. Mayor velocidad en el procesamiento de datos.
3. Mayor capacidad de almacenamiento de datos.
4. Mayor flexibilidad en la manipulación y análisis de datos.
5. Menor susceptibilidad a la degradación de la señal.

Sin embargo, también hay algunas limitaciones en la digitalización, como:

1. Pérdida de información debido a la cuantificación (conversión de valores continuos a discretos).
2. Ruido y errores de digitalización.
3. Requisitos de velocidad y resolución en la conversión.

## conversión analoga digital
La Conversión Analógico-Digital (CAD) es el proceso por el cual una señal de naturaleza analógica, continua y variable en el tiempo, se convierte en una señal digital, discreta y representada por una secuencia de bits (1 y 0). Este proceso es fundamental en la adquisición y procesamiento de datos en sistemas digitales.

*Características clave de la Conversión Analógico-Digital:*

1. *Muestreo*: La señal analógica se muestrea en intervalos definidos de tiempo por segundo por lo tanto la unidad es Hz, esto representa que entre mas grande la tasa de muestreo mas información se puede tomar de la señal analogica y menor va a ser la perdida de información. 
2. *Cuantificación*: Los valores muestreados que se toman en intervalos de etiempo definidos se convierten en puntos o valores para poder asignar un valor digital y asi poder hacer la discretizacion de los mismos.
3. *Codificación*: se asignan valores de tipo digital (1-0) a cada punto o valor muestreado en la señal analogica, asignandolo como tipo binario y asi poder igualar el valor analogo a un numero binario para poderlo utilizar como datos en los aparatos digitales. Esto conlleva que se necesita una mayor capacidad del procesador para poder manejar una mayor informacion entre mas bits pueda manejar mas informacion se puede recolectar.
*Consideraciones*
Los convertidores de analógico a digital (A/D) comerciales tienen un límite en el rango de voltajes que pueden convertir y asignar a un numero binario. En ciertas aplicaciones, es importante tener en cuenta los tiempos de retraso entre el momento en que se toma la muestra y cuando se cuantifica el valor.

Tiempos relacionados con el muestreador y retenedor:
• Ta (tiempo de adquisición): es el intervalo que pasa desde que se da la instrucción de muestreo hasta que el valor se mantiene dentro de un margen de tolerancia aceptable. 
• Tp (tiempo de apertura): es el intervalo desde que empieza la retención hasta que el muestreador se abre. 
• Ts (tiempo de establecimiento): cuando el interruptor se mueve, puede generar capacitancia parásita que causa un transitorio. El tiempo que toma para que esta oscilación se estabilice se llama tiempo de establecimiento.


## Conversion digital a analoga

*Conversor Digital/Analógico (DAC)*

Un DAC es un dispositivo que convierte valores digitales en señales analógicas, creando una correspondencia directa entre ellos.
Para cada valor digital en el rango completo, el DAC puede generar 2^n valores analógicos diferentes, incluyendo el valor cero.
Resolución de un DAC

La resolución de un DAC, al igual que en los convertidores A/D, depende de cuántos bits se usan para representar la señal.

Se mide en voltios o como un porcentaje del rango completo (FS, Fondo de Escala).

Ejemplo con FS = 10V:

Supongamos que el FS del DAC es 10V.
| **Bits (Entrada)** |     **Resolución (V)**  | **Resolución (%FS)** |
|--------------------|-------------------------|------------------------------------------------|
|           4        |    10 / 2^4 = 0,625     |0,625 / 10 × 100 = 6,25%                        |
|           8        |       10 / 2^8 = 0,039  |0,039 / 10 × 100 = 0,39%                        |
|          16        |  10 / 2^16 = 0,0001526  |0,0001526 / 10 × 100 = 0,001526%                |
|             32     |10 / 2^32 ≈ 2,33 x 10^-9 |2,33 x 10^-9 / 10 × 100 ≈ 0,0000000233% |

*Resistores Ponderados*

Cómo funciona: Este método utiliza una serie de resistores con diferentes valores para representar cada bit del valor digital. La configuración es bastante sencilla porque solo necesitas ajustar los valores de los resistores de acuerdo con el número de bits.
Ventajas: Es fácil de configurar y menos costoso en términos de componentes.
Desventajas: La precisión puede no ser la mejor debido a la variabilidad en los valores de los resistores y las tolerancias de fabricación. Esto puede llevar a errores en la señal analógica resultante.

*Red en Escalera R-2R*

Cómo funciona: En este método se usa una red de resistores con solo dos valores, R y 2R, dispuestos en una configuración de escalera. La señal digital se convierte en una señal analógica ajustando la relación de estos resistores.
Ventajas: Aunque la configuración es más compleja que la de los resistores ponderados, el método R-2R es más preciso y tiene mejor estabilidad porque los errores de tolerancia de los resistores se cancelan entre sí.
Desventajas: mas complicado de configurar y programar.

## modelo matematico

Aunque los conversores analógico-digitales (A/D) y digital-analógicos (D/A) realizan operaciones opuestas en las señales, ambos utilizan componentes similares.
Componentes Comunes:
Muestreador: Captura el valor de la señal en momentos específicos.
Retenedor: Mantiene el valor de la señal durante un periodo de tiempo.
Muestreador:

Se puede modelar idealmente como un interruptor controlado por una señal de reloj. Esto significa que el muestreador toma un valor de la señal analógica en intervalos regulares de tiempo.
Retenedor:

Se puede modelar usando una función de transferencia, que describe cómo la señal se mantiene durante el periodo entre muestras.
Características del Conversor Digital-Analógico (DAC):

Igualdad en Magnitud: Las entradas y salidas del DAC tienen la misma magnitud, lo que significa que el rango de valores digitales y analógicos es consistente.
Conversión Instantánea: La conversión de digital a analógico ocurre de manera instantánea, es decir, no hay retraso en la conversión.
Salida Constante: La salida del DAC permanece constante durante el periodo de muestreo, proporcionando una señal estable mientras se realiza la conversión.

*Zero-Order Hold (ZOH)*
El Zero-Order Hold es un método utilizado en sistemas de control digital para convertir una señal digital en una señal analógica. Es una técnica muy común en sistemas donde se necesita convertir una señal digital muestreada en una señal continua para su procesamiento o salida.

En el Zero-Order Hold, la señal digital se mantiene constante durante cada intervalo de muestreo. Es decir, el valor de la señal digital en cada instante de muestreo se mantiene constante hasta el siguiente instante de muestreo.

Simplicidad: El ZOH es fácil de implementar porque solo requiere mantener el valor digital constante durante el intervalo de muestreo.
Requisitos de Hardware: No demanda mucha capacidad de procesamiento del microcontrolador o procesador, reduciendo costos y complejidad en el diseño.
Implementación Práctica: Es un método práctico para sistemas donde la simplicidad y el costo son factores críticos.

Función de Transferencia del ZOH:

Para un sistema de ZOH con un intervalo de muestreo 
𝑇
T, la función de transferencia 
𝐻(𝑠)
H(s) en el dominio de Laplace se puede expresar como:

GZO𝐻(𝑠)=1−𝑒^-𝑠𝑇/s

*First Order Hold (FOH)*

El First Order Hold es una técnica de conversión digital-analógica que utiliza un modelo lineal para interpolar entre muestras. A diferencia del Zero-Order Hold (ZOH), que mantiene el valor constante durante el intervalo de muestreo, el FOH asume que la señal cambia linealmente entre las muestras.


Second Order Hold (SOH)

El Second Order Hold es una técnica más avanzada que utiliza un modelo parabólico para interpolar entre muestras. En lugar de una transición lineal, el SOH asume que la señal analógica sigue una curva parabólica entre dos puntos de muestreo.

en ambos casos es mas complicada tanto la programacion como el montaje, esto añadiendo dificultad y aumentando los costos en ptocesador para poder ejecutar correctamente estas interpolaciones. sin embargo, en ambos casos se obtiene una mejor codificacion y muestreo en la señal analoga por lo que generaria menos perdida de informacion.
# Ejercicios#

📚 Ejercicio 1:

Señal analógica: [1,2] V
Bits de representación: 3 bits
2^3 = 8 posibles símbolos
Rango analógico: 1,2 - 0 = 1,2 V
Representación: 1,2 / 8 = 0,15 V
En realidad, hay 2^(r-1) posibles símbolos porque un símbolo se usa para representar el 0 V
Ejemplo 2:

📚Ejercicio 2:
Señal analógica: [0,5] V
Bits de representación: 4 bits
2^4 = 16 posibles símbolos
Rango analógico: 0,5 - 0 = 0,5 V
Representación: 0,5 / 16 = 0,03125 V


## Conclusiones

En el control digital, se utilizan técnicas para convertir señales entre los dominios digital y analógico. El Zero-Order Hold (ZOH) es el método más simple, manteniendo constante el valor de la señal digital durante el intervalo de muestreo. El First Order Hold (FOH) mejora la suavidad de la señal analógica mediante una interpolación lineal entre muestras, mientras que el Second Order Hold (SOH) ofrece una mayor precisión al interpolar con una curva parabólica. Cada método tiene sus propias ventajas y aplicaciones, equilibrando complejidad, precisión y requisitos de procesamiento. En general, la elección del método depende de las necesidades específicas del sistema y de los recursos disponibles.


