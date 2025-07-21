# 📚 Unidad 5: Algoritmos Divide y Vencerás

## 🧠 Introducción

La técnica **Divide y Vencerás** descompone un problema en subproblemas más pequeños, los resuelve recursivamente y combina sus soluciones para obtener el resultado final.

---

## 🔍 1. Búsqueda Binaria

Algoritmo eficiente para buscar un elemento en un **arreglo ordenado**.

### 🧪 Algoritmo

1. Comparar el objetivo con el elemento central.
2. Si son iguales 👉 retornar índice.
3. Si es menor 👉 buscar en mitad izquierda.
4. Si es mayor 👉 buscar en mitad derecha.

### 🧾 Código Java

```java
public class BusquedaBinaria {
    public static int buscar(int[] arreglo, int objetivo) {
        int inicio = 0;
        int fin = arreglo.length - 1;
        while (inicio <= fin) {
            int medio = (inicio + fin) / 2;
            if (arreglo[medio] == objetivo) {
                return medio;
            } else if (arreglo[medio] < objetivo) {
                inicio = medio + 1;
            } else {
                fin = medio - 1;
            }
        }
        return -1; // No encontrado
    }
}
```

## 🔃 2. Ordenación

### 🧩 Merge Sort (Ordenación por Fusión)

📌 Divide el arreglo en mitades, las ordena recursivamente y las fusiona.

#### 🔗 Algoritmo

1. Si el arreglo es pequeño, usar inserción.
2. Dividir el arreglo en dos subarreglos `U` y `V`.
3. Ordenar `U` y `V` recursivamente.
4. Fusionar en el arreglo original.

📈 **Complejidad Temporal:** `O(n log n)`  
📄 Referencia: Páginas 12–15

#### 🔁 Proceso de Fusión

- Compara elementos de `U` y `V`.
- Usa **centinelas (∞)** para facilitar la fusión.

---

### ⚡ Quicksort (Ordenación Rápida)

📌 Selecciona un pivote y reordena el arreglo alrededor de él.

#### 🔗 Algoritmo

1. Si el subarreglo es pequeño, usar inserción.
2. Seleccionar un pivote.
3. Reordenar el arreglo:
   - Elementos menores a la izquierda.
   - Elementos mayores a la derecha.
4. Aplicar Quicksort recursivamente a las particiones.

📄 Página 19  
🔢 **Ejemplo:**  
Ordenar `[6, 2, 3, 8, 11, 9, 1, 10, 5, 7, 5, 4, 12]`

📈 **Complejidad Promedio:** `O(n log n)`  
⚠️ En el peor caso: `O(n²)` si no se elige un buen pivote.

---

## 🎯 3. Mediana

La mediana puede obtenerse usando la técnica de partición de **Quicksort**.

### 🧭 Algoritmo

1. Elegir un pivote (idealmente cercano a la mediana).
2. Particionar el arreglo.
3. La mediana está en la posición central tras particionar.

📄 Página 24

---

## ✖️ 4. Multiplicación de Matrices

Multiplicación clásica de matrices cuadradas `n x n`.

### 🧾 Código Java

```java
public static void multiplicar(int[][] a, int[][] b, int[][] c) {
    int n = a.length;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            c[i][j] = 0;
        }
    }
    for (int k = 0; k < n; k++) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                c[i][j] += a[i][k] * b[k][j];
            }
        }
    }
}
```
