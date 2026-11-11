# Semana 4 — Comparadores, ALU y Taller Práctico

## 1. Comparador de magnitud (CI 7485)

### 1.1. Igualdad $A=B$
Una **XNOR** por cada par $(A_i,B_i)$ (da `1` si son iguales) y una **AND** global: todos los bits deben coincidir.

### 1.2. Mayor que $A>B$
Se compara **desde el bit más significativo**: el primer bit donde difieren decide. Para 2 bits:
$$(A>B)=A_1B_1'+(A_1\oplus B_1)'\cdot A_0B_0'$$
(gana en el bit alto, **o** empatan en el alto y gana en el bajo).

---

## 2. De aquí sale la ALU

En un procesador, los bloques trabajan **en paralelo** y un **multiplexor** (Semana 5) elige cuál resultado sale según la instrucción:

1. Sumador / Restador
2. Comparador
3. Bloque lógico AND / OR / XOR

$$\text{Bloques en paralelo}\longrightarrow\text{Multiplexor (Semana 5)}\longrightarrow\text{Resultado}$$

---

## 3. Taller dirigido en parejas (25 min) — resuelto

### 3.1. Sumar $1011_2+0110_2$
| Col. | Operación | $S_i$ | Acarreo |
| :-: | :--- | :-: | :-: |
| 0 | $1+0+0=1$ | 1 | $C_1=0$ |
| 1 | $1+1+0=2$ | 0 | $C_2=1$ |
| 2 | $0+1+1=2$ | 0 | $C_3=1$ |
| 3 | $1+0+1=2$ | 0 | $C_4=1$ |

Resultado: $10001_2$ ($11+6=17$).

### 3.2. Restar $0110_2-0011_2$ con $M=1$
$B=0011\xrightarrow{\text{XOR}}1100$, $C_0=M=1$:
$$0110+1100+1=\mathbf1\,0011\Rightarrow S=0011_2\,(3),\ C_4=1$$

### 3.3. Retardo de un sumador de 16 bits
$$2\times16\times10\text{ ns}=32\text{ compuertas}\times10\text{ ns}=320\text{ ns}$$

### 3.4. Comparar $A=10_2$ y $B=01_2$
Bit más significativo: $A_1=1,\ B_1=0$ ⇒ difieren y gana $A$. Por tanto **$A>B=1$** y **$A=B=0$**.

---

## 4. Resumen de la semana
- **$S$ y $C$:** $S$ se escribe; $C$ se lleva.
- **Semisumador:** $S=A\oplus B$, $C=AB$; solo columna 0.
- **Sumador completo:** $S$ = impar de unos; $C_{out}$ = al menos dos unos.
- **Ripple-carry:** acarreo etapa a etapa, retardo $\approx2n\cdot10\text{ ns}$.
- **Resta:** $M=1$ ⇒ XOR invierten $B$ e inyectan $C_{in,0}=1$.
- **Overflow:** $V=C_3\oplus C_4$, no $C_{out}$.

## 5. Tarea para la próxima clase
- [ ] **Lectura:** capítulo de circuitos aritméticos combinacionales del texto base.
- [ ] **Cuestionario de autoevaluación 04** (EVA).
- [ ] **Diseño previo APE 04:** tabla de verdad y ecuaciones del sumador completo en papel, para el laboratorio (**martes 07:30–09:30**).

[⬅ Teoría](./01_Teoria_Circuitos_Aritmeticos_Resta_y_Overflow.md) · [README](./README.md) · [Unidad 1](../README.md)
