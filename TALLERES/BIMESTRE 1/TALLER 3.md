## TALLER 3
---

| i | j | X(i,j)            | Contador |
|---|---|-------------------|----------|
| 1 | 2 | 1, 2              | 2        |
| 1 | 3 | 1, 2, 3           | 3        |
| 1 | 4 | 1, 2, 3, 4        | 4        |
| 1 | 5 | 1, 2, 3, 4, 5     | 5        |
| 2 | 3 | 1, 2, 3           | 3        |
| 2 | 4 | 1, 2, 3, 4        | 4        |
| 2 | 5 | 1, 2, 3, 4, 5     | 5        |
| 3 | 4 | 1, 2, 3, 4        | 4        |
| 3 | 5 | 1, 2, 3, 4, 5     | 5        |
| 4 | 5 | 1, 2, 3, 4, 5     | 5        |

**Total:** `40`

---

## Representación

Se define:

$$
T(n) = \sum_{i=1}^{n-1} \sum_{j=i+1}^{n} \sum_{k=1}^{j} 1
$$

Reorganizando sumas:

$$
T(n) = \sum_{i=1}^{n-1} \sum_{j=i+1}^{n} j
$$

Sabemos que:

$$
\sum_{j=i+1}^{n} j = \frac{n(n+1)}{2} - \frac{i(i+1)}{2}
$$

Entonces:

$$
T(n) = \sum_{i=1}^{n-1} \left( \frac{n(n+1)}{2} - \frac{i(i+1)}{2} \right)
$$

Separando términos:

$$
T(n) = \frac{n(n+1)}{2} \sum_{i=1}^{n-1} 1 - \frac{1}{2} \sum_{i=1}^{n-1} i(i+1)
$$

Sabemos que:

$$
\sum_{i=1}^{n-1} i(i+1) = \frac{(n-1)n(n+1)}{3}
$$

Entonces:

$$
T(n) = \frac{n(n+1)}{2}(n-1) - \frac{1}{2} \cdot \frac{(n-1)n(n+1)}{3}
$$

Factorizando:

$$
T(n) = \frac{(n-1)n(n+1)}{2} \left(1 - \frac{1}{3} \right)
$$

Simplificando:

$$
T(n) = \frac{(n-1)n(n+1)}{2} \cdot \frac{2}{3} = \frac{(n-1)n(n+1)}{3}
$$

Para $n = 5$:

$$
T(5) = \frac{(5-1)(5)(6)}{3} = \frac{4 \cdot 5 \cdot 6}{3} = \frac{120}{3} = 40
$$

---

✅ **Resultado final:** $T(5) = 40$
