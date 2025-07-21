# 🎯 Resumen de Algoritmos de Ordenación con Divide y Vencerás

## 🎯 Objetivo

Este apartado se centra en comprender y aplicar algoritmos de ordenación basados en la estrategia **Divide y Vencerás**, destacando su eficiencia y aplicaciones, según el documento **"Unidad 5 - Algoritmos Divide y Vencerás"** de **Manuel Sucunuta (UTPL)**.

---

## 🧩 ¿Qué es Divide y Vencerás?

La estrategia **Divide y Vencerás** consiste en:

1. **Dividir** el problema en subproblemas más pequeños.  
2. **Conquistar** cada subproblema recursivamente.  
3. **Combinar** las soluciones parciales para obtener el resultado final.  

Es ideal para problemas que pueden descomponerse en partes similares al original, como la **ordenación de arreglos**.

---

## 📊 Algoritmos de Ordenación con Divide y Vencerás

### 📌 Merge Sort (Ordenación por Fusión)

#### 🧾 Descripción

`Merge Sort` divide un arreglo en dos mitades, las ordena recursivamente y luego fusiona las mitades ordenadas en un solo arreglo ordenado.

**Algoritmo** _(Páginas 12–13 del documento)_:

1. Si el tamaño del arreglo `n` es pequeño, utiliza un método de inserción.  
2. Divide el arreglo en dos subarreglos `U` y `V` de tamaño `n/2`.  
3. Ordena recursivamente `U` y `V`.  
4. Fusiona `U` y `V` en el arreglo original `T` comparando elementos y usando **centinelas (∞)**.

#### 🧾 Código de Ejemplo

```java
public class MergeSort {
    public static void mergeSort(int[] arr, int left, int right) {
        if (left < right) {
            int middle = (left + right) / 2;
            mergeSort(arr, left, middle);
            mergeSort(arr, middle + 1, right);
            merge(arr, left, middle, right);
        }
    }

    static void merge(int[] arr, int left, int mid, int right) {
        int n1 = mid - left + 1;
        int n2 = right - mid;
        int[] L = new int[n1 + 1];
        int[] R = new int[n2 + 1];

        for (int i = 0; i < n1; i++)
            L[i] = arr[left + i];
        for (int j = 0; j < n2; j++)
            R[j] = arr[mid + 1 + j];

        L[n1] = Integer.MAX_VALUE;
        R[n2] = Integer.MAX_VALUE;

        int i = 0, j = 0, k = left;
        while (k <= right) {
            if (L[i] <= R[j]) {
                arr[k] = L[i++];
            } else {
                arr[k] = R[j++];
            }
            k++;
        }
    }
}
```

### 📈 Complejidad Temporal: `O(n log n)` (Página 15)

---

## ✅ Ventajas de Merge Sort

- ✅ Estable (mantiene el orden relativo de elementos iguales).
- ✅ Eficiente para grandes conjuntos de datos.

## ❌ Desventajas de Merge Sort

- ❌ Requiere espacio adicional `O(n)`.

---

## ⚡ Quick Sort (Ordenación Rápida)

### 🧾 Descripción

`Quick Sort` selecciona un pivote, particiona el arreglo en elementos menores y mayores, y ordena recursivamente las particiones.

**Algoritmo** _(Página 19 del documento)_:

1. Si el subarreglo es pequeño, usar inserción.
2. Seleccionar un **pivote** (por ejemplo, el último elemento).
3. Particionar el arreglo:
   - Elementos menores a la izquierda.
   - Elementos mayores a la derecha.
4. Aplicar Quick Sort a ambas particiones.

---

### 🧾 Código de Ejemplo

```java
public class QuickSort {
    public static void quickSort(int[] arr, int low, int high) {
        if (low < high) {
            int pi = partition(arr, low, high);
            quickSort(arr, low, pi - 1);
            quickSort(arr, pi + 1, high);
        }
    }

    static int partition(int[] arr, int low, int high) {
        int pivot = arr[high];
        int i = low - 1;
        for (int j = low; j < high; j++) {
            if (arr[j] <= pivot) {
                i++;
                int temp = arr[i]; arr[i] = arr[j]; arr[j] = temp;
            }
        }
        int temp = arr[i + 1]; arr[i + 1] = arr[high]; arr[high] = temp;
        return i + 1;
    }
}
```
### 📈 Complejidad Temporal de Quick Sort

- Promedio: `O(n log n)`
- Peor caso: `O(n²)` (si el pivote es el menor o mayor elemento)

---

## ✅ Ventajas de Quick Sort

- ✅ Muy eficiente en la práctica.
- ✅ No requiere espacio adicional significativo (`O(log n)` por recursión).

---

## ❌ Desventajas de Quick Sort

- ❌ No es estable.
- ❌ Sensible a la elección del pivote.

---

## 🔢 Ejemplo (Página 22)

Ordenar el arreglo:

```text
[6, 2, 3, 8, 11, 9, 1, 10, 5, 7, 5, 4, 12]
```

## 🧠 Conceptos Clave

| 🧩 Concepto    | 💬 Descripción                                             |
|----------------|------------------------------------------------------------|
| **Divide**     | Separar el arreglo en subarreglos más pequeños.           |
| **Conquista**  | Ordenar recursivamente cada subarreglo.                   |
| **Combina**    | En Merge Sort: fusionar. En Quick Sort: particionar.      |
| **Eficiencia** | Complejidad promedio `O(n log n)` (Página 15).            |

---

## 🌈 Ventajas de la Estrategia Divide y Vencerás

- ✅ **Eficiencia:** Ideal para grandes cantidades de datos.  
- ✅ **Recursividad:** Compatible con estructuras recursivas.  
- ✅ **Versatilidad:** Funciona en múltiples problemas de ordenación.  
- ✅ **Organización:** Mejora claridad y modularidad del código.  

---

## 🧪 Ejemplo Interactivo

```java
public class OrdenarEjemplo {
    public static void main(String[] args) {
        int[] arreglo = {6, 2, 3, 8, 11, 9, 1, 10, 5, 7, 5, 4, 12};

        System.out.println("Arreglo original:");
        for (int num : arreglo) System.out.print(num + " ");

        MergeSort.mergeSort(arreglo, 0, arreglo.length - 1);
        System.out.println("\nArreglo ordenado con Merge Sort:");
        for (int num : arreglo) System.out.print(num + " ");

        // Reiniciar arreglo para Quick Sort
        arreglo = new int[]{6, 2, 3, 8, 11, 9, 1, 10, 5, 7, 5, 4, 12};
        QuickSort.quickSort(arreglo, 0, arreglo.length - 1);
        System.out.println("\nArreglo ordenado con Quick Sort:");
        for (int num : arreglo) System.out.print(num + " ");
    }
}
```
💡 Ejecuta este código para observar cómo `Merge Sort` y `Quick Sort` ordenan el mismo arreglo paso a paso.

---

## ✅ Conclusión

Los algoritmos **Merge Sort** y **Quick Sort**, basados en la técnica **Divide y Vencerás**, son herramientas poderosas para ordenar arreglos de forma eficiente.

| 🧮 Algoritmo   | 🧷 Estabilidad  | ⚙️ Eficiencia Teórica                        | 🗂️ Espacio Adicional |
|---------------|----------------|---------------------------------------------|-----------------------|
| Merge Sort    | ✅ Estable      | `O(n log n)`                                 | `O(n)`                |
| Quick Sort    | ❌ No estable   | `O(n log n)` promedio / `O(n²)` en el peor caso | `O(log n)`         |

📌 **Merge Sort** es más **predecible y estable**, mientras que **Quick Sort** suele ser más **rápido en la práctica**, pero depende de la **elección del pivote**.
