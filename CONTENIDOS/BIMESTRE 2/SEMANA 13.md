# 🔍 Mediana y Multiplicación de Matrices con Divide y Vencerás

---

## 🧩 ¿Qué es Divide y Vencerás?

La estrategia **Divide y Vencerás** divide un problema en subproblemas más pequeños, los resuelve recursivamente y combina las soluciones para obtener el resultado final. Es ideal para problemas como la búsqueda de la mediana y la multiplicación de matrices, donde la descomposición recursiva mejora la eficiencia.

![Multiplicación de Matrices Animación](https://miro.medium.com/v2/resize:fit:1200/format:webp/1*dWhuzVJ9ghk9Gn-RU8qfyQ.gif)

---

## 📌 Mediana de Dos Arreglos Ordenados

### Descripción

El problema consiste en hallar la mediana de dos arreglos ordenados en tiempo logarítmico, utilizando **búsqueda binaria** para dividir eficientemente el espacio de búsqueda.

- **Algoritmo** (Página 24):
  - Selecciona un pivote (idealmente la mediana) en uno de los arreglos.
  - Particiona el arreglo para identificar elementos menores y mayores al pivote.
  - Usa búsqueda binaria para encontrar la posición donde los arreglos combinados tienen la mediana.
  - Ejemplo (Página 24): Para un arreglo con `[..., 3, 4, 3, ...]`, se selecciona el pivote `p=3`, y la mediana se encuentra en la posición 4, dando como resultado `3`.
- **Código de Ejemplo** (adaptado del concepto proporcionado):

  ```java
  public class MedianSortedArrays {
      public static double findMedianSortedArrays(int[] nums1, int[] nums2) {
          if (nums1.length > nums2.length) {
              int[] temp = nums1; nums1 = nums2; nums2 = temp;
          }
          int m = nums1.length, n = nums2.length;
          int left = 0, right = m;
          while (left <= right) {
              int partitionX = (left + right) / 2;
              int partitionY = (m + n + 1) / 2 - partitionX;
              int maxLeftX = (partitionX == 0) ? Integer.MIN_VALUE : nums1[partitionX - 1];
              int minRightX = (partitionX == m) ? Integer.MAX_VALUE : nums1[partitionX];
              int maxLeftY = (partitionY == 0) ? Integer.MIN_VALUE : nums2[partitionY - 1];
              int minRightY = (partitionY == n) ? Integer.MAX_VALUE : nums2[partitionY];
              if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                  if ((m + n) % 2 == 0) {
                      return (Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY)) / 2.0;
                  } else {
                      return Math.max(maxLeftX, maxLeftY);
                  }
              } else if (maxLeftX > minRightY) {
                  right = partitionX - 1;
              } else {
                  left = partitionX + 1;
              }
          }
          throw new IllegalArgumentException("Arreglos no válidos");
      }
  }
  ```
- **Complejidad Temporal**: `O(log(min(m, n)))`, donde `m` y `n` son los tamaños de los arreglos, debido al uso de búsqueda binaria.
- **Ejemplo Interactivo**:

  ```java
  public static void main(String[] args) {
      int[] A = {1, 3, 8};
      int[] B = {7, 9, 10, 11};
      System.out.println(findMedianSortedArrays(A, B)); // Output: 8.0
  }
  ```

---

## 🧮 Multiplicación de Matrices

### Algoritmo Estándar

El algoritmo estándar para multiplicar dos matrices de tamaño `n x n` tiene una complejidad de `O(n³)`.

- **Código** (Página 25):

  ```java
  public class MatrixMultiplication {
      public static void multiply(int[][] a, int[][] b, int[][] c) {
          int n = a.length;
          for (int i = 0; i < n; i++) {
              for (int j = 0; j < n; j++) {
                  c[i][j] = 0;
                  for (int k = 0; k < n; k++) {
                      c[i][j] += a[i][k] * b[k][j];
                  }
              }
          }
      }
  }
  ```
- **Complejidad Temporal**: `O(n³)` (Página 25).
- **Fórmula**: ( C\_{i,j} = \\sum\_{k=1}^n A\_{i,k} B\_{k,j} ).

### ⚡ Algoritmo de Strassen

El algoritmo de Strassen reduce la complejidad a aproximadamente `O(n^2.81)` dividiendo cada matriz en cuatro submatrices y utilizando siete multiplicaciones recursivas en lugar de ocho.

- **Algoritmo** (mencionado implícitamente en el documento, Página 4):
  - Divide cada matriz en cuatro submatrices de tamaño `n/2 x n/2`.
  - Calcula siete productos intermedios (en lugar de ocho) combinando sumas y restas de submatrices.
  - Combina los resultados para obtener la matriz resultante.
- **Código de Ejemplo** (adaptado del concepto proporcionado):

  ```java
  public class StrassenMatrixMultiplication {
      public static int[][] strassen(int[][] A, int[][] B) {
          int n = A.length;
          int[][] C = new int[n][n];
          if (n <= 1) {
              C[0][0] = A[0][0] * B[0][0];
              return C;
          }
          // Dividir matrices en submatrices
          int mid = n / 2;
          int[][] A11 = new int[mid][mid], A12 = new int[mid][mid], A21 = new int[mid][mid], A22 = new int[mid][mid];
          int[][] B11 = new int[mid][mid], B12 = new int[mid][mid], B21 = new int[mid][mid], B22 = new int[mid][mid];
          for (int i = 0; i < mid; i++) {
              for (int j = 0; j < mid; j++) {
                  A11[i][j] = A[i][j];
                  A12[i][j] = A[i][j + mid];
                  A21[i][j] = A[i + mid][j];
                  A22[i][j] = A[i + mid][j + mid];
                  B11[i][j] = B[i][j];
                  B12[i][j] = B[i][j + mid];
                  B21[i][j] = B[i + mid][j];
                  B22[i][j] = B[i + mid][j + mid];
              }
          }
          // Calcular los 7 productos
          int[][] P1 = strassen(add(A11, A22), add(B11, B22));
          int[][] P2 = strassen(add(A21, A22), B11);
          int[][] P3 = strassen(A11, subtract(B12, B22));
          int[][] P4 = strassen(A22, subtract(B21, B11));
          int[][] P5 = strassen(add(A11, A12), B22);
          int[][] P6 = strassen(subtract(A21, A11), add(B11, B12));
          int[][] P7 = strassen(subtract(A12, A22), add(B21, B22));
          // Combinar resultados
          int[][] C11 = add(subtract(add(P1, P4), P5), P7);
          int[][] C12 = add(P3, P5);
          int[][] C21 = add(P2, P4);
          int[][] C22 = add(subtract(add(P1, P3), P2), P6);
          // Reconstruir matriz C
          for (int i = 0; i < mid; i++) {
              for (int j = 0; j < mid; j++) {
                  C[i][j] = C11[i][j];
                  C[i][j + mid] = C12[i][j];
                  C[i + mid][j] = C21[i][j];
                  C[i + mid][j + mid] = C22[i][j];
              }
          }
          return C;
      }
  
      private static int[][] add(int[][] A, int[][] B) {
          int n = A.length;
          int[][] result = new int[n][n];
          for (int i = 0; i < n; i++) {
              for (int j = 0; j < n; j++) {
                  result[i][j] = A[i][j] + B[i][j];
              }
          }
          return result;
      }
  
      private static int[][] subtract(int[][] A, int[][] B) {
          int n = A.length;
          int[][] result = new int[n][n];
          for (int i = 0; i < n; i++) {
              for (int j = 0; j < n; j++) {
                  result[i][j] = A[i][j] - B[i][j];
              }
          }
          return result;
      }
  }
  ```
- **Complejidad Temporal**: `O(n^2.81)` debido a la reducción de multiplicaciones.
- **Ejemplo Interactivo**:

  ```java
  public static void main(String[] args) {
      int[][] A = {{1, 2}, {3, 4}};
      int[][] B = {{5, 6}, {7, 8}};
      int[][] C = strassen(A, B);
      // Resultado esperado: [[19, 22], [43, 50]]
      for (int[] row : C) {
          for (int val : row) {
              System.out.print(val + " ");
          }
          System.out.println();
      }
  }
  ```

---

## 🧠 Conceptos Clave

| Concepto | Descripción |
| --- | --- |
| **Divide y Vencerás** | Técnica recursiva para dividir, resolver y combinar soluciones. |
| **Mediana** | Valor central de un conjunto ordenado, encontrado en `O(log(min(m, n)))` con búsqueda binaria. |
| **Strassen** | Algoritmo que reduce la multiplicación de matrices a 7 productos, logrando `O(n^2.81)`. |
| **Complejidad** | Mediana: `O(log(min(m, n)))`; Multiplicación estándar: `O(n³)`; Strassen: `O(n^2.81)`. |

---

## 🌈 Ventajas de la Estrategia

- ✅ **Eficiencia**: Reduce la complejidad temporal en problemas como la mediana y la multiplicación de matrices.
- ✅ **Recursividad**: Simplifica la implementación mediante descomposición en subproblemas.
- ✅ **Versatilidad**: Aplicable a diversos problemas algorítmicos.
- ✅ **Optimización**: Strassen mejora significativamente la multiplicación de matrices grandes.

---

## Conclusión

La estrategia **Divide y Vencerás** es clave para resolver problemas como la **mediana de dos arreglos ordenados** y la **multiplicación de matrices**. La búsqueda binaria permite encontrar la mediana en tiempo logarítmico (`O(log(min(m, n)))`), mientras que el algoritmo de Strassen optimiza la multiplicación de matrices a `O(n^2.81)` frente al estándar `O(n³)` (Páginas 24-25). Estos métodos demuestran la potencia de la recursión y la división en problemas algorítmicos complejos.
