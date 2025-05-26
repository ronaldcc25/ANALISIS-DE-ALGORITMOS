## TALLER 2

🔸 Dado:  
- $f(n) = n^3 + 9n^2 \log(n)$  
- $g(n) = n^2 \log(n)$

### ▫️ Comprobar si $f(n) \in \mathcal{O}(g(n))$  
### ▫️ Comprobar si $f(n) \in \mathcal{O}(n^2)$

📌 Demostrar formalmente si existe relacion de pertenencia entre $f(n)$ y $\mathcal{O}(g(n))$  
y tambien entre $g(n)$ y $\mathcal{O}(f(n))$ considerando:  
- $f(n) = 2^n$  
- $g(n) = 2^{2n}$

---

## Primera parte

🔹 Dado:
- $f(n) = n^3 + 9n^2 \log(n)$  
- $g(n) = n^2 \log(n)$

### ▫️ Comprobar si $f(n) \in \mathcal{O}(g(n))$, **No**

$\displaystyle
\frac{f(n)}{g(n)} = \frac{n^3 + 9n^2 \log(n)}{n^2 \log(n)} = \frac{n^3}{n^2 \log(n)} + \frac{9n^2 \log(n)}{n^2 \log(n)} = \frac{n}{\log(n)} + 9
$

Cuando $n \to \infty \Rightarrow \frac{n}{\log(n)} \to \infty$, entonces:  
$\displaystyle
\frac{f(n)}{g(n)} \to \infty \Rightarrow f(n) \notin \mathcal{O}(g(n))
$

📌 **Esto implica que $f(n) \notin \mathcal{O}(g(n))$**

---

### ▫️ Comprobar si $f(n) \in \mathcal{O}(n^2)$, **No**

$\displaystyle
\frac{f(n)}{n^2} = \frac{n^3 + 9n^2 \log(n)}{n^2} = n + 9 \log(n) \to \infty
$

📌 **Esto implica que $f(n) \notin \mathcal{O}(n^2)$**

---

## Segunda parte

🔹 Dado:
- $f(n) = 2^n$  
- $g(n) = 2^{2n} = (2^n)^2$

### ▫️ Comprobar si $f(n) \in \mathcal{O}(g(n))$, **Si**

$\displaystyle
\frac{f(n)}{g(n)} = \frac{2^n}{2^{2n}} = \frac{1}{2^n} \Rightarrow \lim_{n \to \infty} \frac{f(n)}{g(n)} = 0
$

📌 **Esto implica que $f(n) \in \mathcal{O}(g(n))$**, porque el cociente tiende a cero.

---

### ▫️ Comprobar si $g(n) \in \mathcal{O}(f(n))$, **No**

$\displaystyle
\frac{g(n)}{f(n)} = \frac{2^{2n}}{2^n} = 2^n \to \infty \Rightarrow g(n) \notin \mathcal{O}(f(n))
$

📌 **Esto implica que $g(n) \in \mathcal{O}(f(n))$ no se comprueba, ya que el cociente crece sin limite.**
