# Metodos algebraicos
estos metodos son utilizados para para obtener un determinado comportamiento en un sistema de lazo cerrado, esto se logra mediante metodos algebraicos en donde la solucion a ellos es encontrar el valor de un controlador.
para obtener un resultado a este metodo la base fundamental es modificar la funcion de transferencia en lazo cerrado para asi encontras la respuesta deseada.

existen ods enfoques:
1.por igualacion de modelo
2. por igualacion de coeficientes
   
r->(|c(z)->G(z)->|Go(z))y
         
   
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


