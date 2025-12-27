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

**Elementos de $U$:**
- $u_{11} = a_{11}$
- $u_{12} = a_{12}$
- $u_{13} = a_{13}$
- $u_{22} = a_{22} - l_{21}u_{12}$
- $u_{23} = a_{23} - l_{21}u_{13}$
- $u_{33} = a_{33} - (l_{31}u_{13} + l_{32}u_{23})$

**Elementos de $L$:**
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

#### *Primero: $M=L^T$* 
En esta parte creo no tener dudas, ya que: 
- A = LDM
- A = $A^T$ porque A es simetrica y D = $D^T$ al ser diagonal
- $A^T$ = $(LDM)^T$
- $(LDM)^T$ => $M^T$ $D^T$ $L^T$ => $M^T$ D $L^T$.
- A = $A^T$ = LDM =  $M^T$ D $L^T$
Por unicidad de factorización se deduce que
-  $M^T$ = L y $L^T$ = M, quedando demostrado que M= $L^T$ que es lo que inicialmente se queria demostrar

#### *Segundo: Si $d_{ii}$ > 0 entonces A def positiva*
En este si que tengo más dudas en alguno de los pasos, lo que entiendo para hacerlo es:
- Por definición A es def positiva si $x^tAx$ > 0; tomando x $\neq$ 0
- $x^tAx$ = $x^tLDL^t x$
- $L^t$ x=y, siendo y un vector **MI DUDA ES SI y $\neq$ 0 obligatoriamente**
- Suponiendo que y $\neq$ 0
- $L^t$ x=y => $x^tLDL^t x$ = $(x^tL)D(L^t x)$ 
---
## Notación

- $A$: matriz original
- $L$: matriz triangular inferior (lower)
- $U$: matriz triangular superior (upper)
- $D$: matriz diagonal
- $L^T$: traspuesta de $L$
- $A^{-1}$: inversa de $A$
