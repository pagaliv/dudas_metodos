# Dudas Métodos

## Duda 1: Factorización LU con Doolittle

### Descripción

Para obtener la factorización LU usando el método de Doolittle para una matriz $A$ de $3 \times 3$, escribo de forma genérica las matrices $L$ y $U$ de la siguiente manera:

$$
L = \begin{bmatrix}
1 & 0 & 0 \\
l_{21} & 1 & 0 \\
l_{31} & l_{32} & 1
\end{bmatrix}
\quad
U = \begin{bmatrix}
u_{11} & u_{12} & u_{13} \\
0 & u_{22} & u_{23} \\
0 & 0 & u_{33}
\end{bmatrix}
$$

Luego calculo los elementos mediante: 

**Elementos de U:**
- $u_{11} = a_{11}$
- $u_{12} = a_{12}$
- $u_{13} = a_{13}$
- $u_{22} = a_{22} - l_{21}u_{12}$
- $u_{23} = a_{23} - l_{21}u_{13}$
- $u_{33} = a_{33} - (l_{31}u_{13} + l_{32}u_{23})$

**Elementos de L:**
- $l_{21} = \frac{a_{21}}{u_{11}}$
- $l_{31} = \frac{a_{31}}{u_{11}}$
- $l_{32} = \frac{a_{32} - l_{31}u_{12}}{u_{22}}$

### Mis dudas

1. **¿Este método es correcto?** Entiendo que sí, porque lo he usado y comprobado y es funcional. 

2. **¿Cómo adaptarlo a matrices más grandes que $3 \times 3$?** En la hoja 1 hay fórmulas generales, pero no sé cómo aplicarlas de forma práctica para obtener los valores específicos. 

---

## Duda 2: Factorización de Cholesky

### Descripción

En los apuntes se menciona que para evitar las raíces cuadradas (y así también los números irracionales), se puede usar la factorización $LDL^T$ en vez de $LL^T$. 

### Mis dudas

1. **¿Cómo obtener la factorización $LDL^T$?** No sé cómo implementar este método en la práctica.

2. **¿Cómo llegar a $LL^T$?** Yo hago algo similar al método anterior: obtengo los valores de $L$ multiplicándola por su traspuesta $L^T$ e igualando los resultados a los valores de $A$. Sin embargo, por lo que he visto en otros compañeros, hacen lo siguiente: 
   
   - Primero aplican **Doolittle** y obtienen $LU$
   - Luego descomponen:  $LU = LD \cdot D^{-1}U$
   - D = Matriz diagonal donde $d_{ii}$ = $\sqrt(u_{ii})$ ; $d_{if}=0$ siendo $i \neq f$
   - Definen:  $B = LD$ y $B^T = D^{-1}U$
   - Así obtienen:  $A = B \cdot B^T$
   - Y sobre $BB^T$ aplican **Cholesky**

   ¿Esta forma es la correcta o la unica correcta es la suya? , ¿sobre todo la duda radica en saber si $LDL^T$ en el examen sera la unica valida o si se podra hacer $LL^T$ y sobre el metodo de obtencion de $LL^T$ porque para 3x3 es factible mi metodo y para 4x4 aunque se haga un poco más largo también pero para n*n es inviable, por lo que no se si es del todo eficaz ?


---
## Duda 3

### Descripcion
En la hoja 3 de ejercicios hay una demostración que es el ejercicio 2, pide : Sea A no singular; A = LU = LDM con L y M triangulares inferiores con 1 en todos los valores de sus diagonales, D diagonal y A simetrica demostrar:

#### *Primero:* $M=L^T$ 
En esta parte creo no tener dudas, ya que: 
- A = LDM
- A = $A^T$ porque A es simetrica y D = $D^T$ al ser diagonal
- $A^T$ = $(LDM)^T$
- $(LDM)^T$ => $M^T$ $D^T$ $L^T$ => $M^T$ D $L^T$.
- A = $A^T$ = LDM =  $M^T$ D $L^T$
Por unicidad de factorización se deduce que
-  $M^T$ = L y $L^T$ = M, quedando demostrado que M= $L^T$ que es lo que inicialmente se queria demostrar

#### *Segundo: Si* $d_{ii}$ > 0 *entonces A def positiva*
En este si que tengo más dudas en alguno de los pasos, lo que entiendo para hacerlo es:
- Por definición A es def positiva si $x^tAx$ > 0; tomando x $\neq$ 0
- $x^tAx$ = $x^tLDL^t x$
- $L^t$ x=y, siendo y un vector **MI DUDA ES SI y $\neq$ 0 obligatoriamente**
- Suponiendo que y $\neq$ 0
- $L^t$ x=y => $x^tLDL^t x$ = $(x^tL)D(L^t x)$ = $y^tDy$ 
- al ser D diagonal: <br>
  $\sum_{i=1}^{n} d_{ii} * y^2_{i}$ = $y^tDy$ <br>
- suponiendo C implica que ese sumatorio > 0  **SEGUNDA DUDA, si y $\neq$ 0 significa que el sumario > 0 o \neq 0**
- si $y^tDy$ > 0 =>  $x^tAx$ > 0 y q.e.m. que A es definida postiva por definición

 ### *Tercero: Si A es definida positiva entonces* $d_{ii} > 0$ 
 En esta también tengo dudas
 - Para cada vector $e_{k}$ , toma $x=L^{-t}e_{k}$ => $xL^t=e_{k} **DUDA ESTO ES CIERTO?**
 - $x^tAx$ => $(L^{-t}e_{k})^t$ A $(L^{-t}e_{k})$
 - $(L^{-t}e_{k})^t$ = $e_{k}^t (L^{-t})^t$ => $(L^{-t})^t$ = $L^{-1}$ =>  $e_{k}^t L^{-1}$
 - $L^{-t}$ * $L^{t}$ = I
 - L * $L^{-1}$ = I
 - $(L^{-t}e_{k})^t$ A $(L^{-t}e_{k})$ =>  $(L^{-t}e_{k})^t$ LDL^t $(L^{-t}e_{k})$ = $e_{k}^t L^{-1} LDL^t (L^{-t}e_{k})$
 - $e_{k}^t (L^{-1} L)D(L^t L^{-t})e_{k}$ =  $e_{k}^t I D I e_{k}$ = $e_{k}^t D e_{k}$ = $d_{ii}$
 - $x^tAx$ = $d_{ii}$
 - $x^tAx$ >0 => $d_{ii}$ > 0, q.e.m
  ---
## Duda 4
### Descripción: En la hoja tres ejercicio 4 hay una matriz tridiagonal, en los apuntes no se menciona como resolverlas a parte de metodos normales pero al ser una matriz especial entiendo que se debe usar un metodo especial, en que he econtrado es el metodo del algoritmo de thomas que es una variante de una despejación gaussiana, basada en despejar $F_{n-1}$ con F_{n}, quedando al final solo $a_{n,n}$ y despejando desde ahí. Pero este metodo es iterativo y se necesitan n operaciones, no se si es el método adecuado.

### Cuestion: ¿Para despejar matrices tridiagonales se debe usar el metodo de Thomas?
## Notación

- $A$: matriz original
- $L$: matriz triangular inferior (lower)
- $U$: matriz triangular superior (upper)
- $D$: matriz diagonal
- $L^T$: traspuesta de $L$
- $A^{-1}$: inversa de $A$
---
## Duda 5
### Descripcion: En la hoja tres ejercicio 11 se habla del metodo de hauseholding y no lo he encontrado en los apuntes y las explicaciones que he encontrado en internet no las he entendido, como funciona este metodo exactamente. 
---
## Duda 6
### Descripcion : Para el metodo de sobre relajación la forma de carcular el w optimo es:
$\frac{2}{1+\sqrt{1-p(J^2)}}$
Siendo p(J) el radio espectral de la matriz de iteración de Jacobi
### Pregunta : ¿Esto es cierto? En tal caso de ser cierto, ¿Es util? ¿Cuando se pregunta si hay un w optimo lo que se pide es calcular esto?

## Duda 7
### Descripcion: ¿Que significa exactamente que una funcion sea contractiva? lo he leido varias veces y lo he intentado comprender. Por ejemplo el ejercicio 10 de la hoja 4 no entiendo como hacerlo.
## Duda 8
### Metodo de las potencias: Son dos dudas, la primera para calcular $λ_{1}$ se puede usar la formula $λ^{(n+1)}= \frac{y_{i}^{(n+1)}}{z_i^{(n)}}$ o debo usar el cociente de Rayleigh 

$$
λ^{(n+1)}= \frac{(y^{(n+1)})^T z^{(n)}}{(z^{(n)})^T z^{(n)}}
$$

¿En caso de valer la primera opción hay alguna forma de elegir un i sin calcularlos todos? A parte de tener ojo para que no sean valores que tienden a 0 obviamente.
---
## Duda Final 
### Descripción: Esto no es una duda persé, sino más bien una duda general de si he entendido bien todo lo que entra. Como yo he estudiando basandome en los apuntes y las hojas de ejercicios me voy a basar en ello.
### Temario Hoja 1 y 2
- error relativo y error absoluto
- Norma matricial 1,2, $\infty$
  1. $||A||_1 el maximo de la suma de columnas$
  2. $||A||_2 el \sqrt{p(A*A)}$
  3. $||A||_{\infty} el maximo de la suma de las filas$
  4. $||A||_F  el valor de la raiz cuadrada de la suma de los cuadrados de todo a_{ij}$
      
- Metodo de Gauss sin pivote
- Metodo de Gauss con pivote parcial : 
     En cada paso, antes de eliminar una columna, buscamos el elemento de mayor valor absoluto en la columna actual por debajo de la diagonal y intercambiamos filas para ponerlo en la posición pivote.
- Metodo de Gauss con pivote parcial escalado: Se basa en lo mismo que el anterior pero comparamos valores escalados: dividimos cada elemento de la columna por el máximo absoluto de su fila
### Temario Hoja 3
 - Descomposición LU /Doolittle basada en hacer: 

$$
L = \begin{bmatrix}
1 & 0 & 0 \\
l_{21} & 1 & 0 \\
l_{31} & l_{32} & 1
\end{bmatrix}
\quad
U = \begin{bmatrix}
u_{11} & u_{12} & u_{13} \\
0 & u_{22} & u_{23} \\
0 & 0 & u_{33}
\end{bmatrix}
$$

De tal forma que:

$$
L \cdot U = A
$$
- Metodo de Cholesky: Se puede aplicar para toda matriz hermetica y definida positiva.

   - De tal forma que:

$$
A = L \cdot L^T 
$$
$$
L = \begin{bmatrix}
l_{11} & 0 & 0 \\
l_{21} & 1 & 0 \\
l_{31} & l_{32} & l_{33}
\end{bmatrix}
\quad
U = \begin{bmatrix}
l_{11} & l_{21} & l_{31} \\
0 & l_{22} & l_{32} \\
0 & 0 & l_{33}
\end{bmatrix}
$$
- Metodo de Jacobi: se basa en calcular $x_{n+1}$ separar en la linea n $x_{n}$ , coger un valor inicial e ir iterando con estos valores.
- Metodo de Gauss Seidel, igual que Jacobi pero una vez obtenido um $x_{n+1}$ se usa este valor en los siguientes valores en vez de $x_{n}$
### Hoja 4
- Metodo de biseccion: basandose en el teorema de bolzano si hay un punto fijo entre [a,b] calcular $\frac{a}b$ = c y calcular si el punto fijo esta entre [a,c] o [c,b] y repetir el proceso las veces que se conside necesario.
- Metodo del punto fijo: teniendo f(x)=0 -> g(x)=x e iterar, hay que tener cuidado de que no diverja.
- Metodo de newton: similar al del punto fijo pero aplicando la siguiente función:

$$
x_{n+1} = x_{n} -  \frac{f(x_{n})}{f'(x_{n})}
$$
- Metodo de la regula falsi: También iterativo, pero ya sin derivar usando la siguiente formula:

$$
c=\frac{a \cdot f(b) - b \cdot f(a)}{f(b) - f(a)}
$$

Después se evalua c y dependiendo de si el punto fijo queda a la izquierda a la derecha se hace el mismo calculo con [a,c] o [c,b] 

- Metodo de la secante se hace aplicando la siguiete formula:

$$
x_{n+1} = x_{n} -f(x_{n}) \cdot \frac{x_{n} - x_{n-1}}{f(x_{n}) - f(x_{n-1})}
$$
- Probar convergencia de sucesiones
- Hallar puntos fijos
- Probar que las funciones son contractivas

### Hoja 5
- Metodo de las potencias para calcular el maximo valor propio si es unico usando:

$$ 
y^{(n+1)} = Az^{(n)}
$$

$$
z^{(n)} = \frac{y^{(n)}}{||y^{(n)}||}
$$

siendo $z^{(0)}$ un vector elegido arbitrarimente ||z|| $\neq$ 0 

Para calcular  $λ^{(n+1)}= \frac{y_{i}^{(n+1)}}{z_i^{(n)}}$ o  usar el cociente de Rayleigh 

$$
λ^{(n+1)}= \frac{(y^{(n+1)})^T z^{(n)}}{(z^{(n)})^T z^{(n)}}
$$

- Metodo de las potencias inversa
Similar al de las potencias pero para calcular el autovalro más pequeño.
Se resuelve $Ay^{(n+1)}=z^{(n)}$ para lo que se calcula el coeficiente de Rayleight

$$
μ^{(n+1)}= \frac{(y^{(n+1)})^T z^{(n)}}{(z^{(n)})^T z^{(n)}}
$$

aplicando despues $\frac{1}{μ^{(n+1)}} y para seguir iterando como en el metodo de las potencias 

$$
z^{(n)} = \frac{y^{(n)}}{||y^{(n)}||}
$$

- Metodo de las potencia inversa desplazada: Similar al metodo de la potencia inversa pero sirve para calcular el autovalor mas cercano a un d concreto, para usarlo hay que
1. Resolver el sistema

$$
(A-dI)y^{(n+1)} = z^{(n)}
$$

2. Calcular el cociente

$$
μ^{(n+1)}= \frac{(y^{(n+1)})^T z^{(n)}}{(z^{(n)})^T z^{(n)}}
$$

3. Calcular autovalor de A

   
$$
λ^{(n+1)}=d+\frac{1}{μ^{(n+1)}}
$$

4. Normalizar para obtener z

$$
z^{(n)} = \frac{y^{(n)}}{||y^{(n)}||}
$$

5. Parar si $|λ^{(n+1)} - λ^{(k)}|< ϵ$

- Metodo de Discos de Gerschgorin: El teorema de Gerschgorin es una herramienta geométrica para localizar los autovalores de una matriz en el plano complejo. No los calcula exactamente, pero da regiones donde deben estar. Este metodo sirve solo para matrices nxn.
El metodo consiste en calcular dos cosas, el centro y el radio.
El centro (C) es el valor de $a_{ii}$ y el radio (R) sera la suma del resto de valores.
El disco sera [C-R, C+R] y habra un disco por cada fila. 


