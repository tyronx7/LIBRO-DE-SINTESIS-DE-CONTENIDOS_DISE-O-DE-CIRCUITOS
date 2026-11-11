# Semana 2 — Caso Alarma y Talleres de Simplificación

## 1. Caso guiado: alarma de 3 sensores

**Enunciado:** una bodega tiene sensores de puerta ($A$), ventana ($B$) y movimiento ($C$). Para evitar falsas alarmas, la sirena $F$ suena si **al menos dos** sensores se activan.

| $i$ | $A$ | $B$ | $C$ | $F$ | Término canónico |
| :-: | :-: | :-: | :-: | :-: | :--- |
| 0 | 0 | 0 | 0 | 0 | $M_0=A+B+C$ |
| 1 | 0 | 0 | 1 | 0 | $M_1=A+B+C'$ |
| 2 | 0 | 1 | 0 | 0 | $M_2=A+B'+C$ |
| 3 | 0 | 1 | 1 | 1 | $m_3=A'BC$ |
| 4 | 1 | 0 | 0 | 0 | $M_4=A'+B+C$ |
| 5 | 1 | 0 | 1 | 1 | $m_5=AB'C$ |
| 6 | 1 | 1 | 0 | 1 | $m_6=ABC'$ |
| 7 | 1 | 1 | 1 | 1 | $m_7=ABC$ |

### 1.1. Simplificación algebraica
Partimos de $F=A'BC+AB'C+ABC'+ABC$. Por **idempotencia** se triplica $ABC$ para reducir los tres pares:
1. $A'BC+ABC=BC(A'+A)=BC$
2. $AB'C+ABC=AC(B'+B)=AC$
3. $ABC'+ABC=AB(C'+C)=AB$

$$\boxed{F=AB+AC+BC}\qquad\text{POS equivalente: }F=(A+B)(A+C)(B+C)$$

### 1.2. Costo en hardware

| Característica | Canónica | Simplificada |
| :--- | :--- | :--- |
| NOT | 3 (`1×7404`) | 0 |
| AND | 4 de 3 entradas (`2×7411`) | 3 de 2 entradas (`1×7408`) |
| OR | 1 de 4 entradas (o cascada con `7432`) | 1 de 3 entradas (2 compuertas de un `7432`) |
| **Total CI** | **4** | **2** |

---

## 2. Ticket de salida (Sesión 1) — resuelto
1. $(A'+BC)'=(A')'\cdot(BC)'=A(B'+C')$
2. Para $ABC$ con $4=100_2$: $m_4=AB'C'$ y $M_4=A'+B+C$.

---

## 3. Sesión 2: simplificación algebraica

### 3.1. Procedimiento
1. Buscar pares adyacentes: $XY+XY'=X$.
2. Duplicar términos si hace falta: $X=X+X$.
3. Absorción: $X+XY=X$.
4. Absorción del complemento: $X+X'Y=X+Y$.
5. Consenso: $XY+X'Z+YZ=XY+X'Z$.

> El álgebra **no** garantiza visualmente haber llegado al mínimo absoluto; por eso la Semana 3 introduce los mapas de Karnaugh.

### 3.2. Ejemplo guiado: $F=A+A'B+AB'C$
1. Original: $A+A'B+AB'C$
2. Absorción del complemento ($A+A'B=A+B$): $=(A+B)+AB'C$
3. Conmutativa: $=A+AB'C+B$
4. Absorción ($A+A(B'C)=A$): $=A+B$

**Impacto:** de 3 términos (5 literales) a **una OR de 2 entradas**. Verificación con $A=0,B=0,C=1$: original $=0$, simplificada $=0$ ✓.

---

## 4. Taller por grupos (entregables)
Cada grupo entrega: **1)** tabla de verdad, **2)** $\sum m$ y $\prod M$, **3)** SOP canónica, **4)** versión simplificada, **5)** recuento de compuertas y CI.

> Las resoluciones siguientes son una propuesta de verificación elaborada a partir de los enunciados.

### G1 y G5 — Luz de pasillo
Interruptores conmutados $A,B$; maestro $M=1$ apaga siempre. $F=(A\oplus B)\cdot M'$. Orden $ABM$.

| $i$ | $A$ | $B$ | $M$ | $F$ |
| :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | 0 |
| 1 | 0 | 0 | 1 | 0 |
| 2 | 0 | 1 | 0 | **1** |
| 3 | 0 | 1 | 1 | 0 |
| 4 | 1 | 0 | 0 | **1** |
| 5 | 1 | 0 | 1 | 0 |
| 6 | 1 | 1 | 0 | 0 |
| 7 | 1 | 1 | 1 | 0 |

- $\sum m(2,4)$ · $\prod M(0,1,3,5,6,7)$
- SOP canónica: $F=A'BM'+AB'M'$
- Simplificada: $F=M'(A\oplus B)$
- Hardware: 1 XOR + 1 NOT + 1 AND → 3 CI (`7486`, `7404`, `7408`).

### G2 y G6 — Detector de primos (2, 3, 5, 7)
- $\sum m(2,3,5,7)$ · $\prod M(0,1,4,6)$
- SOP canónica: $A'BC'+A'BC+AB'C+ABC$
- Simplificada: $\{m_2,m_3\}\to A'B$; $\{m_5,m_7\}\to AC$ ⇒ $F=A'B+AC$ (4 literales)
- Hardware: 1 NOT, 2 AND, 1 OR → 3 CI (`7404`, `7408`, `7432`).

### G3 y G7 — Bomba de agua
Agua en cisterna $B$ y (tanque bajo $A$ o manual $C$): $F=B(A+C)$. Orden $ABC$.
- Filas con $F=1$: `011`, `110`, `111` ⇒ $\sum m(3,6,7)$ · $\prod M(0,1,2,4,5)$
- SOP canónica: $A'BC+ABC'+ABC$
- Simplificada: $F=AB+BC=B(A+C)$
- Hardware: 1 OR + 1 AND → 2 CI (`7432`, `7408`).

### G4 y G8 — Aviso de cinturón
Motor $E$, cinturón puesto $C$, puerta abierta $P$: $F=E(C'+P)$. Orden $ECP$.
- Filas con $F=1$: `100`, `101`, `111` ⇒ $\sum m(4,5,7)$ · $\prod M(0,1,2,3,6)$
- SOP canónica: $EC'P'+EC'P+ECP$
- Simplificada: $F=EC'+EP=E(C'+P)$
- Hardware: 1 NOT, 1 OR, 1 AND → 3 CI (`7404`, `7432`, `7408`).

---

## 5. Tarea (aprendizaje autónomo — 2,5 h)
- [ ] **Lectura:** Garza, J. Á. (2025). *Electrónica digital I: álgebra de Boole, De Morgan y formas canónicas.* Complemento en inglés: Carpinelli (2023), apartado de álgebra de Boole.
- [ ] **Cuestionario N.º 02** (autoevaluación en el EVA).
- [ ] Traer resuelto el ejercicio del taller de su grupo para la Semana 3.

[⬅ Teoría](./01_Teoria_Algebra_Boole_y_Formas_Canonicas.md) · [README](./README.md)
