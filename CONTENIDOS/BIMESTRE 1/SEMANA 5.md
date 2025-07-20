# 🗓️ Semana 05

## 📘 Temas tratados
- Notación Theta (Θ)
- Notación Omega (Ω)
- Notación O (Big O)
- Notación Asintótica Condicional
- Demostraciones con Límites

---

## 🔹 Notación Theta (Θ)

La notación **Theta (Θ)** representa un **límite ajustado** del crecimiento de un algoritmo. Esto implica que el algoritmo crece a la misma velocidad que una función g(n), tanto desde arriba como desde abajo. Es útil cuando el mejor y peor caso coinciden en el orden de crecimiento.

### Ejemplos:

- **Θ(1)** – Tiempo constante: acceso a un índice de un array.
- **Θ(n)** – Tiempo lineal: recorrido completo de un arreglo.
- **Θ(n log n)** – Tiempo lineal-logarítmico: Merge Sort, Heap Sort.
- **Θ(n²)** – Tiempo cuadrático: Bubble Sort en su peor caso.

---

## 🔹 Notación Omega (Ω)

La notación **Omega (Ω)** describe un **límite inferior** en el tiempo de ejecución de un algoritmo. Representa el **mejor caso**: la menor cantidad de recursos que puede necesitar.

---

## 🔹 Notación O (Big O)

La notación **O** (O grande) define un **límite superior**. Se usa para expresar el **peor caso**, indicando el máximo tiempo o espacio que un algoritmo puede requerir según el tamaño de la entrada.

---

## 🔹 Notación Asintótica Condicional

Este tipo de análisis se aplica bajo **condiciones específicas** de entrada, que afectan la complejidad del algoritmo.

Por ejemplo:

- Un algoritmo con complejidad **O(n²)** puede comportarse como **O(n)** si la entrada está casi ordenada.
- Sirve para modelar el comportamiento en situaciones del mundo real.

---

## 🧮 Demostraciones con Límites

### Caso 1:

Si:

$$
\lim_{n \to \infty} \frac{f(n)}{g(n)} = c \in \mathbb{R}
$$

Entonces:

$$
\begin{aligned}
&f(n) \in O(g(n)) \\
&f(n) \in \Omega(g(n)) \\
&f(n) \in \Theta(g(n)) \\
&g(n) \in O(f(n)) \\
&g(n) \in \Omega(f(n)) \\
&g(n) \in \Theta(f(n)) \\
\end{aligned}
$$

Ambas funciones se comportan igual, diferenciándose por una constante.

---

### Caso 2:

Si:

$$
\lim_{n \to \infty} \frac{f(n)}{g(n)} = \infty
$$

Entonces:

$$
\begin{aligned}
&f(n) \notin O(g(n)) \\
&f(n) \in \Omega(g(n)) \\
&f(n) \notin \Theta(g(n)) \\
&g(n) \in O(f(n)) \\
&g(n) \notin \Omega(f(n)) \\
&g(n) \notin \Theta(f(n)) \\
\end{aligned}
$$

Por grande que sea la constante en $g(n)$, nunca superará a $f(n)$.

---

### Caso 3:

Si:

$$
\lim_{n \to \infty} \frac{f(n)}{g(n)} = 0
$$

Entonces:

$$
\begin{aligned}
&f(n) \in O(g(n)) \\
&f(n) \notin \Omega(g(n)) \\
&f(n) \notin \Theta(g(n)) \\
&g(n) \notin O(f(n)) \\
&g(n) \in \Omega(f(n)) \\
&g(n) \notin \Theta(f(n)) \\
\end{aligned}
$$

La función $g(n)$ crece más rápidamente que $f(n)$.

---
