# Controladores por Retroalimentación de Estados

## Controlabilidad y Observabilidad

**Controlabilidad**  
La controlabilidad se refiere a la capacidad de un sistema para ser manipulado o dirigido a cualquier estado deseado, utilizando el control adecuado.

Un sistema es controlable en un tiempo $$\( t_0 \)$$ si, desde cualquier estado inicial $$\( x(t_0) \)$$, se puede transferir a cualquier otro estado en un intervalo de tiempo finito.
  

#### Matriz de Controlabilidad

En sistemas discretos, el comportamiento del sistema es:

$$\[
x(k+1) = A x(k) + B u(k)
\]$$
$$\[
y(k) = C x(k) + D u(k)
\]$$

Donde:

$$\( x(k) \)$$ es el vector de estado en el tiempo $$\( k \)$$,

$$\( u(k) \)$$ es el vector de control en el tiempo $$\( k \)$$,

$$\( y(k) \$$) es la salida en el tiempo $$\( k \)$$,

$$\( A \)$$, $$\( B \)$$, y $$\( C \)$$ son matrices del sistema.

La matriz de controlabilidad se construye:

$$U=\left[ B,AB,A^{2}B,A^{3}B....A^{n-1}B \right]$$

Si el sistema es controlable, entonces el rango de la matriz de controlabilidad debe ser igual al número de variables de estado $$\( n \)$$ y el determinante de esta matriz debe ser diferente de cero. En otras palabras, si el sistema es controlable, el rango de U es igual a n.

💡 Ejemplo

A=[1.5,1/1,0]

B=[1/0]

y=[2,-1]



Queremos verificar si el sistema es controlable.

La matriz de controlabilidad  es:

U=[B,AB]

AB=[1.5,1/1,0][1/0]=[1.5/1]


U=[1,1.5/0,1]

Determinante de la matriz de controlabilidad

U=[1,1.5/0,1]=1


El determinante es 1, lo que es diferente de cero, lo que implica que el sistema es **controlable**.



**Observabilidad**

Se dice que un sistema es observable en el tiempo %%\( t_0 \)%% si, con el sistema en el estado $$X(t_{0})$$, es posible determinar dicho estado observando la salida durante un intervalo de tiempo finito.

En otras palabras, la observabilidad nos permite estimar cualquier variable de estado del sistema si conocemos sus entradas y salidas durante un período de tiempo. Esta propiedad es fundamental en el diseño de sistemas de control, como los controladores por retroalimentación de estados, ya que nos permite diseñar estimadores de estados cuando los estados no son directamente medibles.


#### Matriz de Observabilidad


V=[C/CA/CA^{2}...CA^{n-1}]

Donde n es el número de estados en el sistema.su determinante debe ser diferente de cero) para que el sistema sea observable.

 Si el rango de la matriz de observabilidad es igual al número de estados del sistema, entonces el sistema es observable.



💡 Ejemplo

se tiene un sistema con dos variables de estado y las siguientes matrices:


A=[1.5,1/1,0]

C=[2,-1]

la matriz de observabilidad es:

v=[C/CA]

CA=[2,-1][1.5,1/1,0]=[2,2]

V=[2,-1/2,2]

Determinante de la matriz de observabilidad

V=[2,-1/2,2]=6


 **el sistema es observable**.

### ¿Para qué sirven las condiciones de Controlabilidad y Observabilidad?

Las condiciones de controlabilidad y observabilidad son fundamentales en el diseño y análisis de sistemas de control. Estas condiciones no solo determinan si un sistema es manipulable o si sus estados pueden ser estimados con precisión, sino que también garantizan la existencia de soluciones factibles para los problemas de control.



## Control por retroalimentacion de estados



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



### **Ejemplo: Diseño del Controlador de Retroalimentación de Estados**

Consideremos un sistema con las siguientes matrices:

\[
A = \begin{bmatrix}
0 & 1 & 0 \\
0 & 0 & 1 \\
-1 & -5 & -6
\end{bmatrix}, \quad
B = \begin{bmatrix}
0 \\
0 \\
1
\end{bmatrix}
\]

Queremos diseñar un controlador que ubique los polos del sistema cerrado en las siguientes posiciones:

\[
z = -0.2 + j0.4, \quad z = -0.2 - j0.4, \quad z = -0.02
\]

#### **Paso 1: Comprobación de Controlabilidad**

La **matriz de controlabilidad** \( \mathcal{C} \) se calcula como:

\[
\mathcal{C} = \begin{bmatrix}
B & AB & A^2B
\end{bmatrix}
\]

Para el sistema dado, se calcula:

\[
AB = \begin{bmatrix} 0 & 1 & 0 \end{bmatrix} \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix} = \begin{bmatrix} 1 \\ 0 \\ -6 \end{bmatrix}
\]

\[
A^2B = \begin{bmatrix} 0 & 1 & 0 \\ 0 & 0 & 1 \\ -1 & -5 & -6 \end{bmatrix} \begin{bmatrix} 0 \\ 0 \\ 1 \end{bmatrix} = \begin{bmatrix} 0 \\ 1 \\ 6 \end{bmatrix}
\]

La matriz de controlabilidad \( \mathcal{C} \) es:

\[
\mathcal{C} = \begin{bmatrix}
0 & 1 & 0 \\
0 & 0 & 1 \\
1 & -6 & 6
\end{bmatrix}
\]

Comprobamos el rango de \( \mathcal{C} \). Si el rango es igual al número de estados del sistema (en este caso 3), el sistema es **controlable**.

En este caso, el rango de \( \mathcal{C} \) es 3, lo que significa que el sistema es controlable.

#### **Paso 2: Determinar el Polinomio Característico en Lazo Abierto**

El polinomio característico del sistema se obtiene como:

\[
P(\lambda) = \det(\lambda I - A) = \lambda^3 + 6\lambda^2 + 5\lambda + 1
\]

Este es el **polinomio característico en lazo abierto**.

#### **Paso 3: Determinar la Matriz \( T \)**

La matriz \( T \) se construye usando los coeficientes del polinomio característico y la matriz de controlabilidad. Para este caso, \( T \) se construye con los coeficientes \( a_1 = 6 \), \( a_2 = 5 \), y \( a_3 = 1 \), dando lugar a:

\[
T = \begin{bmatrix}
6 & 5 & 1 \\
5 & 6 & 1 \\
1 & 5 & 6
\end{bmatrix}
\]

#### **Paso 4: Determinar el Polinomio Deseado**

El polinomio deseado para el sistema cerrado con los polos en las ubicaciones deseadas \( z = -0.2 \pm j0.4 \) y \( z = -0.02 \) es:

\[
P_d(\lambda) = (\lambda + 0.2 - j0.4)(\lambda + 0.2 + j0.4)(\lambda + 0.02)
\]

Expandiendo este producto obtenemos el polinomio deseado:

\[
P_d(\lambda) = \lambda^3 + 0.402\lambda^2 + 0.2008\lambda + 0.0004
\]

#### **Paso 5: Calcular las Ganancias de Retroalimentación de Estados**

Finalmente, calculamos las ganancias de retroalimentación de estados \( K \) usando la relación:

\[
K = [\alpha_n - a_n, \alpha_{n-1} - a_{n-1}, \dots, \alpha_1 - a_1] \cdot T^{-1}
\]

Sustituyendo los coeficientes \( \alpha_i \) del polinomio deseado y los coeficientes \( a_i \) del polinomio del sistema:

\[
K = \begin{bmatrix}
0.004 - 1 \\
-1 - 5 \\
0.2008 - 5.6 \\
0.402 - 6
\end{bmatrix}
T^{-1}
\]

Calculando \( T^{-1} \) y obteniendo las ganancias \( K \), finalmente obtenemos:

\[
K = \begin{bmatrix} -0.996 & -4.799 & -5.598 \end{bmatrix}
\]

Estas son las ganancias de retroalimentación de estados que colocarán los polos del sistema cerrado en las ubicaciones deseadas.




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



