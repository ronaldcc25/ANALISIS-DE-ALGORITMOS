# 🗓️ Semana 04

## 📘 Temas tratados:
- Notación Asintótica
- Tasa de Crecimiento en Algoritmos
- Tipos de Complejidad y Ejemplos en Java

---

## 🔹 Notación Asintótica

La **notación asintótica** es una herramienta fundamental en la ciencia de la computación para describir el comportamiento del tiempo de ejecución o uso de memoria de un algoritmo cuando el tamaño de la entrada tiende a infinito.

Permite abstraerse del hardware, lenguaje de programación o constantes, centrándose en cómo crecen las operaciones necesarias.

Por ejemplo, si un algoritmo realiza `3n + 5` operaciones, se considera que es `O(n)`.

---

## 🔹 Tasa de Crecimiento

La **tasa de crecimiento** describe cuán rápido aumenta el consumo de recursos en función del tamaño de la entrada `n`. Es útil para:

- Estimar rendimiento con entradas grandes.
- Comparar eficiencia entre algoritmos.
- Decidir qué algoritmo implementar.

---

## 🔹 Importancia de la Tasa de Crecimiento

| n      | O(log n) | O(n)  | O(n²)     |
|--------|----------|--------|-----------|
| 10     | 3        | 10     | 100       |
| 100    | 7        | 100    | 10,000    |
| 1000   | 10       | 1000   | 1,000,000 |

Algoritmos con tasas de crecimiento menores escalan mejor a entradas grandes.

---

## 🔹 Tipos Comunes de Complejidad

| Complejidad            | Notación   | Ejemplo                          |
|------------------------|------------|----------------------------------|
| Constante              | O(1)       | Acceso a un arreglo              |
| Logarítmica            | O(log n)   | Búsqueda binaria                 |
| Lineal                 | O(n)       | Recorrido de arreglo             |
| Lineal-logarítmica     | O(n log n) | Merge Sort, Quick Sort           |
| Cuadrática             | O(n²)      | Bubble Sort, selección           |
| Cúbica                 | O(n³)      | Algoritmos de fuerza bruta       |
| Exponencial            | O(2ⁿ)      | Problemas NP-completos           |
| Factorial              | O(n!)      | Permutaciones, backtracking      |

---

## 🔹 Ejemplos de Complejidad en Java

### 🔸 Búsqueda Lineal – O(n)

```java
public boolean buscarElemento(int[] arreglo, int objetivo) {
    for (int elemento : arreglo) {
        if (elemento == objetivo) {
            return true;
        }
    }
    return false;
}
