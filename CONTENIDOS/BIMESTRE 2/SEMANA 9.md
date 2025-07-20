# 📘 Algoritmos Voraces y Grafos

Este repositorio contiene una explicación clara y estructurada de los **algoritmos voraces** y su aplicación en **grafos**, incluyendo el algoritmo de **Kruskal** y conceptos como **árboles de recubrimiento mínimo**, **caminos mínimos**, y más.

---

## 🧠 Algoritmos Voraces (Greedy Algorithms)

Los **algoritmos voraces** toman decisiones paso a paso eligiendo la mejor opción local disponible, sin considerar el impacto futuro.

### 🔍 ¿Cómo funcionan?

1. Se construye una solución desde cero.
2. En cada paso se elige la mejor opción local.
3. No se reconsideran decisiones anteriores.

### ✅ Ventajas

- **Simplicidad**: fácil de implementar.
- **Eficiencia**: más rápidos que otros métodos como programación dinámica o backtracking.
- Funcionan bien en problemas reales de **optimización**.

### ❌ Desventajas

- No garantizan soluciones óptimas globales.
- **Miopía algorítmica**: no consideran el efecto a largo plazo.
- Solo aplican si el problema cumple:
  - **Subestructura óptima**
  - **Elección voraz segura**

### 🧪 Ejemplos comunes

- Algoritmo de **Kruskal** y **Prim** (Árbol de recubrimiento mínimo).
- Algoritmo de **Dijkstra** (camino más corto).
- Problema del **cambio de monedas** (en casos simples).

---

## 🌳 Árbol de Recubrimiento Mínimo (MST)

Un **árbol de recubrimiento mínimo** de un grafo ponderado y no dirigido es un subconjunto de aristas que:

- Conecta todos los vértices.
- Tiene el **peso total mínimo**.
- No contiene **ciclos**.

### 🔗 Propiedades

- Un grafo conectado con _n_ vértices tiene un MST con _n - 1_ aristas.
- Puede haber más de un MST si existen aristas con el mismo peso.

---

## 🌐 Grafos

Un **grafo G(V, E)** se compone de:

- Un conjunto de **vértices (nodos)** `V`.
- Un conjunto de **aristas (enlaces)** `E` que conectan pares de vértices.

### Tipos de grafos

- **Conexo**: hay un camino entre cada par de vértices.
- **No conexo**: algunos vértices no están conectados.
- **Dirigido**: aristas con dirección (u → v).
- **No dirigido**: aristas sin dirección (u — v).

### 📍 Aplicaciones

- Redes sociales, mapas, redes de transporte, redes de computadoras, etc.

---

## 🛣️ Caminos en Grafos

Un **camino** es una secuencia de vértices conectados por aristas.

- Puede ser **simple** (sin repetir vértices) o contener **ciclos**.
- La **longitud** se mide por número de aristas o suma de pesos (en grafos ponderados).

### 🔧 Aplicaciones

- GPS, redes de datos, IA, juegos, logística, etc.

---

## 🌲 Árboles

Un **árbol** es un grafo conexo, **no dirigido y sin ciclos**.

### Propiedades

- Solo hay un camino entre cualquier par de nodos.
- Con _n_ nodos, contiene exactamente _n - 1_ aristas.
- Eliminar una arista **desconecta** el árbol.

### Tipos comunes

- **Árbol raíz** (nodo principal).
- **Árbol binario**, **AVL**, etc.

---

## ⚖️ Grafos Ponderados

Un **grafo ponderado** tiene un peso (costo) asignado a cada arista.

### Representaciones

#### 🧮 Matriz de Adyacencia

|     | A | B | C |
|-----|---|---|---|
| A   | 0 | 5 | 0 |
| B   | 5 | 0 | 2 |
| C   | 0 | 2 | 0 |

- `0` indica ausencia de arista o peso nulo.
- Las posiciones (i,j) representan el **peso entre vértices**.

---

## 🔍 Caminos Mínimos

Consiste en encontrar el camino de menor costo entre dos nodos de un grafo ponderado.

### Algoritmos clásicos

- **Dijkstra**: pesos positivos.
- **Bellman-Ford**: permite pesos negativos.
- **A***: utiliza heurística para mejorar eficiencia.

---

## 🧮 Algoritmo de Kruskal

### 📌 Descripción

Algoritmo voraz para encontrar un **árbol de recubrimiento mínimo (MST)** en un grafo **no dirigido y ponderado**.

### 🔁 Funcionamiento

1. Crear un conjunto disjunto para cada vértice.
2. Ordenar todas las aristas por peso ascendente.
3. Recorriendo las aristas:
   - Si los vértices están en diferentes conjuntos, añadir la arista al MST y unir conjuntos.
4. Repetir hasta tener _n - 1_ aristas.

### 🧾 Pseudocódigo

```pseudo
Kruskal(G):
    A = ∅
    Para cada vértice v en G:
        Crear un conjunto disjunto {v}
    Ordenar las aristas por peso ascendente
    Para cada arista (u, v) en el grafo ordenado:
        Si u y v no están en el mismo conjunto:
            Añadir (u, v) a A
            Unir los conjuntos de u y v
    Devolver A
```
