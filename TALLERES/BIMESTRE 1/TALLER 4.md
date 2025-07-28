
# TALLER 4

## 1. Codificar el algoritmo de Fibonacci

El algoritmo clásico de Fibonacci se define recursivamente como:

```python
def fibonacci(n):
    if n <= 1:
        return n
    return fibonacci(n-1) + fibonacci(n-2)
```

Esta implementación tiene una complejidad exponencial debido a la alta cantidad de llamadas recursivas repetidas.

---

## 2. Identificar las recurrencias

La función recursiva anterior genera la siguiente relación de recurrencia:

$$
T(n) = T(n - 1) + T(n - 2) + c
$$

donde $T(n)$ representa el tiempo de ejecución para calcular el $n$-ésimo número de Fibonacci y $c$ es una constante.

---

## 3. Obtener la ecuación general

Para resolver la recurrencia:

$$
T(n) = T(n - 1) + T(n - 2)
$$

Usamos el método de solución por ecuaciones características. Asumimos una solución de la forma:

$$
T(n) = r^n
$$

Sustituyendo en la recurrencia:

$$
r^n = r^{n-1} + r^{n-2}
$$

Dividiendo entre $r^{n-2}$:

$$
r^2 = r + 1
$$

Resolviendo esta ecuación cuadrática:

$$
r = \frac{1 \pm \sqrt{5}}{2}
$$

Entonces la solución general es:

$$
T(n) = A \left(\frac{1 + \sqrt{5}}{2}\right)^n + B \left(\frac{1 - \sqrt{5}}{2}\right)^n
$$

---

## 4. Demostrar

Utilizando inducción matemática o aplicando condiciones iniciales ($T(0) = 0$, $T(1) = 1$), se determinan las constantes $A$ y $B$. Así obtenemos la fórmula cerrada conocida como la fórmula de Binet:

$$
F(n) = \frac{1}{\sqrt{5}} \left( \left(\frac{1 + \sqrt{5}}{2}\right)^n - \left(\frac{1 - \sqrt{5}}{2}\right)^n \right)
$$

Esta fórmula permite calcular el $n$-ésimo número de Fibonacci en tiempo constante.

---

✅ **Conclusión:** Se ha codificado, analizado y resuelto el algoritmo de Fibonacci utilizando técnicas de recurrencias y fórmulas cerradas.
