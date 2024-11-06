# Espacio de estados

El espacio de estados es una herramienta matemática fundamental en el análisis y diseño de sistemas dinámicos. A diferencia de la función de transferencia, que solo describe la relación entre la entrada y la salida de un sistema, el espacio de estados considera todas las variables internas del sistema. Esto permite una descripción más completa de su dinámica, ya que captura tanto el comportamiento pasado como el presente del sistema, proporcionando una visión más detallada de su evolución a lo largo del tiempo.

El espacio de estados describe un sistema dinámico mediante un conjunto de ecuaciones diferenciales o en diferencias, que representan cómo el estado del sistema evoluciona en el tiempo en función de las entradas y las condiciones iniciales. 


### Estado:
El estado de un sistema dinámico se refiere al conjunto de variables necesarias y suficientes para describir completamente el comportamiento del sistema en un instante de tiempo dado.

### Variables de Estado:
Las variables de estado son las variables que describen el estado de un sistema en un momento dado. Estas variables capturan la información esencial sobre el sistema y determinan su evolución futura. Dependiendo del sistema, las variables de estado pueden ser posiciones, velocidades, temperaturas, presiones, o cualquier otra magnitud relevante para el comportamiento dinámico del sistema.

No necesariamente medibles: Aunque las variables de estado son cruciales para entender la dinámica de un sistema, no siempre son directamente medibles. Por ejemplo, en un sistema de control de temperatura, la temperatura interna de un objeto podría ser una variable de estado, pero no siempre se puede medir directamente. En esos casos, se pueden usar estimadores o sensores indirectos.


### Ecuaciones de Estado:
Las ecuaciones de estado son las ecuaciones matemáticas que describen cómo evolucionan las variables de estado de un sistema a lo largo del tiempo. Estas ecuaciones se basan en las leyes que rigen el comportamiento dinámico del sistema y generalmente se expresan en una forma vectorial y matricial. 

La representación matemática del espacio de estados para un sistema dinámico puede expresarse mediante un conjunto de ecuaciones que describen la relación entre las entradas, las salidas y las variables de estado en función del tiempo o en función de un índice discreto $$\( k \)$$. 

En un sistema discreto de tiempo, los elementos clave son las *entradas*, las *salidas* y las *variables de estado*. La representación típica sigue la siguiente estructura:

La notación que mencionas describe las **entradas** de un sistema dinámico discreto de tiempo. En este contexto, las entradas se representan por el vector \( \mathbf{u}(k) \), y cada componente de este vector corresponde a una entrada diferente del sistema en el instante de tiempo \( k \).

### Entradas
$$\( u_1(k), u_2(k), u_3(k), \dots, u_r(k) \)$$ Estas son las señales de entrada al sistema en el tiempo discreto $$\( k \)$$. El índice $$\( k \)$$ indica que estamos trabajando con un sistema de tiempo discreto, y cada $$\( u_i(k) \)$$ es la entrada correspondiente a la $$\( i \)$$-ésima señal de entrada en el instante de tiempo $$\( k \)$$.


### Variables de Estado:
Las variables de estado $$\( x_1(k), x_2(k), \ldots, x_n(k) \)$$ representan el estado del sistema en el tiempo discreto $$\( k \)$$. Estas variables contienen toda la información necesaria para predecir el comportamiento futuro del sistema.


### Ecuaciones de Salida:
Las salidas del sistema $$\( y_1(k), y_2(k), \ldots, y_m(k) \)$$ están relacionadas con el estado y las entradas del sistema. La ecuación de salida es:




### Esquema General del Modelo:

El modelo de espacio de estados se expresa generalmente de la siguiente forma:

1. **Ecuación de Estado**:

$$X\left( k+1 \right)= AX(k)+Bu(k)$$

2. **Ecuación de Salida**:
 
$$y\left( k \right)= CX\left( X \right)+Du\left( k \right)$$

A es la matriz de estados
B es la matriz de entrada
C es la matriz de salida 
D es la matriz de transmision directa

💡 Ejemplo

$$y\left( k+2 \right)+y\left( k+1 \right)+0.16y\left( k \right)= 2u\left( k \right)$$

se despeja la maxima derivada:

$$y\left( k+2 \right)=-y\left( k+1 \right)-0.16y\left( k \right)+2u\left( k \right)$$

$$y(k)=X_{1}(k)$$

$$y\left( k+1 \right)=X_{1}\left( k+1 \right)=X_{2}(k)$$

$$y(k+2)=X_{2}(k+2)=-X_{2}(k)-0.16X_{1}(k)+2u(k)$$


$$\left[ X_{1}(k+1)/X_{2}(k+2) \right]=\left[ 0,1/-0.16,-1 \right]\left[ X_{1}(k)/X_{2} (k)\right]+\left[ 0/2 \right]u$$


$$y=\left[ 1/0 \right]\left[ X_{1}(k)/X_{2}(k) \right]+\left[ 0 \right]u$$





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


