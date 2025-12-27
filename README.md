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

2. **¿Cómo adaptarlo a matrices más grandes que $3 \times 3$? ** En la hoja 1 hay fórmulas generales, pero no sé cómo aplicarlas de forma práctica para obtener los valores específicos. 

---

## Duda 2: Factorización de Cholesky

### Descripción

En los apuntes se menciona que para evitar las raíces cuadradas (y así también los números irracionales), se puede usar la factorización $LDL^T$ en vez de $LL^T$. 

### Mis dudas

1. **¿Cómo obtener la factorización $LDL^T$?** No sé cómo implementar este método en la práctica.

2. **¿Cómo llegar a $LL^T$?** Yo hago algo similar al método anterior: obtengo los valores de $L$ multiplicándola por su traspuesta $L^T$ e igualando los resultados a los valores de $A$. Sin embargo, por lo que he visto en otros compañeros, hacen lo siguiente: 
   
   - Primero aplican **Doolittle** y obtienen $LU$
   - Luego descomponen:  $LU = LD \cdot D^{-1}U$
   - Definen:  $B = LD$ y $B^T = D^{-1}U$
   - Así obtienen:  $A = B \cdot B^T$
   - Y sobre $BB^T$ aplican **Cholesky**

   ¿Es esta la forma correcta de conectar ambos métodos, sobre todo la duda radica en saber si $LDL^T$ en el examen sera la unica valida o si se podra hacer $LL^T$ y sobre el metodo de obtencion de $LL^T$ porque para 3x3 es factible mi metodo y para 4x4 aunque se haga un poco más largo también pero para n*n es inviable, por lo que no se si es del todo eficaz ?


---

## Notación

- $A$: matriz original
- $L$: matriz triangular inferior (lower)
- $U$: matriz triangular superior (upper)
- $D$: matriz diagonal
- $L^T$: traspuesta de $L$
- $A^{-1}$: inversa de $A$
