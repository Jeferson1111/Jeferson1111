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




## Espacio de estados a partir de funcion de transferencia

### Función de Transferencia:
se tiene una función de transferencia de un sistema en tiempo discreto:

$$\[
G(z) = \frac{b_0 z^n + b_1 z^{n-1} + \cdots + b_{n-1} z + b_n}{z^n + a_1 z^{n-1} + \cdots + a_{n-1} z + a_n}
\]$$

Donde:
$$\( b_0, b_1, \dots, b_n \$$ son los coeficientes del numerador (relacionados con las entradas del sistema).
 $$\( a_1, a_2, \dots, a_n \)$$ son los coeficientes del denominador (relacionados con las variables de estado del sistema).

es posible representar esta función de transferencia en una representación en espacio de estados de acuerdo con las dinámicas del sistema. Hay varias formas de representar el sistema en espacio de estados, y las tres formas más comunes son la forma canónica controlable, la forma canónica observable y la forma de Jordan.


### Forma Canónica Controlable

En la forma canónica controlable, el modelo en espacio de estados se diseña de manera que las entradas tengan la máxima influencia posible sobre las variables de estado.



### Forma Canónica Observable

En la forma canónica observable, el sistema se organiza de manera que las salidas tienen la máxima influencia posible sobre las variables de estado. La forma general es:

### Forma Canónica diagonal
Este metodo es usado si se conocen los polos de la funcion de transferencia y todos son diferentes



💡 Ejemplo
 Conversión de Función de Transferencia a Espacio de Estados:

Consideremos un sistema con la siguiente función de transferencia:

$$\[
G(z) = \frac{z + 1}{z^2 + 2z + 1}
\]$$

1. Denominador: El polinomio $$\( z^2 + 2z + 1 \)$$ corresponde a la dinámica del sistema, y lo podemos usar para construir las matrices \( A \) y \( B \).
   
2. Numerador: El polinomio $$\( z + 1 \)$$ se usa para definir las matrices \( C \) y \( D \), que describen cómo el estado y la entrada afectan la salida.

se identifican los coeficientes de la función de transferencia:

$$\[
G(z) = \frac{b_1 z + b_0}{z^2 + a_1 z + a_0}
\]$$


Entonces, $$\( a_1 = 2, a_0 = 1 \)$$ y $$\( b_1 = 1, b_0 = 1 \)$$.

ya depende de la forma que se utiliza se reemplaza los valores en las matrices.


## Raices del polinomio caracteristico

### calculo de los polos en el espacio de estados

se resta la matriz A a la matriz identidad ZI:

$$\left| zI-A \right|=0$$

a la matriz resultante se saca la determinante y esto nos da el polinomio caracteristico.
ya obteniendo este polinomio se pueden encontrar los polos.

## Espacio de estados a funcion de transferencia 


### Sistema en espacio de estados:

El sistema en el espacio de estados está dado por:

$$X\left( k+1 \right)= AX(k)+Bu(k)$$

$$y\left( k \right)= CX\left( X \right)+Du\left( k \right)$$


se aplicar la transformada  Z 

se despeja $$\frac{Y(z)}{U(z)}$$




$$\[
\frac{Y(z)}{U(z)} = C ((z I - A)^{-1} B) + D
\]$$





# Ejercicios#

📚 Ejercicio 1:

**Forma Canónica Controlable**

se tiene la funcion de transferencia:

$$\[
G(z) = \frac{z + 2}{z^2 + 3z + 2}
\]$$

se identifican los coeficientes

$$\[
G(z) = \frac{b_1 z + b_0}{z^2 + a_1 z + a_0}
\]$$


Los coeficientes del numerador son:

 $$\( b_1 = 1 \)$$
$$\( b_0 = 2 \)$$

Y los coeficientes del denominador son:

$$\( a_1 = 3 \)$$
$$\( a_0 = 2 \)$$

se escriben las matrices en forma canónica controlable

$$A=\left[ 0,1/-2,-3 \right]$$


$$B=\left[ 0/1 \right]$$


$$C=\left[ 2,1 \right]$$

$$D=0$$

 el modelo de espacio de estados en la forma canónica controlable es:


$$\left[ X_{1} (k+1)\right/X_{2}(k+2)]=\left[ 0,1/-2,-3 \right]\left[ X1(k)/X2(K) \right]+\left[ 0/1 \right]u(k)$$

$$y=\left[ 2,1 \right]\left[ X1(k)/X2(K) \right]$$




📚Ejercicio 2:

**Forma Canónica Observable**

tenemos la función de transferencia:

$$\[
G(z) = \frac{2z + 1}{z^2 + 4z + 3}
\]$$


Los coeficientes del numerador son:
$$\( b_1 = 2 \)$$
$$\( b_0 = 1 \)$$

Y los coeficientes del denominador son:
$$\( a_1 = 4 \)$$
$$\( a_0 = 3 \)$$

se escribe la matriz en la forma caonica observable



$$A=\left[ 0,-3/1,-4 \right]$$


$$B=\left[ 1/2 \right]$$


$$C=\left[ 0,1 \right]$$

$$D=0$$

 el modelo de espacio de estados en la forma canónica observable es:


$$\left[ X_{1} (k+1)\right/X_{2}(k+2)]=\left[ 0,-3/1,-4 \right]\left[ X1(k)/X2(K) \right]+\left[ 1/2 \right]u(k)$$

$$y=\left[ 0,1 \right]\left[ X1(k)/X2(K) \right]$$


# concluciones

El espacio de estados es una representación matemática fundamental para el análisis y diseño de sistemas dinámicos. A diferencia de la función de transferencia, que solo describe la relación entre la entrada y la salida del sistema, el espacio de estados ofrece una visión más completa al modelar explícitamente las variables internas del sistema, conocidas como estados.

El espacio de estados permite expresar los sistemas en términos de ecuaciones discretas o diferenciales, utilizando matrices que describen cómo los estados evolucionan en función de las entradas y cómo las salidas dependen de los estados. A través de estas matrices  A ,  B , C ,  D , se puede modelar completamente un sistema dinámico y analizar su estabilidad, controlabilidad y observabilidad, aspectos esenciales para el diseño de controladores avanzados, como los basados en retroalimentación de estados o el control óptimo.

Además, el proceso de convertir una función de transferencia a un modelo en espacio de estados es un paso fundamental en muchos enfoques de diseño de control, especialmente cuando se busca una representación más detallada que permita trabajar con los estados internos del sistema. Las formas canónicas como la controlable y la observable proporcionan distintas maneras de estructurar el sistema para facilitar su análisis y control, maximizando la influencia de las entradas sobre los estados o la observación de los estados desde las salidas.



