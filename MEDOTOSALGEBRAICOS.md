# Espacio de estados

El espacio de estados es una herramienta matemática fundamental en el análisis y diseño de sistemas dinámicos. A diferencia de la función de transferencia, que solo describe la relación entre la entrada y la salida de un sistema, el espacio de estados considera todas las variables internas del sistema. Esto permite una descripción más completa de su dinámica, ya que captura tanto el comportamiento pasado como el presente del sistema, proporcionando una visión más detallada de su evolución a lo largo del tiempo.

El espacio de estados describe un sistema dinámico mediante un conjunto de ecuaciones diferenciales o en diferencias, que representan cómo el estado del sistema evoluciona en el tiempo en función de las entradas y las condiciones iniciales. 

En su forma más general, el modelo en espacio de estados se puede escribir como:


### Explicación de los Conceptos en el Contexto del Espacio de Estados

En el contexto de los sistemas dinámicos, el **espacio de estados** es una representación poderosa y flexible para modelar y analizar el comportamiento de un sistema a lo largo del tiempo. A continuación, se desarrollan y amplían los conceptos que mencionas:


### Estado:
El estado de un sistema dinámico se refiere al conjunto de variables necesarias y suficientes para describir completamente el comportamiento del sistema en un instante de tiempo dado. Dicho de otra manera, el estado del sistema contiene toda la información que es necesaria para predecir su futuro comportamiento sin necesidad de conocer su historia previa.

- **Importancia del Estado**: El conocimiento del estado de un sistema permite determinar cómo se va a comportar el sistema en el futuro, si se conoce la entrada actual y las condiciones iniciales. Esto es fundamental en la teoría de control y en la simulación de sistemas.

---

### **Variables de Estado**:
Las **variables de estado** son las variables que describen el estado de un sistema en un momento dado. Estas variables capturan la **información esencial** sobre el sistema y determinan su evolución futura. Dependiendo del sistema, las variables de estado pueden ser posiciones, velocidades, temperaturas, presiones, o cualquier otra magnitud relevante para el comportamiento dinámico del sistema.

- **No necesariamente medibles**: Aunque las variables de estado son cruciales para entender la dinámica de un sistema, no siempre son directamente medibles. Por ejemplo, en un sistema de control de temperatura, la temperatura interna de un objeto podría ser una variable de estado, pero no siempre se puede medir directamente. En esos casos, se pueden usar estimadores o sensores indirectos.

- **Medición de variables de estado en control**: Aunque las variables de estado no deben ser necesariamente medibles, en muchos **métodos de control** basados en espacio de estados (como el **control por retroalimentación de estado** o **estimación de estado**), es crucial que las variables de estado sean **medibles** o, al menos, puedan ser estimadas a partir de las salidas del sistema. Esto es esencial para calcular las señales de control adecuadas.

---

### **Ecuaciones de Estado**:
Las **ecuaciones de estado** son las ecuaciones matemáticas que describen cómo evolucionan las variables de estado de un sistema a lo largo del tiempo. Estas ecuaciones se basan en las leyes que rigen el comportamiento dinámico del sistema y generalmente se expresan en una forma vectorial y matricial. 

En la representación estándar en espacio de estados, las ecuaciones de estado toman la forma de:

\[
\mathbf{\dot{x}}(t) = A \mathbf{x}(t) + B \mathbf{u}(t)
\]

\[
\mathbf{y}(t) = C \mathbf{x}(t) + D \mathbf{u}(t)
\]

Donde:

- \( \mathbf{x}(t) \) es el vector de variables de estado.
- \( \mathbf{u}(t) \) es el vector de entradas del sistema.
- \( \mathbf{y}(t) \) es el vector de salidas.
- Las matrices \( A \), \( B \), \( C \), y \( D \) son matrices que definen la dinámica y las interacciones entre el estado, las entradas y las salidas.

Las ecuaciones de estado constituyen un sistema de **ecuaciones diferenciales (o en diferencias en sistemas discretos)** que describen cómo las variables de estado cambian con el tiempo, en función de las entradas y de su propio comportamiento dinámico.







## Igualacion de modelo por metodos algebraicos
teniendo o sabiendo que G(Z) es la funcion de lazo abierto donde G(Z) es conocida y asi mismo conociendo la respuesta deseada que se representa en una funcion de transferencia de lazo cerrado Go(z) se puede realizar este metodo por igualacion de modelo para encontrar la fincion de transferencia del controladorC(z) para asegurar esa respuesta.

se asume que G y Go son funciones causales entonces:

$$G_{0}\left( S \right)= \frac{C\left( z \right)G\left( Z \right)}{1+C\left( z \right)G\left( Z \right)}$$

despejando para encontrar el valor del controlador se obtiene

$$C\left( Z \right)= \frac{G_{0}\left( Z \right)}{G\left( z \right)-G_{0}\left( Z \right)G\left( Z \right)}$$

NOTA: si se tiene polos fuera del circulo unitario o en z=-1, la retroalimentacion unitaria no puede ser implementada en cualquier $$G_{0}\left( Z \right)$$; debido a que los controladores podrian ser no implementables.

💡 Ejemplo

para la planta: $$G\left( Z \right)= \frac{0.01\left( Z+1 \right)}{Z^{2}-2.01Z+1}$$
obtener la funcion de transferencia en lazo cerrado con las condiciones:
-para hacer estable el sistema
-con respuesta subamortiguada
-sobreimpulso menor a 5%

se encuentra la funcion de transferencia en lazo cerrado:

$$G_{0}\left( Z \right)= \frac{0.009Z+0.008}{Z^{2}-1.801+0.818}$$

se remplaza en:
$$C\left( Z \right)= \frac{G_{0}\left( Z \right)}{G\left( z \right)-G_{0}\left( Z \right)G\left( Z \right)}$$

y se obtiene que la funcion de transferencia del controlador C(z) es:

$$C\left( Z \right)= \frac{0.934^{3}-1.004z^{2}-0.822z+0.973}{z^{3}-0.81z^{2}-z+0.81}$$


## Igualacion de coeficientes

Conociendo la funcion de lazo abierto G(z) y la ubicacion de los polos que se desean(se dan o se les coloca un valos aleatoreo donde se cancelen dendro del circulo unitario), se puede representar un polinomio caracteristico

💡 Ejemplo
diseñar un controlador de accion proporcional para los polos ubicados en lazo cerrado en:
P1=0.91+j0.23;P2=0.91-j0.23

$$G\left( Z \right)= \frac{0.0043}{Z^{2}-1.819Z+0.8187}$$

el polinomio caracteristico deseado en lazo cerrado es:

$$\left( z-0.91+j0.23 \right)\left( z-0.91-j0.23 \right)=z^{2}-1.82z+0.881$$

calculando la funcion de transferencia de lazo cerrado se obtine :

polinomio caracteriztico deseado: $$Z^{2}-1.82Z+0.881$$
polinomio caracterizrico lazo cerrado:  $$Z^{2}-1.819Z+0.8187+k*0.0043$$

al igualar los 2 polinomios y asi mismo sus coeficientes se evidencia que no se puede solucionar ya que no son iguales y no se pueden tampoco igualar.

Para poder solucionar esto se utiliza las funciones causales propias en donde se colocan mas variables al controlador para asi poder generar una mayor cantidad de incognitas en cada coeficiente para asi despejar un valor en el que puedan quedar igualados

NOTA: El orden C(z) debe ser 1 grado menOr con respecto a la planta en lazo abierto.

se utiliza el controlador con la siguiente funcion:

$$C(Z)=\frac{B_{0}+B_{1}Z}{A_{0}+A_{1}Z}$$

ahora el sistema es de tercer orden por eso se deben ubicar 3 polos
Z=0.91+j0.23
Z=0.91-j0.23
Z=0.91
reemplazando en

$$G_{0}\left( S \right)= \frac{C\left( z \right)G\left( Z \right)}{1+C\left( z \right)G\left( Z \right)}$$

se obtine:

$$G_{0}\left( z \right)=\frac{0.0043\left( B_{0}+B_{1}Z \right)}{A_{1}Z^{3}+Z^{2}\left( A_{0}-1.819A_{1} \right)\left(  +0.8187A_{1}-1.819A_{0}+0.0043BA_{1}\right)Z+0.8187A_{0}+0.0043B_{0}}$$

se igualan los polinomios caracteristicos  y se despejan las incognitas para asi encontrar el valor de la funcion de transferencia del controlador

al igualar y remplazar se encuentran A0-B0-A1-B1
A0=-0.911
A1=1
B0=-12.99
B1=14.23

El controlador seria:

$$C\left( Z \right)= \frac{B_{0}+B_{1}Z}{A_{0}+A_{1}Z}= \frac{-12.99+14.23Z}{-0.911+Z}$$


# Ejercicios#

📚 Ejercicio 1:



📚Ejercicio 2:


## Conclusiones

En el control digital, se utilizan técnicas para convertir señales entre los dominios digital y analógico. El Zero-Order Hold (ZOH) es el método más simple, manteniendo constante el valor de la señal digital durante el intervalo de muestreo. El First Order Hold (FOH) mejora la suavidad de la señal analógica mediante una interpolación lineal entre muestras, mientras que el Second Order Hold (SOH) ofrece una mayor precisión al interpolar con una curva parabólica. Cada método tiene sus propias ventajas y aplicaciones, equilibrando complejidad, precisión y requisitos de procesamiento. En general, la elección del método depende de las necesidades específicas del sistema y de los recursos disponibles.

