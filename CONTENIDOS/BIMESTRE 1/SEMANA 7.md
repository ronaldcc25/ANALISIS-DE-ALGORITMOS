
# 🗓️ Semana 07

## Temas tratados
- Recurrencias
- Suposiciones Inteligentes (Método de Sustitución)

---

## 📘 Recurrencias

Una **recurrencia** (o relación de recurrencia) es una expresión que define una función en términos de sí misma, pero con valores de entrada más pequeños.

Son útiles para describir el tiempo de ejecución de algoritmos recursivos, ya que su complejidad depende de llamadas recursivas con entradas menores.

Por ejemplo, el factorial de `n` se define como:

```math
n! = n \cdot (n - 1)!
```

Las **ecuaciones de recurrencia** son clave para encontrar la **complejidad asintótica** de algoritmos recursivos.

---

## 🧠 Solución de Recurrencias

Resolver una recurrencia = encontrar una forma no recursiva de la función.

### Técnicas comunes:

---

### ✅ Método de Sustitución (Suposiciones Inteligentes)

1. Calcular valores pequeños de la recurrencia.
2. Buscar un patrón o regularidad.
3. Proponer una fórmula general (solución candidata).
4. Verificar la solución por **inducción matemática**.

---

### ✅ Ecuación Característica

- Se usa para recurrencias lineales homogéneas con coeficientes constantes.
- Se transforma la recurrencia en una ecuación polinómica.
- Las **raíces** del polinomio ayudan a encontrar la forma general de la solución.

---

### ✅ Método del Árbol de Recursión

- Visualiza las llamadas recursivas como un árbol.
- Suma los costos en cada nivel del árbol para hallar el costo total.

---

### ✅ Teorema Maestro

Sirve para resolver recurrencias del tipo:

```math
T(n) = a \cdot T(n/b) + f(n)
```

Se aplica mucho en algoritmos **Divide y Vencerás**, como Merge Sort o QuickSort.

---
