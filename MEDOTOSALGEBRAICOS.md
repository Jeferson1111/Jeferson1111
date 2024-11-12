
# Observadores de Estados y Error de Estado Estacionario

## Eliminación de error de estado estacionario

Un observador de estados es un algoritmo utilizado para estimar los estados internos de un sistema dinámico cuando estos no son directamente observables. Este es un concepto muy utilizado en el control moderno para sistemas donde solo algunas salidas son medibles, pero los estados no lo son, o no se pueden medir directamente.

En este contexto, uno de los problemas más comunes es el error de estado estacionario, que se refiere a la diferencia entre el estado estimado y el estado real cuando el sistema ha alcanzado un régimen estable o de equilibrio (estado estacionario). 

## segimiento integral

El problema de eliminación de error de estado estacionario en el contexto de un sistema con seguimiento integral, primero vamos a analizar cómo se integra el concepto de observadores de estado, error de estado estacionario, y finalmente cómo se puede eliminar este error usando una ley de control con un vector de ganancias  F  para la referencia.

### **Ecuaciones del Sistema en Discreto**

$$\[
x(k+1) = A x(k) + B u(k)
\]$$

$$\[
y(k) = C x(k)
\]$$


En este caso, se propone una ley de control que incluye un vector de ganancias F  para el seguimiento de la referencia.

$$\[
u(k) = -K x(k) + F r(k)
\]$$


K  es la matriz de ganancias del controlador.

x(k) es el vector de estados en el instante k.

r(k) es la referencia del sistema (puede ser una señal deseada que se desea seguir).

F es el vector de ganancias de referencia.


$$\[
x(k+1) = (A - B K) x(k) + B F r(k)
\]$$
$$\[
y(k) = CX(k) 
\]$$


### Nuevas ecuaciones de estados


   $$\[
   v(k+1) = v(k) + r(k) - y(k)
   \]$$
   
y(k) = C x(k)

v(k) es un vector auxiliar que parece estar relacionado con la referencia y la salida del sistema,
y(k) es la salida del sistema, dada por y(k) = C x(k), donde C es la matriz de observación.

se reemplaza 

$$\[
v(k+1) = v(k) + r(k) - C x(k)
\]$$

Combinando las ecuaciones

Ahora, tenemos dos ecuaciones que describen la dinámica del sistema. 


[x(k+1)/v(k+1)]=[A,0/-C,1][X(k)/v(k)]+[B/0]u(K)+[0/1]r

y(k)=[C,0][x(k)v(k)]


### seguimiento integral


La ley de control que se presenta es una combinación de un control por estado y un control integral. La entrada de control u se expresa como:

$$\[
u = -K x + K_i v
\]$$

 x es el vector de estado del sistema.
 
 K  es el vector de ganancias para la regulación de estados
 
$$K_i$$ es la ganancia para el seguimiento integral

 v  es el valor auxiliar que se ha introducido para manejar el seguimiento de la referencia.

Reescribiendo de forma matricial:


u=-[k-ki][x/v]

u=-ka xa


El vector  K  controla la dinámica del estado del sistema. Es de tamaño  n- 1  y se aplica directamente al estado  x(k)  del sistema. Esto regula cómo se comportan las variables de estado del sistema.

La ganancia  K_i es una constante que se aplica al valor v(k) , que es un valor auxiliar utilizado para seguir la referencia r(k) y eliminar el error de estado estacionario. El valor  v(k) acumula el error entre la referencia y la salida real, y  K_i controla cómo el sistema corrige este error.

reescribiendo el sistema con matrices apliadas:

$$X_{A}(k+1)=A_{a}X_{a}+B_{a}u+B_{r}r$$

$$y(k)=C_{a}X_{a}$$

aplicando la ley de control:

$$(k+1)=(A_{a}-B_{a}K_{a})X_{a}+B_{r}r$$

$$x(k+1)=A_{aLC}X_{a}+B_{r}r$$

### la Metodología de Diseño

1. Definir el sistema ampliado: Construir las matrices $$A_a$$, $$B_a$$, y $$C_a$$.
2. Calcular el vector $$K_a$$: Utilizar el método Acker o polos en lazo cerrado, para calcular el vector de ganancias  K_a que ubique los polos en las posiciones deseadas en el plano complejo.
3. Definir las ganancias K  y  K_i : Desglosar el vector de ganancias  K_a.
4. Implementar el esquema de control: Aplicar la ley de control  u(k) = -K x(k) + K_i v(k)  y controlar el sistema para eliminar el error de estado estacionario y asegurar un seguimiento preciso de la referencia.


💡 Ejemplo

 Diseñar un controlador por retroalimentación de estados que ubique los polos del sistema en z+0.35)^3y que 
realice seguimiento por medio de acción integral. Para el sistema con las siguientes matrices:

A=[-13,-5.84,5.78/-5.84,-16.26,-5.35/5.78,-5.35,-7.64]

B=[-1.2/0.71/1.63]

C=[0.48,1.3,0.72]

D=0;


Ampliar el Sistema con la Acción Integral



  - Matriz de transición ampliada $$\( A_a \)$$:

Aa=[-13,-5.84,5.78,0/-5.84,-16.26,-5.35,0/5.78,-5.35,-7.64,0/-0.48,-1.03,-0.72,1]

  - Matriz de entrada ampliada $$\( B_a \)$$:

Ba=[-1.2/0.71/1.63/0]

  - Matriz de salida ampliada $$\( C_a \)$$:

  Ca=[0.48,1.3,0.72,0]

- Calcular el Vector de Ganancias  K_a  Usando Ackermann o polos(polinomio deseado en lazo cerrado).


Queremos que los polos en lazo cerrado estén ubicados en \( z = -0.35 \) con multiplicidad 3. 

se calculan las ganancias $$\( K_a \)$$


se dividern las ganancias


4. Implementamos el esquema de control $$\( u(k) = -K x(k) + K_i v(k) \)$$ para lograr el seguimiento integral y eliminar el error de estado estacionario.


## Diseño de un Observador de Estados

Un observador de estados es una herramienta fundamental en sistemas de control cuando no es posible medir directamente todas las variables de estado del sistema. Los observadores permiten estimar estas variables no medibles a partir de las mediciones de salida disponibles y las entradas del sistema. Esta estimación de los estados es esencial para poder implementar un controlador por retroalimentación de estados, que requiere la medición o estimación de todas las variables de estado.

 **Consideraciones sobre los Observadores de Estados**

-Limitación del controlador por retroalimentación de estados:El diseño de un controlador por retroalimentación de estados requiere tener acceso a todas las variables de estado del sistema. Sin embargo, en muchos casos no es posible medir todas las variables de estado directamente, ya sea por limitaciones en los sensores, costo o complejidad.
   
Solución: el Observador de Estados.
   - Un observador de estados estima las variables de estado no medibles a partir de las mediciones de salida y las entradas del sistema. Esto permite la retroalimentación de todos los estados, incluso cuando algunos de ellos no son directamente accesibles.



### Modelo de Error de Estimación

Sea el sistema descrito por las siguientes ecuaciones en espacio de estados:

- Ecuaciones del sistema real:

$$\[
x(k+1) = A x(k) + B u(k)
\]$$

- Ecuaciones del observador de estados:

$$\[
\hat{x}(k+1) = A \hat{x}(k) + B y(k) + Kp \left( y(k) - C \hat{x}(k) \right)
\]$$

donde:
- $$\( x(k) \)$$ es el vector de estado real,
- $$\( \hat{x}(k) \)$$ es el vector de estado estimado,
- $$\( y(k) = C x(k) \)$$ es la salida del sistema,
- $$\( kp \)$$ es la matriz de ganancias del observador, que determinará cómo se corrige el error de estimación basado en la diferencia entre la salida medida $$\( y(k) \)$$ y la salida estimada $$\( C \hat{x}(k) \)$$.

El error de estimación se puede modelar de la siguiente manera:

$$\[
e(k+1) =A(x-\hat{x})
\]$$

Sustituyendo las ecuaciones de la dinámica del sistema real y el observador, obtenemos:


$$\[
e(k+1) = (A - KeC) e(k)
\]$$



## Metodología de Diseño de un Observador de Estados


1. Comprobar la Observabilidad del Sistema

2. Determinar los Coeficientes del Polinomio Característico (Lazo Abierto)


$$\[
\det(Z I - A) = Z^n + a_1 Z^{n-1} + \cdots + a_{n-1} Z + a_n
\]$$

Esto nos da los coeficientes del polinomio característico $$\( a_1, a_2, \dots, a_n \)$$.

3. Determinar la Matriz $$\( Q \)$$ del Observador

Para el diseño del observador, es importante definir la matriz $$\( Q \)$$. Si el sistema está en forma canónica observable, la matriz $$\( Q \)$$ será simplemente la matriz identidad $$\( I \)$$. Sin embargo, si el sistema no está en esta forma, se requiere una transformación adicional  Q=WV.

4. Determinar el Polinomio Deseado para el Observador

El siguiente paso es definir el polinomio deseado para el observador. Esto corresponde a la ubicación de los polos del observador. El polinomio deseado para el observador tendrá la forma:

$$\[
Z^n + \alpha_1 Z^{n-1} + \cdots + \alpha_{n-1} Z + \alpha_n
\]$$

Aquí, los coeficientes $$\( \alpha_1, \alpha_2, \dots, \alpha_n \)$$ corresponden a los polos deseados para el observador.

 5. Calcular la Matriz de Ganancias del Observador

$$Q^{-1}$$ [an-an]


💡 Ejemplo

Diseñar el observador de estados para el sistema:

A=[1.799,-0.8025/1,0]


B=[0.01563,0]


C=[0.01191,0,01107]

ubicando los polos del observador en:

z=-0.2  y  z=-0.2

-comprobando observabilidad

matriz de observabilidad

v=[0.0119,0.0111/0.0325,-0.0096]

determinante=-0.00004735  el sistema es observable

-se obtiene el polinomio caracteristico |zI-A|

|zI-A|=[z-1.799,0.8025/-1,z]

|zI-A|= $$z^{2}-(1.799z)+0.8025$$

a1=-1.799 y a2=0.8

-Determinar la matriz Q

Q=WV

W=[-1.799,1/1,0]

Q=[0.0111,-2.0295/0.0119,0.0111]

-Se obtiene el polinomio deseado

(z+0.2)(z+0.2)

$$z^{2}+0.4z+0.04$$

a1=0.4 y a2=0.04

-se calcula las ganancias del observador






### **Control por Retroalimentación de Estados**


El objetivo principal de esta estrategia es asignar los polos del sistema en lazo cerrado de forma arbitraria mediante la matriz de ganancias  K . Esto implica que se puede modificar el comportamiento dinámico del sistema (en términos de su estabilidad y respuesta) ajustando los valores de  K  de manera que los polos del sistema cerrado estén ubicados en posiciones deseadas en el plano complejo.

u(k)=-k*x(k)


### Metodología de Diseño de Control por Retroalimentación de Estados

Para diseñar un controlador de retroalimentación de estados, se sigue un proceso estructurado:

1. Comprobar la controlabilidad del sistema
2. Determinar los coeficientes del polinomio característico del sistema en lazo abierto:
   - El polinomio característico de un sistema es el determinante de $$\( ZI - A \)$$, donde  A  es la matriz del sistema. Este polinomio tiene la forma:
     \[
     $$\|ZI - A |= Z^n + a_1 Z^{n-1} + \dots + a_n
     \]$$
   
3. Determinar La matriz T.Se utiliza para transformar el sistema en forma canónica controlable. Si el sistema está en esta forma, entonces  T  será la matriz identidad  I . Si no,  T  se calcula a partir de la matriz de controlabilidad U y la matriz  W (T=UW).

4. Determinar el polinomio deseado. Este polinomio se obtiene a partir de la ubicación de los polos deseados. Por ejemplo, si queremos que los polos estén en \( z = -0.2 + j0.4 \), \( z = -0.2 - j0.4 \), y \( z = -0.02 \), podemos construir el polinomio deseado en lazo cerrado.

5. Calcular las ganancias de retroalimentación de estados. Las ganancias  K  se calculan resolviendo la diferencia entre el polinomio característico del sistema y el polinomio deseado. Las ganancias de retroalimentación de estados  K se pueden obtener usando la fórmula:
     $$\[
     K = [\alpha_n - a_n, \alpha_{n-1} - a_{n-1}, \dots, \alpha_1 - a_1] \cdot T^{-1}
     \]$$
     donde $$\( \alpha_i \)$$ son los coeficientes del polinomio deseado y $$\( a_i \)$$ los del polinomio del sistema.



💡 Ejemplo

Consideremos un sistema con las siguientes matrices:

A=[0,1,0/0,0,1/-1,-5,-6]

B=[0/0/1]

Queremos diseñar un controlador que ubique los polos del sistema cerrado en las siguientes posiciones:

z = -0.2 + j0.4

z = -0.2 - j0.4

z = -0.02


#### Comprobación de Controlabilidad

La matriz de controlabilidad  se calcula como:

$$U=[B,AB,A^2B]$$


La matriz de controlabilidad U es:

U=[0,0,1/0,1,-6/1,-6,31]

 el sistema es controlable.


#### Determinar el Polinomio Característico en Lazo Abierto

El polinomio característico del sistema se obtiene como:

$$\[
P(Z) = |ZI - A| = Z^3 + Z^2 + 5Z + 1
\]$$

Este es el polinomio característico en lazo abierto

#### Determinar la Matriz  T 

La matriz T  se construye usando los coeficientes del polinomio característico y la matriz de controlabilidad. Para este caso,  T  se construye con los coeficientes  a_1 = 6 ,  a_2 = 5 , y  a_3 = 1 .

W=[5,6,1/6,1,0/1,0,0]

T=I=[1,0,0/0,1,0/0,0,1]

#### Determinar el Polinomio Deseado

El polinomio deseado para el sistema cerrado con los polos en las ubicaciones deseadas 

$$\[
P_d(Z) = (Z + 0.2 - j0.4)(Z + 0.2 + j0.4)(Z + 0.02)
\]$$


$$\[
P_d(Z) = Z^3 + 0.402Z^2 + 0.2008Z + 0.0004
\]$$

#### Calcular las Ganancias de Retroalimentación de Estados**



$$\[
K = [\alpha_n - a_n, \alpha_{n-1} - a_{n-1}, \dots, \alpha_1 - a_1] \cdot T^{-1}
\]$$

Sustituyendo los coeficientes $$\( \alpha_i \$$ del polinomio deseado y los coeficientes $$\( a_i \)$$ del polinomio del sistema:

K=[0.0004-1,0.2008-5,0.402-6]=[-0.996,-4.799,-5.598]




# Ejercicios#

📚 Ejercicio 1:

tenemos el siguiente sistema:

A=[0,1,0/0,0,1/-3,-4,-5]

B=[0/0/1]


se tienen los siguentes polos

z = -1 

 z = -2
 
 z = -3 + j
 
 z = -3 - j
 

### **Paso 1: Comprobación de Controlabilidad**

La matriz de controlabilidad  U  se forma como:
$$\[
U = [B, AB, A^2B]
\]$$

Calculamos  AB :

AB=[0,1,0/0,0,1/-3,-4,-5][0/0/1]=[0,1,-5]

Se calcula $$\( A^2B \)$$

$$A^2B=[0,1,0/0,0,1/-3,-4,-5]^2[0/0/1]$$

$$A^2=[0,0,1/-3,-4,-5/15,17,21]$$

$$A^2B[[0,0,1/-3,-4,-5/15,17,21][0/0/1]=[1/-5/21]$$

$$A^2B=[1/-5/21]$$

U=[0,0,1/0,1,-5/1,-5,21]

La determinante de u

u=-1

es controlable.

### **Paso 2: Polinomio Característico en Lazo Abierto**

El polinomio característico del sistema es:
$$\[
P(z) =|zI - A|
\]$$

P=[z,-1,0/0,z,-1/3,4,z+5]

$$PD=Z^{3}+5Z^{2}+4Z+3$$




### **Paso 3: Determinar la Matriz  T **

Los coeficientes del polinomio en lazo abierto son $$\( a_1 = 5 \)$$, $$\( a_2 = 4 \)$$, y $$\( a_3 = 3 \)$$. La matriz $$\( T \)$$ es simplemente la matriz identidad en este caso, ya que el sistema está en forma controlable.


T = I = 

### **Paso 4: Determinar el Polinomio Deseado**


$$\[
P_d(z) = (z + 1)(z + 2)(z + 3 - j2)(z + 3 + j2)
\]$$



$$\[
P_d(z) = z^4 + 9z^3 + 30z^2 + 42z + 20
\]$$


### **Paso 5: Calcular las Ganancias de Retroalimentación de Estados  K **


k=[8,25,38,17]




📚Ejercicio 2:


Consideremos un sistema con las siguientes matrices \( A \) y \( B \):

A=[0,1,0/0,0,1/-6,-11,-6]

B=[0/0/1]

tenemos los polos:

z = -1 + j

 z = -1 - j
 
 z = -5

### **Paso 1: Comprobación de Controlabilidad**

U=[0,0,1/0,1,-6/1,-6,25]=-1


es controlable

### **Paso 2: Polinomio Característico en Lazo Abierto**

El polinomio característico del sistema es:
$$\[
P = z^3 + 6z^2 + 11z + 6
\]$$

### **Paso 3: Determinar la Matriz \( T \)**

T = I 

### **Paso 4: Determinar el Polinomio Deseado**

Los polos deseados son \( z = -1 \pm j2 \) y \( z = -5 \). El polinomio deseado es:

$$\[
P_d(z) = (z + 1 - j2)(z + 1 + j2)(z + 5)
\]$$

$$\[
P_d(z) = z^3 + 7z^2 + 12z + 10
\]$$

### **Paso 5: Calcular las Ganancias de Retroalimentación de Estados \( K \)**


k=[4,1,1]


# concluciones

Conclusión Final
Los ejercicios muestran cómo, utilizando la controlabilidad y el diseño del controlador por retroalimentación de estados, es posible modificar el comportamiento de un sistema dinámico, moviendo los polos del sistema cerrado a las ubicaciones deseadas. Esto permite que el sistema tenga la respuesta deseada en términos de estabilidad y tiempo de respuesta, lo cual es crucial en la práctica de sistemas de control.

La metodología que hemos seguido, que incluye la comprobación de controlabilidad, el cálculo del polinomio característico, y la determinación de las ganancias de retroalimentación, es una forma sistemática y eficiente de diseñar controladores para sistemas dinámicos.


