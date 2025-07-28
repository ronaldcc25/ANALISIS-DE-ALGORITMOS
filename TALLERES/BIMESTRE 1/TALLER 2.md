## TALLER 2

### Enunciado

Dado:

- $f(n) = n^3 + 9n^2 \log(n)$  
- $g(n) = n^2 \log(n)$

Comprobar:

- ¿$f(n) \in \mathcal{O}(g(n))$?
- ¿$f(n) \in \mathcal{O}(n^2)$?

---

## 1. Primera parte

### a) Comprobacion: ¿$f(n) \in \mathcal{O}(g(n))$?

Dado:  
$f(n) = n^3 + 9n^2 \log(n)$  
$g(n) = n^2 \log(n)$

Cociente:

$$
\frac{f(n)}{g(n)} = \frac{n^3 + 9n^2 \log(n)}{n^2 \log(n)} = \frac{n^3}{n^2 \log(n)} + \frac{9n^2 \log(n)}{n^2 \log(n)} = \frac{n}{\log(n)} + 9
$$

Cuando $n \to \infty$, $\frac{n}{\log(n)} \to \infty$, por lo tanto:

$$
\frac{f(n)}{g(n)} \to \infty
$$

**Esto implica que:**  
$f(n) \notin \mathcal{O}(g(n))$

---

### b) Comprobacion: ¿$f(n) \in \mathcal{O}(n^2)$?

Cociente:

$$
\frac{f(n)}{n^2} = \frac{n^3 + 9n^2 \log(n)}{n^2} = n + 9 \log(n) \to \infty
$$

**Esto implica que:**  
$f(n) \notin \mathcal{O}(n^2)$

---

## 2. Segunda parte

Dado:

- $f(n) = 2^n$
- $g(n) = 2^{2n} = (2^n)^2$

### a) Comprobacion: ¿$f(n) \in \mathcal{O}(g(n))$?

$$
\frac{f(n)}{g(n)} = \frac{2^n}{2^{2n}} = \frac{1}{2^n} \to 0
$$

**Esto implica que:**  
$f(n) \in \mathcal{O}(g(n))$, porque el cociente tiende a cero.

---

### b) Comprobacion: ¿$g(n) \in \mathcal{O}(f(n))$?

$$
\frac{g(n)}{f(n)} = \frac{2^{2n}}{2^n} = 2^n \to \infty
$$

**Esto implica que:**  
$g(n) \notin \mathcal{O}(f(n))$, ya que el cociente crece sin límite.

---

## Conclusiones

- En el primer caso, $f(n)$ crece más rápido que $g(n)$, por lo tanto:
  - $f(n) \notin \mathcal{O}(g(n))$
  - $f(n) \notin \mathcal{O}(n^2)$

- En el segundo caso:
  - $f(n) \in \mathcal{O}(g(n))$
  - $g(n) \notin \mathcal{O}(f(n))$

Esto demuestra cómo la notacion $\mathcal{O}$ permite establecer comparaciones de crecimiento entre funciones, esencial en el analisis de algoritmos.

---
