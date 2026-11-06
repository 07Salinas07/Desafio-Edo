Adopta y Difunde: EDO logística con Heun y RK4

1. Problema y contexto
Un refugio de mascotas de la comunidad lanza una campaña de adopción. La población beneficiaria son las familias del barrio. Pregunta del desafío: **¿en cuántos días el 80 % de las familias conocerá la campaña?** Meta cuantificable: y(t) ≥ 0,8·K.

2. Modelo matemático
- Variable dependiente: y(t) = familias informadas (familias)
- Variable independiente: t = tiempo (días)
- Parámetros (hipotéticos): K = 2000 familias (población total), r = 0,25 1/día (tasa de difusión)
- Condición inicial: y(0) = y0 = 20 familias
- Intervalo de simulación: 0 a 40 días

**EDO:**

dy/dt = r · y · (1 − y/K),  y(0) = y0

Supuestos: la información se propaga boca a boca (crece con y) y se frena al saturarse el barrio (factor 1 − y/K); K es constante; no hay olvido de la campaña.

3. Solución analítica
y(t) = K / (1 + A·e^(−rt)),  con A = (K − y0) / y0

**Verificación:**
- Condición inicial: y(0) = K/(1 + A) = K / (K/y0) = y0 ✓
- Sustituyendo en la EDO, ambos lados son iguales a K·A·r·e^(−rt) / (1 + A·e^(−rt))² ✓

**Tiempo exacto para llegar al 80 %:** t* = ln(4A) / r ≈ **23,9 días** con los parámetros por defecto.

4. Métodos numéricos
Ambos usan los mismos parámetros, condición inicial, intervalo y tamaño de paso h.

- **Heun (RK2):** k1 = f(y), k2 = f(y + h·k1), y(n+1) = y(n) + h·(k1 + k2)/2
- **RK4:** k1 = f(y), k2 = f(y + h·k1/2), k3 = f(y + h·k2/2), k4 = f(y + h·k3), y(n+1) = y(n) + h·(k1 + 2·k2 + 2·k3 + k4)/6

5. Análisis comparativo
La aplicación calcula el error absoluto y el error relativo porcentual frente a la solución analítica y compara dos tamaños de paso (por defecto h = 4 y h = 1 días). Muestra tabla por pasos y gráfica con la solución analítica, Heun y RK4. RK4 resulta mucho más preciso que Heun, y ambos mejoran al reducir h.

6. Interpretación y limitaciones
La difusión es lenta al comienzo, se acelera en el tramo medio y se frena cuando casi todo el barrio ya conoce la campaña. Para llegar antes a la meta conviene aumentar r (más difusión) o empezar con más familias informadas (y0).

Limitaciones: modelo simplificado, K constante, sin olvido ni canales distintos de difusión. Los parámetros son hipotéticos: la simulación **no es una predicción comprobada con datos reales**.

Cómo ejecutar
Abrir `index.html` en cualquier navegador. No requiere instalación. En la app se pueden ajustar y0, K, r, el tiempo de simulación y dos tamaños de paso; las entradas se validan y se indican las unidades.
