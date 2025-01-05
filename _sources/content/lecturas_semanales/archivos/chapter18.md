# Procesos de Decisión Markovianos

## Introducción

Consideremos un problema de decisión aleatorio en el tiempo con épocas
$E = \{ 1,2,3,\ldots n\}$, $S_{t}$ el espacio de estados, $A_{t}(i)$ el
espacio de decisiones para el estado $i$, $c_{t}(i,a)$ el costo
inmediato en el estado $i$ tomando la decisión $a$ y $p_{t}(j|i,a)$ la
probabilidad de estar en el estado $j$ en el siguiente periodo dado que
en el periodo actual se está en $i$ y se toma la decisión $a$. Este
problema se conoce como un proceso de decisión markoviano finito. Este
tipo de problemas se resuelven utilizando programación dinámica
estocástica (SDP). Sin embargo, en ciertos casos los componentes del
problema de decisión no dependen de la época, **i.e.** $S,$ $A(i)$,
$c(i,a)$ y $p(j|i,a)$. En este caso, se cumple la propiedad de
homogeneidad en el tiempo. Por tanto, se denomina Proceso de Decisión
markoviano homogéneo.

```{admonition} Ejemplo 1
:class: suggestion
 Se tiene un SDP donde se desea encontrar la política que
minimice costos.

$$\text{Épocas} = \{ 1,2,3 \}$$

$$\left\{ X_{n},n \geq 0 \right\},\ S = \{ a,b\}$$

$$A(i) = \left\{ d_{1},d_{2} \right\}\ \ \ \ \ \forall\ i \in S$$

Retornos inmediatos

$$C = \begin{matrix}
 & \begin{matrix}
d_{1} & d_{2}
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
3 & 1 \\
2 & 3
\end{bmatrix}
\end{matrix}$$

Probabilidades de transición

$$\mathbb{P}_{d_{1}} = \begin{matrix}
 & \begin{matrix}
a & b
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
1/2 & 1/2 \\
1/3 & 2/3
\end{bmatrix}
\end{matrix}\mathbb{\ \ \ \ \ \ \ P}_{d_{2}} = \begin{matrix}
 & \begin{matrix}
a & b
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
1/4 & 3/4 \\
2/3 & 1/3
\end{bmatrix}
\end{matrix}$$

Observamos que la solución se realiza de la siguiente forma:

$f_{3}(a) = min\left\{ \begin{matrix}
d_{1}:3\ \ \  \\
d_{2}:1*
\end{matrix} \right.\ $ $f_{3}(b) = min\left\{ \begin{matrix}
d_{1}:2* \\
d_{2}:3\ \ \ 
\end{matrix} \right.\ $

$f_{2}(a) = min\left\{ \begin{matrix}
d_{1}:3 + {\frac{1}{2}f}_{3}(a) + \frac{1}{2}f_{3}(b) = 4.5\ \ \  \\
d_{2}:1 + \frac{1}{4}{\ f}_{3}(a) + \frac{3}{4}f_{3}(b) = 2.75*
\end{matrix} \right.\ $ $f_{2}(b) = min\left\{ \begin{matrix}
d_{1}:2 + {\frac{1}{3}f}_{3}(a) + \frac{2}{3}f_{3}(b) = 3.66* \\
d_{2}:3 + {\frac{2}{3}f}_{3}(a) + \frac{1}{3}f_{3}(b) = 4.33
\end{matrix} \right.\ $

$f_{1}(a) = min\left\{ \begin{matrix}
d_{1}:3 + {\frac{1}{2}f}_{2}(a) + \frac{1}{2}f_{2}(b) = 6.205\ \ \  \\
d_{2}:1 + \frac{1}{4}{\ f}_{2}(a) + \frac{3}{4}f_{2}(b) = 4.43*
\end{matrix} \right.\ $ $f_{1}(b) = min\left\{ \begin{matrix}
d_{1}:2 + {\frac{1}{3}f}_{3}(a) + \frac{2}{3}f_{3}(b) = 5.36* \\
d_{2}:3 + {\frac{2}{3}f}_{3}(a) + \frac{1}{3}f_{3}(b) = 6.05
\end{matrix} \right.\ $

Entonces, sin importar la época, para el estado $a$, se toma la decisión
$d_{2}$ y para el estado $b$ la decisión $d_{1}.$
```

En los procesos de decisión markovianos, es interesante observar que
podemos tomar decisiones cuando el número de épocas es infinito, gracias
a la propiedad de homogeneidad.

## MDP homogéneo de épocas infinitas

Un proceso de decisión markoviano homogéneo de **épocas infinitas**
cumple la propiedad markoviana (donde todo SDP la cumple), y la
propiedad de homogeneidad en el tiempo. Dado esto, la ecuación de
Bellman se denota como $V(i)$ (valor de estar en el estado $i$) en vez
de $f_{t}(i)$, dado que ahora la decisión óptima no se verá afectada por
el período de decisión. La ecuación de Bellman se representa como:

$$V_{i} = \underset{a \in A(i)}{\text{min/max}}{\ \left\{ c(i,a) + \right.\ \mathbb{E}\left( V_{j} \right)}\}\ \forall\ i \in S$$

Dada la anterior expresión, ocurre un problema esencial, y es que para
el cálculo de un $V(i)$, éste puede verse afectado por sí mismo. De la
ecuación se puede observar que, si se acumulan épocas infinitas,
entonces $V(i)$ toma un valor infinito. Por tal motivo, se agrega a la
ecuación de Bellman un término conocido como $\beta$ o tasa de
descuento, que determina el valor en el tiempo de las decisiones. Por lo
que $\beta$ debe tomar un valor mayor a $0$ y menor a$\ 1$. Dado esto,
se tiene que:

$$V(i) = \underset{a \in A(i)}{\text{min/max}}{\ \left\{ c(i,a) + \right.\ \mathbf{\beta}\mathbb{E}\lbrack V(j)\rbrack}\}$$

Entre más cercano el valor de $\beta$ sea a$\ 1$, se le da más
importancia al futuro y entre más cercano sea a$\ 0$, se le da más
importancia al presente. Finalmente, al ser $\beta$ un valor menor a 1,
bajo una tendencia límite al infinito, el valor futuro tiende a$\ 0$,
dado que la expresión queda como
$\beta^{\# épocas} = \beta^{\infty} = 0$.

```{admonition} Ejemplo 2
:class: suggestion

Se tiene un MDP donde se desea encontrar la política que
minimice costos.

$$\text{Épocas} = \{ 1,2,3,\ldots,\infty\}$$

$$\left\{ X_{n},n \geq 0 \right\},\ S = \{ a,b\}$$

$$A(i) = \left\{ d_{1},d_{2} \right\}\ \ \ \ \ \forall\ i \in S$$

$$\beta = 0.5$$

Costos inmediatos

$$C = \begin{matrix}
 & \begin{matrix}
d_{1} & d_{2}
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
3 & 1 \\
2 & 3
\end{bmatrix}
\end{matrix}$$

Probabilidades de transición

$$\mathbb{P}_{d_{1}} = \begin{matrix}
 & \begin{matrix}
a & b
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
1/2 & 1/2 \\
1/3 & 2/3
\end{bmatrix}
\end{matrix}\mathbb{\ \ \ \ \ \ \ P}_{d_{2}} = \begin{matrix}
 & \begin{matrix}
a & b
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
1/4 & 3/4 \\
2/3 & 1/3
\end{bmatrix}
\end{matrix}$$

Ecuaciones de Bellman

$$\ V(a) = min\left\{ \begin{matrix}
d_{1}:3 + 0.5\left( \frac{1}{2}V(a) + \frac{1}{2}V(b) \right)\ \ \  \\
d_{2}:1 + 0.5\left( \frac{1}{4}V(a) + \frac{3}{4}V(b) \right)
\end{matrix} \right.\ \ \ \ V(b) = min\left\{ \begin{matrix}
d_{1}:2 + 0.5\left( \frac{1}{3}V(a) + \frac{2}{3}V(b) \right) \\
d_{2}:3 + 0.5\left( \frac{2}{3}V(a) + \frac{1}{3}V(b) \right)
\end{matrix} \right.\ $$
```

## Solución MDP de épocas infinitas

Con base en la definición de MDPs infinitos, podemos observar que las
matrices de probabilidades de transición están cumpliendo dos
propiedades: homogeneidad en el tiempo y markoviana. Una matriz
$\mathbb{P}_{a}$ donde $a \in A(i)\ \forall\ i \in S$ representa una
CMTD que puede ser o no ergódica.

Si deseamos resolver un MDP homogéneo infinito, es posible observar el
sistema en estado estable. Conociendo que en cada época de decisión se
plantea una cadena de Markov, podemos utilizar las técnicas para
resolver estado estable de una CMTD para resolver también el MDP
homogéneo infinito.

### **Iteración de Valor**

En una cadena de Markov, se puede resolver estado estable conociendo que
cuando la matriz de transiciones $\mathbb{P}$, se eleva a un número muy
grande puede llegar a estabilidad de acuerdo con sus características.
Este mismo proceso se aplica en el MDP, en donde $\mathbb{P}^{1}$
representa evaluar el proceso como un MDP homogéneo **finito**, es decir
un SDP con 1 época; $\mathbb{P}^{2}$ representa evaluar el proceso como
un SDP de 2 épocas y $\mathbb{P}^{n}$ como un SDP de $n$ épocas.

Se encuentra estabilidad cuando la decisión óptima es igual para un
estado, sin importar la época de decisión. Puede ocurrir que las
decisiones varíen en las primeras épocas para un mismo estado; sin
embargo, desde una época, el proceso llega a estabilidad y la regla de
decisión para un mismo estado no varía de acuerdo con la época de
decisión. Este proceso puede llegar a ser largo, dado que no se sabe con
exactitud cuándo se puede estabilizar el MDP.

### **Iteración de política**

Tal y como existe un método para resolver MDP homogéneo e infinito
siguiendo la lógica de $\mathbb{P}^{n}$, también existe uno con
ecuaciones de balance. Se supone que cada posible política que puede
ocurrir tiene una CMTD detrás de la política. El método de Iteración por
política evalúa el resultado de todas las **posibles** políticas y
encuentra la política que optimiza el proceso de decisión. El ejemplo 3
ilustra el método.

```{admonition} Ejemplo 3
:class: suggestion

**Continuamos con el ejemplo 2.**

Ecuaciones de Bellman

$$\ V(a) = min\left\{ \begin{matrix}
d_{1}:3 + 0.5\left( \frac{1}{2}V(a) + \frac{1}{2}V(b) \right)\ \ \  \\
d_{2}:1 + 0.5\left( \frac{1}{4}V(a) + \frac{3}{4}V(b) \right)
\end{matrix} \right.\ \ \ \ V(b) = min\left\{ \begin{matrix}
d_{1}:2 + 0.5\left( \frac{1}{3}V(a) + \frac{2}{3}V(b) \right) \\
d_{2}:3 + 0.5\left( \frac{2}{3}V(a) + \frac{1}{3}V(b) \right)
\end{matrix} \right.\ $$

Listamos todas las **posibles** políticas de decisión:

<u>Política 1:</u> Para el estado $a$ tomar la decisión $d_{1}$ y
para el estado $b$ la decisión $d_{1}$

<u>Política 2:</u> Para el estado $a$ tomar la decisión $d_{1}$ y
para el estado $b$ la decisión $d_{2}$

<u>Política 3:</u> Para el estado $a$ tomar la decisión $d_{2}$ y
para el estado $b$ la decisión $d_{1}$

<u>Política 4:</u> Para el estado $a$ tomar la decisión $d_{2}$ y
para el estado $b$ la decisión $d_{2}$

Cada política tiene asociada un set de ecuaciones que se puede resolver.
Por ejemplo, la política 1 tiene asociadas las ecuaciones:

$$V(a) = 3 + 0.5\left( \frac{1}{2}V(a) + \frac{1}{2}V(b) \right)$$

$$V(b) = 2 + 0.5\left( \frac{1}{3}V(a) + \frac{2}{3}V(b) \right)$$

Y al tener 2 incógnitas, se puede resolver y da como resultado:
$V(a) = 5.45$ y $V(b) = 4.36$

Si resolvemos para cada política, obtenemos que:

<u>Política 1:</u> $V(a) = 5.45$ y $V(b) = 4.36$

<u>Política 2:</u> $V(a) = 6$ y $V(b) = 6$

<u>Política 3:</u> $V(a) = 2.72$ y $V(b) = 3.68$

<u>Política 4:</u> $V(a) = 3.24$ y $V(b) = 4.9$

La política que minimiza el resultado será la cual que
$\sum_{i \in S}^{}{V(i)}$ sea la menor. En este caso es la política 3.
```

### **Método de solución de MDPs basado en Programación Lineal**

Supongamos un problema de decisión en el tiempo (MDP) donde se busca
optimizar una función objetivo, en este caso con sentido de
maximización. Las ecuaciones de Bellman son entonces:

$$V(i) = \max_{a \in A(i)}\left\{ c(i,a) + \beta \cdot \sum_{j \in S}^{}{p\left( j \middle| i,a \right) \cdot V(j)} \right\}\ \forall\ i \in S$$

Para cada estado, su valor óptimo $V^{*}(i)$ cumple con la siguiente
condición:

$$V^{*}(i) \geq \max_{a \in A(i)}\left\{ c(i,a) + \beta \cdot \sum_{j \in S}^{}{p\left( j \middle| i,a \right) \cdot V(j)} \right\}\ \forall\ i \in S$$

Si la anterior expresión se separa por acción se obtiene:

$$V^{*}(i) \geq c(i,a) + \beta \cdot \sum_{j \in S}^{}{p\left( j \middle| i,a \right) \cdot V(j)}\ \forall\ a \in A(i),\ i \in S$$

Entonces, para resolver el problema de decisión del MDP se utiliza
programación lineal

$$P = \min{\sum_{i \in S}^{}{V(i)}}$$

s.a,

$$V(i) \geq c(i,a) + \beta \cdot \sum_{j \in S}^{}{p\left( j \middle| i,a \right) \cdot V(j)}\ \forall\ a \in A(i),\ i \in S$$

$$V(i) \geq 0\ \forall\ i \in S\ $$

Observemos que, si el problema de decisión busca maximizar, el programa
lineal tendrá sentido de minimización. Así mismo, si el problema de
decisión busca minimizar, el programa lineal tendrá sentido de
maximización. No obstante, con el programa lineal solo se encuentra la
solución óptima $V^{*}(i)$ de cada estado. Ahora, ¿cómo se obtiene cuál
fue la acción que optimiza $V(i)$ en cada estado (política óptima
$\pi^{*}$)?

Para responder a esta pregunta, se analiza el valor de las variables
resultantes del programa dual asociado donde
$\mu(i,a)\ \forall\ a \in A(i),\ \ i \in S$ son las variables duales de
cada restricción del problema primal.

A continuación, se presenta el programa dual del MDP en mención:

$$D = \max{\sum_{i \in S}^{}{\sum_{a \in A(i)}^{}{\mu(i,a) \cdot c(i,a)}}}$$

s.a,

$$\sum_{a \in A(j)}^{}{\mu(j,a)}\  = \beta \cdot \sum_{i \in S}^{}{\sum_{a \in A(i)}^{}{p\left( j \middle| i,a \right) \cdot \mu(i,a)}}\ \forall\ \ j \in S$$

$$\mu(i,a) \geq 0\ \forall\ a\  \in A(i),\ i\  \in \ S$$

Por dualidad fuerte se tiene que $P^{*} = D^{*}$. De esta manera, para
saber las acciones correspondientes de política óptima para cada estado,
se buscan las restricciones activas del problema primal $P$ (donde las
variables duales toman valor).

### **Valor esperado de la política**

Ahora bien, $V(i)$ representa los retornos esperados en el estado $i$.
Si deseamos calcular los retornos de la política, tenemos que calcular
la probabilidad de estar en cada estado $i$ del sistema, y ponderarlo
por el valor de la política en ese estado $V(i)$. Para calcular el valor
esperado de una política, se debe estimar la probabilidad de estar en el
estado $i\ $en estado estable (únicamente válido para cadenas
ergódicas). Por lo que el valor esperado de la política se puede
expresar como:

$$\sum_{i \in S}^{}{\pi_{i} \cdot V(i)}$$

Entonces debemos calcular las **probabilidades en estado estable** **de
la política**. Sabemos entonces que cualquier política de un MDP
homogéneo e infinito se representa como una CMTD. Esta cadena representa
las transiciones que genera la política encontrada. Dado esto, se pueden
encontrar estas probabilidades y encontrar el valor esperado de la
política.

```{admonition} Ejemplo 4
:class: suggestion

**Continuando con el ejemplo 2.**

Ecuaciones de Bellman

$$\ V(a) = min\left\{ \begin{matrix}
d_{1}:3 + 0.5\left( \frac{1}{2}V(a) + \frac{1}{2}V(b) \right)\ \ \  \\
d_{2}:1 + 0.5\left( \frac{1}{4}V(a) + \frac{3}{4}V(b) \right)
\end{matrix} \right.\ \ \ \ V(b) = min\left\{ \begin{matrix}
d_{1}:2 + 0.5\left( \frac{1}{3}V(a) + \frac{2}{3}V(b) \right) \\
d_{2}:3 + 0.5\left( \frac{2}{3}V(a) + \frac{1}{3}V(b) \right)
\end{matrix} \right.\ $$

Y la política óptima es para el estado $a$ tomar la decisión $d_{2}$ y
para el estado $b$ la decisión $d_{1}$ con valores $V(a) = 2.72$ y
$V(b) = 3.68$.

Entonces se puede crear una CMTD con una matriz de transición con las
probabilidades dadas de la política:

$$\mathbb{P}^{*} = \begin{matrix}
 & \begin{matrix}
a & b
\end{matrix} \\
\begin{matrix}
a \\
b
\end{matrix} & \begin{bmatrix}
1/4 & 3/4 \\
1/3 & 2/3
\end{bmatrix}
\end{matrix}$$

A esta CMTD se puede calcular estado estable y da como resultado:
$\pi_{a} = 0.69$ y $\pi_{b} = 0.31$. Entonces el valor esperado de la
política es:

$$Valor = \pi_{a}V(a) + \pi_{b}V(b) = 3.02$$
```