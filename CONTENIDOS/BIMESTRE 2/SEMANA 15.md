# 🔍 ¿Qué es un Algoritmo de Monte Carlo?

> Un algoritmo **Monte Carlo** es un tipo de algoritmo probabilista que utiliza **simulaciones aleatorias** para obtener **aproximaciones** rápidas a problemas complejos, aceptando una pequeña probabilidad de error (Página 9, 12).

Se basa en tres principios fundamentales:
1. Generar valores aleatorios mediante números pseudoaleatorios.
2. Realizar múltiples simulaciones para recopilar datos.
3. Calcular una estimación basada en los resultados agregados.

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/8/84/Pi_30K.gif" width="300" alt="Monte Carlo PI Estimation" />
</p>

---

## 🧪 Ejemplo Clásico: Estimar PI
El método de Monte Carlo estima el valor de π generando puntos aleatorios en un cuadrado y contando cuántos caen dentro de un círculo inscrito.

- **Código de Ejemplo** (adaptado del concepto proporcionado):
  ```java
  public class MonteCarloPi {
      public static void main(String[] args) {
          int dentro = 0, total = 100000;
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

- **Descripción**: Se generan `total` puntos aleatorios en un cuadrado de lado 1. La proporción de puntos que caen dentro del círculo inscrito (de radio 1) se multiplica por 4 para estimar π. Cuantas más iteraciones, mayor es la precisión.

---

## 📊 Aplicaciones Comunes
Los algoritmos de Monte Carlo son ampliamente utilizados en diversos campos (mencionados implícitamente en el contexto de algoritmos numéricos, Página 2):
- 📈 **Simulación financiera**: Evaluación de riesgos y precios de activos.
- 🧪 **Cálculo de integrales definidas**: Aproximación de áreas bajo curvas.
- 🎮 **Física computacional**: Simulación de partículas y sistemas físicos.
- 🎲 **Juegos y simulaciones**: Modelado de escenarios aleatorios.
- 🧬 **Biología y genética**: Simulación de poblaciones y procesos evolutivos.
- 🌐 **Estimación de probabilidades**: Análisis de sistemas complejos.

---

## 🧠 Ventajas y Desventajas
| **Ventajas**                                      | **Desventajas**                                  |
|--------------------------------------------------|--------------------------------------------------|
| Fácil de implementar y entender.                 | No garantiza resultados exactos (Página 9).      |
| Escalable a problemas de alta dimensión.         | Requiere muchas iteraciones para alta precisión. |
| Útil cuando no hay soluciones analíticas simples.| Depende de una buena generación de números pseudoaleatorios (Página 14). |
| Rápido para aproximaciones en problemas complejos.| |

---

## 🧪 Generación de Números Pseudoaleatorios
Los algoritmos de Monte Carlo dependen de números pseudoaleatorios generados por métodos deterministas, como el **método congruencial lineal** (Páginas 14, 17-18).

- **Taller (Páginas 17-18)**:
  - Implementar un generador con parámetros: `α = 1664525`, `c = 1013804223`, `m = 2^32`, y una semilla definida.
  - Generar 100 números en [0,1) y analizar su distribución en intervalos: [0,0.2), [0.2,0.4), [0.4,0.6), [0.6,0.8), [0.8,1.0).

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

---

## 🎥 Video Educativo
<p align="center">
  <strong>🎥 Aprende sobre el Método de Monte Carlo</strong><br><br>
  <a href="https://www.youtube.com/watch?v=v0nISE5B2wQ">
    <img src="https://img.youtube.com/vi/v0nISE5B2wQ/0.jpg" alt="Video sobre Monte Carlo" width="500">
  </a><br>
  ⬆️ Haz clic en la imagen para verlo en YouTube
</p>

---

## Conclusión
Los algoritmos **Monte Carlo** son herramientas poderosas para obtener aproximaciones rápidas en problemas complejos, utilizando simulaciones aleatorias basadas en números pseudoaleatorios (Páginas 9, 12, 14). Aunque no garantizan resultados exactos, su facilidad de implementación y escalabilidad los hacen ideales para aplicaciones como la estimación de π, simulaciones financieras y cálculos numéricos. La calidad de los números pseudoaleatorios es crucial para su efectividad (Páginas 17-18).
