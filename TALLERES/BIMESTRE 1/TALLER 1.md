# TALLER 1
---
# Merge Sort -> CODIGO EN JAVA, con ordenamiento Merge Sort y entrada por consola

```java
import java.util.InputMismatchException;
import java.util.Scanner;

public class MergeSortHelper {

    // Funcion de mezcla (merge)
    public static void merge(int[] A, int p, int q, int r) {
        int nL = q - p + 1;
        int nR = r - q;

        int[] L = new int[nL];
        int[] R = new int[nR];

        for (int i = 0; i < nL; i++) {
            L[i] = A[p + i];
        }

        for (int j = 0; j < nR; j++) {
            R[j] = A[q + 1 + j];
        }

        int i = 0, j = 0, k = p;

        while (i < nL && j < nR) {
            if (L[i] <= R[j]) {
                A[k++] = L[i++];
            } else {
                A[k++] = R[j++];
            }
        }

        while (i < nL) {
            A[k++] = L[i++];
        }

        while (j < nR) {
            A[k++] = R[j++];
        }
    }

    // Funcion recursiva de Merge Sort
    public static void mergeSort(int[] A, int p, int r) {
        if (p < r) {
            int q = p + (r - p) / 2;  // evita posibles desbordamientos
            mergeSort(A, p, q);
            mergeSort(A, q + 1, r);
            merge(A, p, q, r);
        }
    }

    // Programa principal
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int n;

        // Lectura segura de la cantidad de elementos
        try {
            System.out.print("Ingrese la cantidad de elementos: ");
            n = scanner.nextInt();

            if (n <= 0) {
                System.out.println("La cantidad debe ser mayor que cero.");
                scanner.close();
                return;
            }

        } catch (InputMismatchException e) {
            System.out.println("Entrada no valida. Debe ingresar un numero entero.");
            scanner.close();
            return;
        }

        int[] A = new int[n];

        // Lectura de los elementos
        System.out.println("Ingrese los elementos del arreglo:");
        for (int i = 0; i < n; i++) {
            try {
                A[i] = scanner.nextInt();
            } catch (InputMismatchException e) {
                System.out.println("Entrada no valida. Debe ingresar numeros enteros.");
                scanner.close();
                return;
            }
        }

        // Ordenar el arreglo usando Merge Sort
        mergeSort(A, 0, n - 1);

        // Mostrar el arreglo ordenado
        System.out.println("Arreglo ordenado:");
        for (int i = 0; i < n; i++) {
            System.out.print(A[i] + " ");
        }
        System.out.println(); // salto de linea final

        scanner.close();
    }
}

```
