# Aplicación para determinar el camino mínimo a partir de un grafo dirigido

# 📌 Algoritmo de Floyd-Warshall en Java

Este proyecto implementa el algoritmo de Floyd-Warshall para encontrar los caminos mínimos entre todos los pares de nodos en un grafo dirigido.

## 🔧 ¿Qué hace este código?

- Solicita al usuario el número de nodos del grafo.
- Genera automáticamente una matriz de adyacencia con pesos aleatorios (o infinitos si no hay conexión).
- Ejecuta el algoritmo de Floyd-Warshall para calcular las distancias mínimas entre todos los nodos.
- Muestra:
  - La matriz generada.
  - Esquemas visuales para cada camino mínimo (de A a B, etc.).
  - La suma total de todos los caminos mínimos.

## 🚀 ¿Cómo funciona?

1. Se genera un grafo dirigido aleatorio.
2. Se aplica Floyd-Warshall:
   - Para cada nodo intermedio `k`, se evalúa si pasar por `k` mejora la distancia de `i → j`.
3. Se muestra visualmente cada ruta encontrada y el peso mínimo.
4. Se suma el peso de todos los caminos posibles (excepto hacia uno mismo).

## 📌 Útil para:

- Estudiantes aprendiendo algoritmos de grafos.
- Visualizar cómo funciona Floyd-Warshall.
- Pruebas con grafos dirigidos generados aleatoriamente.

``` java
package algoritmofloyd;

import java.util.*;

public class AlgoritmoFloyd {
    static final int INF = 999999;

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Random rand = new Random();

        System.out.print("Ingrese el numero de nodos del grafo dirigido: ");
        int n = sc.nextInt();
        int[][] grafo = new int[n][n];

        int minPeso = 1;
        int maxPeso = 20;
        double probabilidadConexion = 0.7;

        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (i == j) {
                    grafo[i][j] = 0;
                } else {
                    if (rand.nextDouble() < probabilidadConexion) {
                        grafo[i][j] = rand.nextInt(maxPeso - minPeso + 1) + minPeso;
                    } else {
                        grafo[i][j] = INF;
                    }
                }
            }
        }

        System.out.println("\nMatriz de adyacencia generada aleatoriamente:");
        mostrarMatriz(grafo, n);

        int[][] distancias = floydWarshall(grafo, n);

        System.out.println("\nCaminos minimos entre todos los pares de nodos:");
        mostrarEsquemas(distancias, n);

        // calcular el total de todos los caminos mínimos
        int total = calcularSumaTotalCaminos(distancias, n);
        System.out.println("Suma total de caminos minimos: " + total);
    }

    static void mostrarMatriz(int[][] m, int n) {
        System.out.print("    ");
        for (int i = 0; i < n; i++) {
            System.out.print("  " + (char) ('A' + i) + " ");
        }
        System.out.println();
        System.out.print("   +");
        for (int i = 0; i < n; i++) {
            System.out.print("----");
        }
        System.out.println();
        for (int i = 0; i < n; i++) {
            System.out.print(" " + (char) ('A' + i) + " |");
            for (int j = 0; j < n; j++) {
                if (m[i][j] == INF)
                    System.out.printf("%4s", "INF");
                else
                    System.out.printf(" %2d ", m[i][j]);
            }
            System.out.println();
        }
    }

    static int[][] floydWarshall(int[][] grafo, int n) {
        int[][] dist = new int[n][n];

        for (int i = 0; i < n; i++)
            dist[i] = grafo[i].clone();

        for (int k = 0; k < n; k++)
            for (int i = 0; i < n; i++)
                for (int j = 0; j < n; j++)
                    if (dist[i][k] < INF && dist[k][j] < INF)
                        if (dist[i][j] > dist[i][k] + dist[k][j])
                            dist[i][j] = dist[i][k] + dist[k][j];

        return dist;
    }

    static void mostrarEsquemas(int[][] dist, int n) {
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (i != j && dist[i][j] < INF) {
                    char from = (char) ('A' + i);
                    char to = (char) ('A' + j);
                    int peso = dist[i][j];
                    System.out.println("De " + from + " a " + to + " → Peso minimo: " + peso);
                    System.out.println("Esquema:");
                    System.out.println(" " + from);
                    System.out.println("  \\");
                    System.out.println("   " + peso);
                    System.out.println("    \\");
                    System.out.println("     " + to);
                    System.out.println();
                }
            }
        }
    }

    static int calcularSumaTotalCaminos(int[][] dist, int n) {
        int total = 0;
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                if (i != j && dist[i][j] < INF) {
                    total += dist[i][j];
                }
            }
        }
        return total;
    }
}
```
