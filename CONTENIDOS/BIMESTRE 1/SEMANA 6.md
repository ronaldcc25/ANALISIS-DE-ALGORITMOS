# 🗓️ Semana 06

## Temas tratados

- Análisis de estructuras de control
- Notación Theta (Θ)
- Notación Asintótica Condicional
- Algoritmo Bubble Sort (pseudocódigo, análisis, implementación y prueba)

---

## Análisis de las Estructuras de Control

El análisis de algoritmos comienza evaluando el tiempo de ejecución de instrucciones individuales, normalmente acotado por una constante. Estos tiempos se combinan según la estructura de control del programa. Algunas estructuras son directas de analizar (como la composición secuencial), mientras que otras, como bucles y condiciones, requieren un análisis más detallado.

---

### Secuencias

Cuando las instrucciones se ejecutan una tras otra, el tiempo total es la suma de sus tiempos individuales.

**Fórmula:**

Si una instrucción toma tiempo \( T_1 \) y la siguiente \( T_2 \), el total es:

\[
T_1 + T_2
\]

---

### Bucles "Para" (For)

El tiempo depende del número de iteraciones y del costo de cada iteración.

**Ejemplo:**

```pascal
para i ← 1 hasta m hacer
    p(i)
```

Si \( p(i) \) toma tiempo constante \( C \), entonces el bucle toma \( m \cdot C \), es decir, \( \Theta(m) \).

---

### Bucles "Mientras" (While)

Ejecutan un bloque de código mientras una condición sea verdadera. La condición se evalúa **antes** de cada iteración. Si es falsa al inicio, el bloque no se ejecuta.

**Ejemplo:**

```pascal
mientras i ≤ m hacer
    p(i)
    i ← i + 1
```

La complejidad depende del número de veces que la condición sea verdadera.

---

### Bucles "Repetir" (Repeat-Until)

Ejecutan un bloque de código **al menos una vez** y repiten hasta que una condición se cumpla. La condición se evalúa **después** de cada iteración.

**Ejemplo:**

```pascal
i ← 0
repetir
    escribir("Iteración ", i)
    i ← i + 1
hasta que (i ≥ 5)
```

En este caso, el bloque se ejecuta exactamente 5 veces (para \( i = 0 \) a \( 4 \)).

---
