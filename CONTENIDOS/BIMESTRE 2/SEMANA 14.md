# 🔢 Algoritmos Probabilistas

---

## 🧩 ¿Qué son los Algoritmos Probabilistas?
Los **algoritmos probabilistas** utilizan decisiones aleatorias, lo que puede generar resultados distintos para la misma entrada. Se dividen en:

- **Las Vegas**: Siempre producen un resultado correcto, pero el tiempo de ejecución varía (Página 12).
- **Monte Carlo**: Pueden dar resultados incorrectos con una probabilidad pequeña, pero son rápidos (Páginas 9, 12).

> **Ejemplo (Páginas 3-4)**: En la fábula del tesoro, un dragón se lleva `y` lingotes cada noche. Si el tesoro tiene `x` lingotes en A o B, decidir aleatoriamente entre A o B (lanzando una moneda) da un beneficio esperado de `x - 7.5y` lingotes, mejor que esperar 4 días (`x - 9y`) o pagar al elfo (`x - 8y`).

<p align="center">
  <img src="https://img.youtube.com/vi/sU4UMh_W8W8/maxresdefault.jpg" alt="Algoritmos Probabilistas" width="500" />
</p>

---

## ⏱️ Tiempo Esperado
El **tiempo esperado** es el tiempo promedio de ejecución de un algoritmo probabilista, considerando las elecciones aleatorias para una entrada fija (Página 10).

- **Tiempo Promedio**: Tiempo medio de un algoritmo determinista sobre todas las entradas posibles del mismo tamaño.
- **Tiempo Esperado en el Peor Caso**: Promedio en el escenario más desfavorable.

### 📌 Ejemplo: Búsqueda Aleatoria
```java
public class RandomSearch {
    public static int busquedaAleatoria(int[] arr, int objetivo) {
        Random rand = new Random();
        int intentos = 0;
        while (true) {
            int index = rand.nextInt(arr.length);
            intentos++;
            if (arr[index] == objetivo) {
                return intentos; // Retorna el número de intentos
            }
        }
    }
}
```

- **Complejidad Temporal**: Tiempo esperado `O(n)` si el elemento está presente.

---

## 📐 Algoritmos Numéricos
Los algoritmos numéricos resuelven problemas matemáticos aproximadamente usando métodos computacionales (Página 2).

### 🧮 Método de Monte Carlo
Utiliza simulaciones aleatorias para estimar valores como áreas, probabilidades o integrales (Página 12).

- **Ejemplo: Estimar PI**:
  ```java
  public class MonteCarloPi {
      public static void main(String[] args) {
          int dentro = 0, total = 10000;
          for (int i = 0; i < total; i++) {
              double x = Math.random();
              double y = Math.random();
              if (x * x + y * y <= 1) dentro++;
          }
          double pi = 4.0 * dentro / total;
          System.out.println("PI estimado: " + pi);
      }
  }
  ```

- **Descripción**: Genera puntos aleatorios en un cuadrado y cuenta cuántos caen dentro de un círculo inscrito. La proporción estima π.

### ⚙️ Otros Métodos Numéricos
- **Método de Newton-Raphson**: Encuentra raíces de funciones.
- **Método de Simpson o Trapecios**: Integración numérica.
- **Métodos Iterativos**: Resuelven sistemas de ecuaciones lineales.

---

## 🧪 Generación de Números Pseudoaleatorios
Los **números pseudoaleatorios** son generados por algoritmos deterministas que simulan aleatoriedad, útiles en algoritmos probabilistas (Página 14).

- **Taller (Páginas 17-18)**: Implementar un generador pseudoaleatorio con el método congruencial lineal:
  - Parámetros: `α = 1664525`, `c = 1013804223`, `m = 2^32`, semilla definida por el estudiante.
  - Generar 100 números en [0,1).
  - Analizar la distribución en intervalos: [0,0.2), [0.2,0.4), [0.4,0.6), [0.6,0.8), [0.8,1.0).

- **Código de Ejemplo**:
  ```java
  public class GeneradorPseudoaleatorio {
      public static void main(String[] args) {
          long semilla = 12345;
          int cantidad = 100;
          double[] numeros = generarPseudoaleatorios(semilla, cantidad);
          System.out.println("Primeros 10 números pseudoaleatorios:");
          for (int i = 0; i < 10; i++) {
              System.out.println(numeros[i]);
          }
          // Análisis de distribución
          int[] intervalos = new int[5];
          for (double num : numeros) {
              if (num < 0.2) intervalos[0]++;
              else if (num < 0.4) intervalos[1]++;
              else if (num < 0.6) intervalos[2]++;
              else if (num < 0.8) intervalos[3]++;
              else intervalos[4]++;
          }
          System.out.println("Distribución en intervalos [0,0.2), [0.2,0.4), [0.4,0.6), [0.6,0.8), [0.8,1.0):");
          for (int i = 0; i < 5; i++) {
              System.out.println("Intervalo " + (i * 0.2) + " - " + ((i + 1) * 0.2) + ": " + intervalos[i]);
          }
      }

      public static double[] generarPseudoaleatorios(long semilla, int cantidad) {
          long a = 1664525;
          long c = 1013804223;
          long m = (long) Math.pow(2, 32);
          double[] resultados = new double[cantidad];
          long x = semilla;
          for (int i = 0; i < cantidad; i++) {
              x = (a * x + c) % m;
              resultados[i] = (double) x / m; // Normalización a [0,1)
          }
          return resultados;
      }
  }
  ```

- **Análisis**:
  - La distribución es aproximadamente uniforme si los números se distribuyen equitativamente en los intervalos.
  - Cambiar la semilla altera la secuencia, pero no la uniformidad si los parámetros son adecuados.

---

## 🧠 Conceptos Clave
| Concepto             | Descripción                                                  |
|----------------------|--------------------------------------------------------------|
| **Probabilista**     | Usa decisiones aleatorias, generando resultados distintos (Páginas 6, 8). |
| **Tiempo Esperado**  | Tiempo promedio considerando elecciones aleatorias (Página 10). |
| **Las Vegas**        | Siempre correcto, tiempo variable (Página 12).                |
| **Monte Carlo**      | Rápido, pero con posible error de baja probabilidad (Página 9). |
| **Números Pseudoaleatorios** | Generados por algoritmos deterministas para simular aleatoriedad (Página 14). |

---

## 🌈 Ventajas de los Algoritmos Probabilistas
- ✅ **Eficiencia**: Pueden ser más rápidos que los deterministas al evitar cálculos exhaustivos (Página 5).
- ✅ **Flexibilidad**: Generan soluciones diferentes para la misma entrada (Página 8).
- ✅ **Tolerancia al Error**: Los algoritmos Monte Carlo permiten errores pequeños con repeticiones para mayor precisión (Página 9).
- ✅ **Simplicidad**: Facilitan la resolución de problemas complejos, como integrales numéricas.

---

## Conclusión
Los **algoritmos probabilistas** aprovechan la aleatoriedad para resolver problemas eficientemente, ya sea garantizando corrección (Las Vegas) o aceptando pequeños errores (Monte Carlo). El **tiempo esperado** mide su desempeño promedio, mientras que los métodos numéricos como Monte Carlo estiman valores complejos mediante simulaciones. La generación de números pseudoaleatorios es fundamental para su implementación (Páginas 3-18). Estos algoritmos son esenciales para problemas donde la aleatoriedad optimiza el rendimiento.

