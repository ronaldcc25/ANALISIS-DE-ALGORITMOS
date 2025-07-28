# Aplicación encontrar el árbol de recubrimiento mínimo a partir de un grafo no dirigido

# 📌 Algoritmo de Prim en Java

Este proyecto implementa el algoritmo de Prim para encontrar el Árbol de Recubrimiento Mínimo (MST) en un grafo no dirigido y conexo.

## 🔧 ¿Qué hace este código?

- Solicita al usuario el número de nodos del grafo.
- Pide los pesos de las conexiones entre nodos para crear una matriz de adyacencia (0 si no hay conexión).
- Aplica el algoritmo de Prim para calcular el MST.
- Muestra:
  - La matriz de adyacencia del grafo.
  - Las aristas del MST con sus pesos y esquemas visuales.
  - El peso total del MST.
  - Un resumen final con el esquema completo del MST.

## 🚀 ¿Cómo funciona?

1. Genera una matriz de adyacencia simétrica basada en los pesos ingresados por el usuario.
2. Ejecuta el algoritmo de Prim:
   - Selecciona el nodo con el menor costo no incluido en el MST.
   - Actualiza los costos mínimos de los nodos adyacentes.
3. Muestra cada arista del MST con un esquema visual (nodo1 → nodo2 con peso).
4. Calcula y muestra el peso total del MST.
5. Presenta un resumen final con todas las aristas y esquemas.

## 📌 Útil para:

- Estudiantes aprendiendo algoritmos de grafos.
- Visualizar el proceso de construcción de un MST.
- Pruebas con grafos no dirigidos ingresados manualmente.

``` java
package algoritmoprim;

import java.util.*;

public class AlgoritmoPrim {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Ingreso del número de nodos
        System.out.print("Ingrese el numero de nodos del grafo: ");
        int n = sc.nextInt();

        // Matriz de adyacencia con guía clara
        int[][] grafo = new int[n][n];
        System.out.println("Ingrese las conexiones entre nodos (0 si no hay conexion):");

        for (int i = 0; i < n; i++) {
            for (int j = i + 1; j < n; j++) {
                System.out.print("Hay conexion entre " + (char) ('A' + i) + " y " + (char) ('A' + j) + "? Ingrese peso (0 si no hay): ");
                int peso = sc.nextInt();
                grafo[i][j] = peso;
                grafo[j][i] = peso; // Simetría automática
            }
        }

        // Mostrar el grafo
        System.out.println("\nGrafo ingresado:");
        mostrarGrafo(grafo);

        // Obtener el MST con Prim
        System.out.println("\nArbol de Recubrimiento Mínimo (Prim):");
        primMST(grafo);
    }

    static void mostrarGrafo(int[][] grafo) {
        int n = grafo.length;
        System.out.print("   ");
        for (int i = 0; i < n; i++) {
            System.out.print((char) ('A' + i) + "  ");
        }
        System.out.println();
        for (int i = 0; i < n; i++) {
            System.out.print((char) ('A' + i) + ": ");
            for (int j = 0; j < n; j++) {
                System.out.print(grafo[i][j] + "  ");
            }
            System.out.println();
        }
    }

    static void primMST(int[][] grafo) {
        int n = grafo.length;
        int[] key = new int[n];           // Costos mínimos
        boolean[] mstSet = new boolean[n]; // Nodos incluidos en MST
        int[] parent = new int[n];         // Para construir el MST

        Arrays.fill(key, Integer.MAX_VALUE);
        key[0] = 0; // Comenzar desde nodo A (índice 0)
        parent[0] = -1;

        for (int count = 0; count < n - 1; count++) {
            int u = minKey(key, mstSet);
            mstSet[u] = true;

            for (int v = 0; v < n; v++) {
                if (grafo[u][v] != 0 && !mstSet[v] && grafo[u][v] < key[v]) {
                    parent[v] = u;
                    key[v] = grafo[u][v];
                }
            }
        }

        int pesoTotal = 0;
        System.out.println("Aristas en el MST:");
        for (int i = 1; i < n; i++) {
            char nodo1 = (char) ('A' + parent[i]);
            char nodo2 = (char) ('A' + i);
            int peso = grafo[i][parent[i]];

            System.out.println("Nodo " + nodo1 + " - Nodo " + nodo2 + " \tPeso: " + peso);

            // Esquema visual individual
            System.out.println("Esquema:");
            System.out.println(" " + nodo1);
            System.out.println("  \\");
            System.out.println("   " + peso);
            System.out.println("    \\");
            System.out.println("     " + nodo2);
            System.out.println();

            pesoTotal += peso;
        }

        System.out.println("Peso total del MST: " + pesoTotal);

        // 🔽 Grafo MST total en forma de esquema al final
        System.out.println("\nResumen completo del MST (esquema final):");
        for (int i = 1; i < n; i++) {
            char nodo1 = (char) ('A' + parent[i]);
            char nodo2 = (char) ('A' + i);
            int peso = grafo[i][parent[i]];

            System.out.println("Nodo " + nodo1 + " - Nodo " + nodo2 + " \tPeso: " + peso);
            pesoTotal += peso;

            // Solo mostrar esquema si hay conexión real (> 0)
            if (peso > 0) {
                System.out.println("Esquema:");
                System.out.println(" " + nodo1);
                System.out.println("  \\");
                System.out.println("   " + peso);
                System.out.println("    \\");
                System.out.println("     " + nodo2);
                System.out.println();
            }

        }
        System.out.println("Valor total del MST: " + pesoTotal);
    }

    static int minKey(int[] key, boolean[] mstSet) {
        int min = Integer.MAX_VALUE, minIndex = -1;
        for (int v = 0; v < key.length; v++) {
            if (!mstSet[v] && key[v] < min) {
                min = key[v];
                minIndex = v;
            }
        }
        return minIndex;
    }
}
```
