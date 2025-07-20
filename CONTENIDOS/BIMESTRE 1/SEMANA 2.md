# DEMOSTRACION POR INDUCCION MATEMATICA
*  Demostrar propiedades acerca de corrección y eficiencia de algoritmos

#### **PRINCIPIO DE INDUCCION MATEMATICA**
* Es una técnica de demostración lógica muy utilizada en matemáticas, especialmente para probar afirmaciones que se aplican a todos los números naturales (o a una parte de ellos, a partir de cierto punto)

Tres pasos:
1. Caso base
2. Hipótesis de inducción
3. Demostración

$$\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

$$\sum_{i=1}^{n} i = \frac{10(10+1)}{2} =55$$

#### PROBAR QUE:

$$1+2+3+...+n= \frac{n(n+1)}{2}$$

   * #### **Paso 1: Caso Base (n=1):**

$$\sum_{i=1}^{n} i = \frac{n(n+1)}{2}$$

$$ 1 = \frac{1(1+1)}{2}$$

   * #### **Paso 2: Hipótesis de inducción**

      * Hipótesis: Supón que se cumple n = k, es decir:

$$ 1+2+3+...+k= \frac{k(k+1)}{2}$$

   * #### **Paso 3: Demostración**

      * Probemos que se cumple n = k + 1, es decir:

$$ 1+2+3+...+k= \frac{k(k+1)}{2}$$
$$ 1+2+3+...+k(k+1)= \frac{k(k+1)}{2}+(k+1)$$
$$ \frac{k(k+1)+2(k+1)}{2} $$
$$ \frac{(k+2)(k+1)}{2} $$
