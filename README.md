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
*Conversión Analógico-Digital (CAD)*

La Conversión Analógico-Digital (CAD) es el proceso por el cual una señal de naturaleza analógica, continua y variable en el tiempo, se convierte en una señal digital, discreta y representada por una secuencia de bits (1 y 0). Este proceso es fundamental en la adquisición y procesamiento de datos en sistemas digitales.

*Características clave de la Conversión Analógico-Digital:*

1. *Muestreo*: La señal analógica se muestrea en intervalos regulares de tiempo.
2. *Cuantificación*: Los valores muestreados se convierten en valores discretos.
3. *Codificación*: Los valores discretos se representan como una secuencia de bits.

*Tipos de Conversión Analógico-Digital:*

1. *Conversión Analógico-Digital Directa*: La señal analógica se convierte directamente en una señal digital.
2. *Conversión Analógico-Digital por Integración*: La señal analógica se integra durante un período de tiempo antes de ser convertida en digital.

*Técnicas de Conversión Analógico-Digital:*

1. *Conversión por Escalera*: La señal analógica se compara con una escalera de voltaje.
2. *Conversión por Flash*: La señal analógica se compara con una serie de voltajes de referencia.
3. *Conversión por Sucesivos Aproximaciones*: La señal analógica se aproxima sucesivamente a un valor digital.

*Importancia de la Conversión Analógico-Digital:*

1. *Permite la adquisición y procesamiento de datos en sistemas digitales*.
2. *Mejora la precisión y exactitud en la medición*.
3. *Facilita la almacenamiento y transmisión de datos*.

*Aplicaciones de la Conversión Analógico-Digital:*

1. *Sistemas de control industrial*.
2. *Sistemas de comunicación*.
3. *Sistemas de medición y monitoreo*.
4. *Sistemas de audio y video digital*.

## 2. Definiciones
Utilice el símbolo '>' para crear bloques de texto. En la presente plantilla estas cajas están reservadas para resaltar las definiciones, las cuales deben ser breves, y la palabra o frase que se está definiendo debe estar en letra itálica. El inicio del bloque de texto debe realizarse con el emoji 🔑 .
>🔑 *Definición:* descripción precisa y clara del significado de una palabra, término, concepto o fenómeno. Es una explicación que establece los límites y el alcance de aquello que se está definiendo, aclarando su naturaleza, características esenciales y, en algunos casos, su relación con otros conceptos.

## 3. Subsecciones
Las subsecciones pueden utilizarse para sub dividir ciertos temas que se tienen en clases, por ejemplo si se está trabajandolos conversores D/A, puede ser necesario subdividir este en circuito de resistencias ponderadas y circuito de escalera R2R. 
### 3.1. Título de subsecciones
Para la creación de estas subsecciones debe utilizar un tamaño de letra más pequeño, por lo tanto utilice la etiqueta '###' 
### 3.2. Numeración de subsecciones
Siga la numeración de la sección seguida de un punto y luego el número de la subsección.

## 4. Ejemplos
Si en algún caso pretende dar un ejemplo explicativo ya sea a través de texto o através de ecuaciones matemáticos, utilizar la palabra 'Ejemplo' seguido de una numeración consecutiva dentro de la clase. Utilice el emoji 💡 antecediendo la palabra.

## 5. Ecuaciones
Para la edición de ecuaciones debe utilizar la etiqueta '$$' al comienzo y final de la ecuación para que la ecuación quede centrada ocupando una línea. Si se quiere que la ecuación quede integrada en el texto debe utilizar la etiqueta '$' al comienzo y final de la ecuación. Las ecuaciones pueden ser editadas utilizando el código LATEX, en el siguiente enlace encuentran un editor de ecuaciones que les genera el código. http://www.alciro.org/tools/matematicas/editor-ecuaciones.jsp . Sin embargo hay muchas otras herramientas que pueden utilizar para esto.

💡**Ejemplo 1:** si se va a representar la ecuación de la ley de Ohm se puede mostrar así $R=\frac{V}{I}$ o también,

$$R=\frac{V}{I}$$

## 6. Figuras
Todas las figuras que incluya deben ser generadas por ustedes, **no utilizar las figuras de las presentaciones**. Para incluir figuras puede seguir los siguientes pasos:
* Primero escribimos ![]().
* Después escribimos, dentro de los corchetes, el texto alternativo. Este es opcional y solo entra en acción cuando no se puede cargar la imagen correctamente.
* Después escribimos, dentro de los paréntesis, la ubicación del archivo (ya sea una url o una ubicación dentro de algun folder local). Se recomienda poner las imágenes en una carpeta que se llame imágenes dentro del repositorio github para que no tengan problemas al cargar las imágenes.

💡**Ejemplo 2:**

![Figura de prueba](images/plantilla/Captura2.PNG)

Figura 1. Figura de prueba

Incluya la respectiva etiqueta a modo de descripción de la figura y mantenga numeración consecutiva para todas las figuras de la clase.

## 7. Tablas
En caso de necesitar la inclusión de tablas para organizar información se recomienda el uso de la herramienta del siguiente enlace https://www.tablesgenerator.com/markdown_tables , la cual permite organizar la información dentro de la tabla y genera el código markdown automáticamente:

💡**Ejemplo 3:** 

| **Resultado** | **x = número de intentos hasta primer éxito** |
|---------------|-----------------------------------------------|
|       S       |                       1                       |
|       FS      |                       2                       |
|      FFS      |                       3                       |
|      ...      |                      ...                      |
|    FFFFFFS    |                       7                       |
|      ...      |                      ...                      |

Tabla 1. Tabla de ejemplo

Cada tabla debe llevar la etiqueta que describa su contenido y numeración consecutiva para todas las tablas

## 8. Código
Teniendo en cuenta que el curso requiere del desarrollo de código matlab, c, c++ u otro. Si requiere incluir pequeños segmentos de código en los apuntes hágalos de la siguiente manera:

💡**Ejemplo 4:**
```
var sumar2 = function(numero) {
  return numero + 2;
}
```

## 9. Ejercicios
Deben agregar 2 ejercicios con su respectiva solución, referentes a los temas tratados en cada una de las clases. Para agregar estos, utilice la etiqueta #, es decir como un nuevo título dentro de la clase con la palabra 'Ejercicios'. Cada uno de los ejercicios debe estar numerado y con su respectiva solución inmediatamente despues del enunciado. Antes del subtitulo de cada ejercicio incluya el emoji 📚

## 10. Conclusiones
Agregue unas breves conclusiones sobre los temas trabajados en cada clase, puede ser a modo de resumen de lo trabajado o a indicando lo aprendido en cada clase

## 11. Referencias
Agregue un subtítulo al final donde pueda 
