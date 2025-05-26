# 🗓️ Semana 03

# 📌 Temas Teóricos

---

### 🔹 Crecimiento de Funciones y Notación Asintótica

- Permite describir el comportamiento del tiempo de ejecución de un algoritmo en función del tamaño de entrada.
- Se centra en el **comportamiento para entradas grandes**, sin importar constantes o detalles de implementación.

---

### 🔹 Notación O (Big-O) – Cota Superior

- Representa un **límite superior** del crecimiento.
- Si `f(n) ∈ O(g(n))`, significa que `f(n)` no crece más rápido que una constante por `g(n)`.

---

### 🔹 Notación Ω (Big-Omega) – Cota Inferior

- Representa un **límite inferior**.
- Si `f(n) ∈ Ω(g(n))`, entonces `f(n)` crece al menos tan rápido como una constante por `g(n)`.

---

### 🔹 Notación Θ (Theta) – Cota Ajustada

- Representa una acotación **tanto superior como inferior**.
- Si `f(n) ∈ Θ(g(n))`, entonces `f(n)` crece exactamente como `g(n)` (a escala constante).

---

### 🔹 Análisis del Caso Promedio

- Estima el tiempo de ejecución **esperado** de un algoritmo.
- Requiere suposiciones sobre la **probabilidad de las entradas**.
- Es más realista que el caso peor, pero también más complejo de calcular.

---

# ⚙️ Algoritmo: Merge Sort

---

### 🔸 ¿Qué es?

- Un algoritmo de ordenamiento basado en el paradigma **divide y vencerás**.
- Divide el array en mitades, las ordena recursivamente y luego las **fusiona**.

---

### 🔸 Método `MERGE`

- **Objetivo:** Combinar dos subarreglos ordenados (`L` y `R`) en uno solo.

#### **Proceso:**

1. Copiar los datos en arreglos temporales.
2. Comparar elementos uno a uno.
3. Insertar el menor en el arreglo original.
4. Copiar los elementos restantes si sobran.

#### **Ejemplo:**

```plaintext
L = [2, 5, 8]
R = [1, 3, 7]
Resultado: [1, 2, 3, 5, 7, 8]
