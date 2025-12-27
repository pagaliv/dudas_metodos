# Dudas Metodos
## Duda 1
### Descripcion : Dolitttle , Para obtener LU yo lo que hago es para A matriz 3x3 escribir de forma generica LU del estilo L= [1,0,0],[l21,1,0],[l31,l32,1] ; U= [u11,u12, u13] , [0,u22,u,23], [[0,0,u33] y multiplicar y despejar para obtener: 
u11= a11
u12 = a12
u13=a13
u22 = a22-l21u12
u23 = a23-l21u13
u33 = a33 - ( l31u13 - l32u23)

l21= a21/u11
l31 = a31/u11
l32 = (a32-l31u12)/u22

Mis dudas son dos, la primera, ¿este metodo es correcto? Entiendo que si, porque lo he usado y comprobado y es funcional y la segunda es enfocado a matrices mas grandes que 3*3, porque en la hoja 1 hay matrices 4*4, para lo que hice fue el mismo metodo pero 4*4, mi duda es si para matrices n*n hay un desarollo más eficaz ya que logro ver que hay un patron y en los apuntes hay un sumatorio pero no logro entenderlo bien del todo. 

## Duda 2
### Descripcion: Usar Cholesky, en los apuntes se habla de que para evitar las raices cuadradas y asi también los numeros irraciones usar LDL^T , en vez de LL^t, tengo dos dudas, la primera no se como se saca realmente D, porque compañeros a los que he pedido apuntes no las usan y en los apuntes no he encontrado el desarollo.
La segunda es sobre como llegar a LL^t, ya que yo hago parecido al anterior, obtengo los valores de L multiplicandola por su traspuesta e igualando los resultados a los valores de A, pero por lo que he visto en otros compañeros , hacen Dollitle y obtienen LU -> eso pasan a L D D^-1 U -> B= LD ; B^T = D^-1U -> B^B^T y ahi hacen Chelosky, me han dicho que su metodo es igual de valido que el mio pero no estoy seguro de como hacer su metodo ni si son igual de validos. 
