# Procesos estocásticos

En este capítulo abordaremos el concepto básico de proceso estocástico,
concepto usado como instrumento para diseñar modelos probabilísticos de
sistemas, cuyo estado está sujeto a evolucionar en el transcurso del
tiempo. El capítulo inicia con una breve introducción y ejemplos de
procesos estocásticos. Seguido, presentaremos una clasificación de los
diferentes tipos de procesos estocásticos y algunos elementos útiles
para su caracterización. Finalmente, ilustramos una aproximación al
concepto de memoria asociado a un proceso estocástico, así como la
definición de homogeneidad en el tiempo.

## Introducción

Consideremos un fenómeno aleatorio, o un sistema con aspectos de
aleatoriedad, y se contempla un elemento observable del fenómeno que
pueda caracterizarse de manera probabilística. Supongamos que los
valores posibles de la observación conforman un conjunto $S$ de tipo 
discreto (finito o contable).

Si se observa ese mismo fenómeno aleatorio de forma reiterada, por
ejemplo, cada minuto durante un cierto intervalo de tiempo, se obtiene
una secuencia ordenada de observaciones en el tiempo, que podemos
denotar como $\{ X_{n},n \geq 0\}$. Esta secuencia ordenada es un
ejemplo de ***proceso estocástico***. El resultado de cada observación
pertenece al conjunto $S$ (definido anteriormente), y en realidad es
predecible sólo en términos probabilísticos, es decir $X_{n}$ es una
variable aleatoria por cada valor de $n$.

### **Ejemplo 1:**
```{admonition} Ejemplo 1
:class: suggestion

-   **Fenómeno aleatorio:** Juego de póker en un casino
    durante un número de rondas.

-   **Variable de interés:** Nos enfocamos en la cantidad
    $D_{n}$ de dinero de un jugador particular.

-   **Conjunto de observación:** Observamos dicha cantidad
    después de cada ronda $n\ $del juego.

```

No se puede predecir con exactitud la cantidad de dinero del jugador,
pero sí es posible determinar la probabilidad de que sea igual a un
determinado monto. Es decir, es posible realizar una predicción de dicha
cantidad en términos probabilísticos. Si denotamos con $D_{n}$ la
cantidad de dinero que el jugador posee al terminar la ronda $n$, siendo
$D_{0}$ la cantidad inicial antes de empezar a jugar, entonces
$\{ D_{n},n \geq 0\}$ es un proceso estocástico.


```{admonition} Nota
:class: warning
El uso de $\mathbf{X,\ D}$ o $\mathbf{n}$ en la notación
$\mathbf{\{}\mathbf{X}_{\mathbf{n}}\mathbf{,n \geq 0\}}$ no es
obligatorio.
```

No puede faltar en la definición de un proceso estocástico la
especificación de la *variable de estado*. En el ejemplo del caso
anterior:

```{admonition} Ejemplo 1: Variable de Estado
:class: suggestion
- $D_{n}$ $≝$ Cantidad de dinero que el jugador posee al terminar la ronda
    $n$ del juego
```

Es importante observar que a partir del mismo fenómeno aleatorio se
pueden definir múltiples procesos estocásticos, por ejemplo, al variar
el elemento observable o la temporalidad de observación. En el caso del
Ejemplo 1, si se observa la cantidad total de dinero apostado por todos
los jugadores en cada ronda, denotada como $T_{n}$, habríamos definido
otro proceso estocástico $\{ T_{n},n \geq 0\}$ .

### **Ejemplo 2:**
```{admonition} Ejemplo 2
:class: suggestion

-   **Fenómeno aleatorio:** Llegadas de un carro a un parqueadero

-   **Variable de interés:** Se busca medir el número de carros en 
    el sistema (parqueadero).

-   **Conjunto de observación:** La observación se realiza cada vez 
    que un carro llega al parqueadero.

```

En este caso la variable de estado se puede definir como:

```{admonition} Ejemplo 2: Variable de Interés 1
:class: suggestion

-   $C_{n}$ $≝$ Número de carros en el parqueadero en el momento
    inmediatamente después de la llegada del carro $n$-ésimo

```


 
 
Para el ejemplo anterior, otra variable de interés podría ser el tiempo
que pasa entre llegadas consecutivas al parqueadero. Por ejemplo,
consideremos la siguiente variable:
 
```{admonition} Ejemplo 2: Variable de Interés 2
:class: suggestion

-   $I_{n}$ $≝$ Tiempo entre la llegada del carro $n$-ésimo y el carro
    $n + 1$-ésimo al parqueadero

```


 
Esta secuencia de observaciones definiría un proceso estocástico
$\{ I_{n},n \geq 0\}$, donde los posibles valores que toma la variable
son tiempos, es decir, números reales no-negativos.
 
 
También, es posible observar un sistema en tiempo continuo, es decir en
cada instante de tiempo, sin precisar la secuencia de instantes en la
cual se realiza el muestreo (observación) de la variable de interés. En
el caso del Ejemplo 2 podríamos por ejemplo definir:
 
```{admonition} Ejemplo: Variable de Interés Tiempo Continuo
:class: suggestion

-   $C(t)$ $≝$ Número de carros en el parqueadero en el instante de tiempo
$t$

```

 
En este caso nos interesa observar esta variable continuamente, en todo
tiempo $t \geq 0$, y no solo en momentos discretos del tiempo. El
conjunto de observaciones sería $\{ C(t),t \geq 0\}$, que constituye un
proceso estocástico que evoluciona en tiempo continuo.
 
 
Las definiciones de la variable de interés y la temporalidad de
observación hacen parte del proceso de modelado de un sistema. Si bien,
en algunos casos tales definiciones pueden ser obviamente determinadas
por la naturaleza del sistema, en general existen múltiples opciones de
modelado, por lo cual es esencial tener en cuenta el objetivo del
estudio del sistema.
 

## Caracterización de los procesos estocásticos 
 
Con el objetivo de proporcionar elementos útiles para el estudio de
sistemas estocásticos que evolucionan en el tiempo, en esta sección
plantearemos una formalización y una posible clasificación de los
procesos estocásticos.
 
 
Una definición muy abstracta de proceso estocástico afirma que: "*Un
proceso estocástico es una familia indexada de variables aleatorias",*
la cual se comprende como mayor facilidad si se substituyen las palabras
*familia indexada* por *secuencia ordenada*. Como tal, los procesos
estocásticos son objeto de estudio teórico de las matemáticas y de la
probabilidad aplicada. Sin embargo, sus áreas de aplicación son
múltiples en las ciencias aplicadas como la física, la ingeniería,
medicina e incluso en ciencias sociales, ya que se prestan para el
modelado de sistemas muy diferentes con el objetivo de medir su
rendimiento y tomar decisiones sin influir directamente en él.
 
 
La palabra *estocástico* fue introducida en tiempos bastante recientes
por L. Bortkiewcz, quien la utilizó en 1917 para definir fenómenos que
incluyen aspectos probabilísticos. Por otra parte, la terminología
*proceso estocástico,* así como la entendemos hoy fue presentada por el
matemático ruso A. Kolmogorov en 1932. La definición de un proceso
estocástico deja libertad en cuanto a la selección de la variable de
interés y a la frecuencia de observación; como consecuencia, existen
muchos tipos de procesos estocásticos. Entre los más conocidos, se
pueden encontrar procesos de conteo, movimientos Brownianos, cadenas de
Markov, procesos de Martingala, procesos de Levy, procesos Gaussianos,
entre otros.
 
 
Consideramos una colección ordenada de variables aleatorias, es decir un
proceso estocástico, y definimos la siguiente terminología; llamaremos
*estado* del proceso estocástico a un valor particular que puede tomar
la variable que se observa, y *espacio de estados* al conjunto de todos
los posibles estados de la variable, lo cual se denota usualmente con
$S$.
 
 
Como se mencionó, en un proceso estocástico solo conocemos el estado del
sistema de forma probabilística. Así, estamos interesados en conocer la
distribución de probabilidad de la variable de interés en un momento del
tiempo. Por ejemplo, para el proceso estocástico
$\left\{ X_{n},n \geq 0 \right\}$, es pertinente preguntar cuál es la
probabilidad $P\left\lbrack X_{5} = x \right\rbrack$, es decir, la
probabilidad de que en el momento $n = 5$ de observación la variable de
estado $X_{5}$ tome el valor $x$, donde $x$ es un valor posible del
estado del proceso, es decir $x\ \epsilon\ S$.También podemos estar
interesados en la probabilidad de que esta variable en el momento
$n = 5$ tome valores menores o iguales a $x$, es decir
$P\lbrack X_{5} \leq x\rbrack$. Por ejemplo, la probabilidad de que el
monto total de dinero apostado en la quinta ronda del juego de póker sea
35,000 pesos, $P\lbrack T_{5} = 35,000\rbrack$, o que sea a lo sumo
20,000 pesos, $P\lbrack T_{5} \leq 20,000\rbrack$.
 
 
Dada la disponibilidad de múltiples observaciones en un proceso
estocástico, surgen otro tipo de preguntas interesantes, cuya respuesta
puede proporcionar información útil para el análisis de los sistemas que
se quieren estudiar a través del modelado. Por ejemplo, la probabilidad
de que el número de carros en el parqueadero a las 9 de la mañana sea
10, dado que a las 8 de la mañana era igual a 5. Esta probabilidad
condicional se describiría en notación matemática como
$P\left\lbrack C(9AM) = 10\  \right|\ C(8AM) = 5\rbrack$.
 
 
También pueden existir preguntas interesantes que involucran las
distribuciones conjuntas de un proceso estocástico. Por ejemplo, si
estuviéramos interesados en la probabilidad de que los primeros tres
tiempos entre llegadas al parqueadero fuesen menores a una cantidad fija
$\tau$, tendríamos que calcular la siguiente
probabilidad$\ P\lbrack I_{1} < \tau,\ I_{2} < \tau,I_{3} < \tau\rbrack$.
 
 
En general, la caracterización de un proceso estocástico requiere
información sobre las distribuciones de probabilidad condicionales,
marginales y conjuntas de las variables aleatorias que conforman el
proceso estocástico. Como veremos en el capítulo siguiente, en algunos
casos específicos dicha caracterización puede simplificarse
considerablemente.
 

## Clasificación de los procesos estocásticos 

 
Una clasificación muy general de los procesos estocásticos es aquella
que considera las posibles tipologías de dos características claves del
proceso. La primera es el espacio de estados $S$, el cual puede ser
discreto o continuo. La segunda es el conjunto de índices, referido al
conjunto que define las observaciones del fenómeno aleatorio al que
denotaremos como $I,$ el cual puede ser discreto o continuo.
 
 
Al definir una variable de interés $X$ que toma valores en un espacio de
estados $S$, y la cual observamos en instantes de tiempo definidos por
un conjunto de índices $I$, tendremos una primera clasificación del
proceso estocástico. Si el espacio de estados $S$ es un conjunto
discreto/continuo, diremos que el proceso estocástico tiene *espacio
discreto/continuo*. Si el conjunto de índices $I$ es un conjunto
discreto/continuo, diremos que el proceso estocástico es en *tiempo
discreto/continuo*.
 
 
Tal como se resume en la Figura 1, la combinación de las diferentes
posibilidades hace que puedan definirse cuatro diferentes tipos de
procesos estocásticos.

<style>
    table, th, td{
        border: 1px solid red;
        text-align: center;
        padding: 3px 6px
    }

    .rotate{
        writing-mode: vertical-lr;
        transform: rotate(180deg);
        white-space: nowrap;
    }
</style>

<table>
  <thead>
    <tr>
      <th colspan = "2"></th>
      <!-- <th> Lorem, ipsum dolor. </th> -->
      <th colspan = "2"> Índices de Observación </th>
      <!-- <th > Lorem, ipsum dolor. </th> -->
    </tr>
  </thead>
  <tbody>
    <tr>
      <td colspan = "2"></td>
      <!-- <td></td> -->
      <td>Discreto</td>
      <td>Continuo</td>
    </tr>
    <tr>
      <td rowspan = "2" class="rotate"><b>Espacio de Estados</b></td>
      <td class="rotate">Discreto</td>
      <td>Espacio discreto <br>
      Tiempo discreto</td>
      <td>Espacio discreto <br>
      Tiempo discreto</td>
    </tr>
    <tr>
      <!-- <td>9</td> -->
      <td class="rotate">Continuo</td>
      <td>Espacio discreto <br>
      Tiempo discreto</td>
      <td>Espacio continuo <br>
      Tiempo continuo</td>
    </tr>
  </tbody>
</table>

<div style="text-align:center">
    <b><i>Figura 1: Tipos de procesos estocásticos </i></b>
</div>


`````{admonition} EJERCICIO
:class: tip
Clasifique cada uno de los procesos estocásticos introducidos
en la Sección 1.1.
`````



Los procesos estocásticos de tiempo discreto y continuo se denotan de
forma diferente debido a la naturaleza del conjunto de índices. En
particular, los procesos de tiempo discreto se denotan como
$\{ X_{n},n \geq 0\}$, es decir, el tiempo discreto aparece como un
sub-índice de la variable, mientras que los procesos de tiempo continuo
se denotan como $\{ X(t),t \geq 0\}$, es decir, el índice tiempo aparece
como argumento de la variable de estado $X$.

Es importante resaltar que la definición de la variable de estado de un
proceso en tiempo continuo es usualmente más sencilla que la definición
de la variable de estado para un proceso de tiempo discreto. Por
ejemplo, supongamos que nos interese analizar la efectividad de una
política de inventario de un almacén. La variable que queremos observar
y predecir es entonces $N$, el número de unidades en inventario. Si
quisiéramos modelar el sistema con un proceso estocástico en tiempo
continuo, deberíamos sencillamente definir la variable de estado como:

```{admonition} Ejemplo: Inventario Tiempo Continuo (Variable de Interés)
:class: suggestion

-   $N(t)$ $≝$ Número de unidades de producto en el inventario en el
instante de tiempo $t$.
```

Para todo proceso estocástico en tiempo continuo el conjunto de índices
siempre es igual al semieje positivo, y por ende la definición de la
variable de estado sólo necesita especificar que se observa el sistema
en cada posible valor del tiempo $t$.

Puede que sea posible, conocer el estado del sistema en cada momento del
tiempo, pero esto puede no ser relevante/necesario. Quizá sea importante
conocerlo al momento de la apertura del almacén, o los viernes a la hora
del cierre, o solo en aquellos momentos en los cuales se pueden realizar
órdenes para reabastecerlo. En todos estos casos, el conjunto de índices
es discreto, y existen infinitas posibilidades de observar el sistema en
un subconjunto de momentos en el tiempo. Por esta razón, es fundamental
definir de manera concisa, pero completa, la variable de estado. Por
ejemplo, para las tres opciones mencionadas arriba:

```{admonition} Ejemplo: Inventario Tiempo Discreto (Variables de Interés)
:class: suggestion

-   $N_{n}^{1}$ $≝$ Número de unidades en inventario a la hora de abrir el
almacén el día $n$

-   $N_{n}^{2}$ $≝$ Número de unidades en inventario a la hora del cierre el
viernes de la semana $n$

-   $N_{n}^{3}$ $≝$ Número de unidades en inventario en el $n$-ésimo momento
de solicitar la provisión

```

Notamos cómo el índice $n$ en la definición de la variable de estado es
utilizado para especificar un elemento preciso de la secuencia temporal
dentro del conjunto de observaciones $I$. También, es interesante notar
que la periodicidad de las observaciones en la **opción 1** es diaria, en la
**opción 2** es semanal y en la **opción 3** queda definida por una secuencia de
eventos externos determinada por la disponibilidad de los proveedores
para recibir solicitudes.

Los procesos estocásticos en tiempo discreto proveen mucha flexibilidad
a la hora de modelar sistemas. La definición de la variable de estado
tiene que ser suficientemente detallada para que especifique exactamente
la selección de la secuencia de índices.

## Dependencias entre observaciones en los procesos estocásticos

Considere el siguiente fenómeno aleatorio: se lanza un dado, y se define
como variable de interés la cara del dado $(D)$. Si repetimos el
experimento, podemos definir el proceso estocástico
$\left\{ D_{n},n \geq 0 \right\}\ $con espacio de estados discreto
$S = \left\{ 1,2,\ldots,6 \right\}\ $y en tiempo discreto, donde se
define:

```{admonition} Ejemplo: Dados (Variable de Interés)
:class: suggestion

-   $D_{n}$ $≝$ Cara que se obtiene en el $n$-ésimo lanzamiento del dado
```

Este proceso estocástico tiene propiedades de independencia muy fuertes,
las cuales aseguran que el valor observado en el $n -$ésimo lanzamiento
no es afectado por los resultados de los lanzamientos anteriores. En
otras palabras, conocer el resultado de los lanzamientos que ocurrieron
en el pasado no nos proporciona ninguna información sobre el resultado
del próximo resultado. Podemos escribir en forma matemática esta
propiedad de la siguiente manera:

> $P\left\lbrack D_{n} = i \middle| D_{n - 1} = i_{n - 1},D_{n - 2} = i_{n - 2},\ldots,D_{1} = i_{1} \right\rbrack = P\left\lbrack D_{n} = i \right\rbrack = \frac{1}{6}$,

Es decir, la probabilidad de observar un valor $i\ \epsilon\ S$ en el
n-ésimo lanzamiento, dada toda la historia de resultados desde el primer
lanzamiento hasta el n-1-ésimo, es simplemente igual a $\frac{1}{6}$,
sin importar $i_{n - 1},i_{n - 2},\ldots,\ i_{1}$ los resultados que se
obtuvieron en los lanzamientos $n - 1,n - 2,\ldots,\ 1$,
respectivamente.

Consideramos ahora el proceso estocástico
$\left\{ Z(t),t \geq 0 \right\}$, que modela el valor de mercado de un
producto en el tiempo $t$. En este caso, esperamos que este proceso
estocástico, con espacio continuo y en tiempo continuo, no posee las
propiedades de independencia del proceso anterior. Por ejemplo, si el
precio del producto en el tiempo $t$ es $z$, en un intervalo de tiempo
$\lbrack t,t + \delta\rbrack$ con $\delta \approx 0$, es de esperar que
el precio se mantenga cercano a $z$ con alta probabilidad. Entonces,
para este proceso estocástico:

> $P\left\lbrack Z(t + \delta) = z_{1}\  \right|\ Z(t) = z\rbrack \neq P\lbrack Z(t + \delta) = z_{1}\rbrack$.

Esta dependencia expresa la existencia de memoria en el proceso
estocástico, donde el estado que el proceso asume en el futuro depende
del estado pasado. Los procesos estocásticos buscan capturar los
aspectos claves de esta dependencia en el tiempo. Por ejemplo, podemos
esperar que la dependencia se haga más y más débil conforme aumente la
separación temporal con respecto a la observación inicial. En el caso
del precio de un producto, si éste tuvo un valor particular hace mucho
tiempo atrás debería afectar de manera poco significativa el precio de
mercado presente.

## Homogeneidad de un proceso estocástico

Consideremos el proceso estocástico con espacio discreto y en tiempo
continuo $\left\{ U(t),t \geq 7am \right\}$ cuya variable de espacio es
definida como:

```{admonition} Ejemplo 1 Homogeneidad (Variable de Interés)
:class: suggestion

-   $U(t)$ $≝$ Número de usuarios que han llegado al restaurante desde la
apertura hasta el instante de tiempo $t$
```

Donde se supone que el restaurante abre a las $7am$. El estado de este
proceso estocástico en el tiempo es no-decreciente en el tiempo, es
decir, para cada pareja de instantes $(t_{1},t_{2})$ tal que
$7am\  \leq t_{1} \leq t_{2}$, podemos afirmar que

> $\begin{matrix} P\lbrack U\left( t_{1} \right) \geq u\rbrack \leq P\lbrack U\left( t_{2} \right) \geq u\rbrack & \forall\ u \in N,\ u > 0 \end{matrix}$.

Es decir, si tomamos como referencia un número de clientes $u$, es más
probable observar más de $u$ usuarios en el momento $t_{2}$ que en el
momento $t_{1}$ ya que en $t_{2}$ ha transcurrido más tiempo, lo que da
una mayor oportunidad de observar más usuarios. Es interesante
preguntarse si la velocidad del crecimiento del valor de la variable de
estado es constante en el tiempo. Por ejemplo, si en promedio, entre las
10 y las 11 de la mañana, llegan el mismo número de usuarios que entre
las 1 y las 2 de la tarde, en términos matemáticos, nos estamos
preguntando si:

> $$E\left\lbrack U(11am) - U(10am) \right\rbrack = E\left\lbrack U(2pm) - U(1pm) \right\rbrack$$


Note que en este caso nos preguntamos si esperamos observar, en valor
esperado, el mismo número de usuarios en un intervalo de una hora.
Cuando un proceso estocástico es homogéneo, esta igualdad se cumple para
todo intervalo de la misma longitud, luego esperamos observar el mismo
número de usuarios en cualquier intervalo de una hora.

Si por el contrario si suponemos que el sistema modelado es un
restaurante, es razonable suponer que a la hora del almuerzo lleguen más
clientes que en otros momentos del día. Así, es probable que la igualdad
arriba no sea verdadera. Este es un ejemplo de un proceso estocástico no
homogéneo en el tiempo, ya que la dinámica de cambio de estado no es
igual a lo largo de la secuencia de observaciones.

Formalmente, un proceso estocástico en tiempo continuo
$\left\{ X(t),t \geq 0 \right\}$ es homogéneo si se cumple que:

> $P\left\lbrack X\left( t_{2} \right) - X\left( t_{1} \right) = u \right\rbrack = P\left\lbrack X\left( t_{2} - t_{1} \right) = u \right\rbrack\ \ \ \ 0 \leq t_{1} \leq t_{2},\ \forall\ u \in \ S$

En otras palabras, el cambio de la variable sólo depende de la distancia
temporal entre las observaciones (el ancho del intervalo
$t_{2} - t_{1}$) y no de la elección de los valores particulares de
$t_{1}$ y $t_{2}$.

Consideremos ahora el proceso estocástico con espacio de estados
discreto y en tiempo discreto $\left\{ S_{n},n \geq 0 \right\}$, cuya
variable de estado es definida como:

```{admonition} Ejemplo 2 Homogeneidad (Variable de Interés)
:class: suggestion

-   $S_{n}$ $≝$ Número de sellos obtenidas luego del n-ésimo lanzamiento de
una moneda.
```

Se puede afirmar que la probabilidad de obtener un número cualquiera de
sellos $v$, no depende del momento en el tiempo en el que se esté
observando el sistema, si no de la cantidad de lanzamientos que se
realicen. Éste, es un claro ejemplo de un proceso estocástico homogéneo
en tiempo discreto. De forma general, para un proceso estocástico en
tiempo discreto $\left\{ X_{n},n \geq 0 \right\}$, la propiedad de
homogeneidad se puede describir como:

> $P\left\lbrack X_{m} - X_{n} = v \right\rbrack = P\left\lbrack X_{m - n} = v \right\rbrack\ \ \ 0 \leq n \leq m,\ \ \forall\ v \in S$.

$$$$
