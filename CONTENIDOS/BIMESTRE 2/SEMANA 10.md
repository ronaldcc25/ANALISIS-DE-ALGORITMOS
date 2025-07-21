# 🧩 Unidad 4: Algoritmos Voraces

## 🎯 Objetivo

Explorar el uso de **algoritmos voraces** en la resolución de problemas de optimización, aplicados especialmente sobre **grafos dirigidos y no dirigidos**. Se busca comprender cómo estos algoritmos toman decisiones eficientes aunque no siempre óptimas.

---

## ⚙️ ¿Qué son los algoritmos voraces?

Los **algoritmos voraces (greedy)** resuelven problemas paso a paso, eligiendo en cada momento la mejor opción local disponible con la esperanza de alcanzar una solución óptima global.

### ✨ Características

- Rápidos y fáciles de implementar.
- Se aplican a problemas de optimización.
- No siempre garantizan una solución óptima.
- Se basan en heurísticas que toman decisiones locales óptimas.

---

## 👍 Ventajas y 👎 Desventajas

| ✅ Ventajas                          | ❌ Desventajas                                                                 |
|-------------------------------------|--------------------------------------------------------------------------------|
| Fáciles de implementar              | No garantizan la solución óptima global                                       |
| Producción eficiente de soluciones  | No todos los problemas de optimización se resuelven con algoritmos voraces    |
| A veces encuentran la solución óptima | Difícil encontrar una función de selección que asegure decisiones correctas |

---

## 🪙 Ejemplo clásico: Cambio de monedas

Resolver el problema de dar vuelto usando el **menor número de monedas posibles**.  
🔁 Se selecciona en cada paso la moneda de mayor denominación que no exceda el monto restante.

---

## 🌐 Grafos y árboles de recubrimiento mínimo

### 🌲 ¿Qué es un árbol de recubrimiento mínimo (MST)?

Un **árbol de expansión mínimo** conecta todos los vértices de un grafo no dirigido con la **menor suma de pesos posible**.

#### 📌 Aplicaciones
- Planificación de redes eléctricas.
- Redes de telecomunicaciones.
- Sistemas de distribución logística.

---

## 🧩 Algoritmos clásicos para MST

### 🧵 Algoritmo de Kruskal
1. Ordenar todas las aristas por peso ascendente.
2. Añadir la arista más ligera que **no cree ciclos**.
3. Repetir hasta conectar todos los nodos.

> Usa estructuras de conjuntos disjuntos (Union-Find).

---

### 🔄 Algoritmo de Prim
1. Iniciar desde cualquier nodo.
2. Repetidamente añadir la arista más barata que conecte el árbol con un nodo no visitado.
3. Continuar hasta incluir todos los nodos.

> Utiliza una **cola de prioridad** para seleccionar las aristas mínimas.

---

## 🔄 Grafos dirigidos

Un **grafo dirigido** \( G = (V, A) \) está formado por:
- **V**: Conjunto de vértices.
- **A**: Conjunto de arcos dirigidos.

Cada arco es un **par ordenado** \((v, w)\) donde:
- `v`: es la **cola** del arco (origen).
- `w`: es la **cabeza** del arco (destino).

📌 Importante: \( A \rightarrow B \) **no implica** \( B \rightarrow A \)

---

## 🛣️ Caminos mínimos en grafos dirigidos

### 🎯 Objetivo

Encontrar el **camino más corto desde un nodo fuente** a todos los demás vértices.

### ⚡ Algoritmo de Dijkstra (para grafos con pesos positivos)

1. Inicializar todas las distancias como infinito, excepto la fuente (0).
2. Usar una cola de prioridad (min-heap).
3. Mientras la cola no esté vacía:
   - Extraer el nodo con menor distancia.
   - Para cada vecino no visitado:
     - Si la distancia actual + peso < distancia del vecino:
       - Actualizar distancia.
       - Añadir el vecino a la cola.

#### 🧮 Pseudocódigo

```python
Inicializar distancias[] con infinito excepto la fuente;
Crear una cola de prioridad;
Mientras la cola no esté vacía:
    Extraer el nodo con menor distancia;
    Para cada vecino:
        Si distancia actual + peso < distancia[vecino]:
            Actualizar distancia[vecino];
            Añadir vecino a la cola;
```
