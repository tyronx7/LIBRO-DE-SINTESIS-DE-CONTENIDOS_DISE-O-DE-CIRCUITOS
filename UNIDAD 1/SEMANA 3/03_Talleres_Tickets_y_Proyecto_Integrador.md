# Semana 3 — Talleres, Tickets y Proyecto Integrador

## 1. Taller dirigido en parejas (30 min)

| Ejercicio | Función |
| :-: | :--- |
| T1 | $F(A,B,C)=\sum m(1,3,4,6)$ |
| T2 | $F(A,B,C,D)=\sum m(0,1,4,5,6,7,14,15)$ (¿algún primo sobra?) |
| T3 | $F(A,B,C,D)=\sum m(0,2,5,8,10,13)$ (atención a las esquinas) |
| T4 | Diagnóstico de errores sobre T2 |

### T1 — Resolución
| $A\backslash BC$ | `00` | `01` | `11` | `10` |
| :-: | :-: | :-: | :-: | :-: |
| **0** | 0 | **1** | **1** | 0 |
| **1** | **1** | 0 | 0 | **1** |

$\{m_1,m_3\}\to A'C$; $\{m_4,m_6\}\to AC'$ (enrollando bordes) ⇒ $F=A'C+AC'=A\oplus C$.

### T2 — Resolución
Grupos primos esenciales de 4 celdas: $\{m_0,m_1,m_4,m_5\}\to A'C'$ y $\{m_6,m_7,m_{14},m_{15}\}\to BC$. El grupo $\{m_4,m_5,m_6,m_7\}\to A'B$ es **redundante** (sus unos ya están cubiertos).
$$F=A'C'+BC$$

### T3 — Resolución
- Esquinas $\{m_0,m_2,m_8,m_{10}\}\to B'D'$
- $\{m_5,m_{13}\}$ ($B=1,C=0,D=1$) $\to BC'D$

$$F=B'D'+BC'D$$

### T4 — Diagnóstico: 3 errores clásicos
Un estudiante obtuvo $F=A'C'+BC+A'B+A'B'C'$ para $\sum m(0,1,4,5,6,7,14,15)$.

| # | Error | Corrección |
| :-: | :--- | :--- |
| 1 | Columnas $CD$ en binario (`00,01,10,11`) | Usar **Gray** (`00,01,11,10`) |
| 2 | Grupo de **3 celdas** (no es potencia de 2) | Solo 1, 2, 4, 8… |
| 3 | Grupos **redundantes / no primos**: el par `0000`-`0001` ($A'B'C'$) ya está dentro del cuadrado de 4 ($A'C'$), más un término no esencial | Eliminar los no primos y los redundantes |

**Expresión correcta:** $F=A'C'+BC$.

---

## 2. Ticket de salida (Sesión 1) — resuelto
**Ejercicio:** SOP mínima de $F(A,B,C,D)=\sum m(0,2,5,7,8,10,13,15)$.
- Esquinas $\{m_0,m_2,m_8,m_{10}\}\to B'D'$
- Bloque central $\{m_5,m_7,m_{13},m_{15}\}\to BD$

$$F=B'D'+BD=(B\oplus D)'\quad\text{(XNOR entre }B\text{ y }D)$$

---

## 3. Proyecto integrador: «Un sistema, tres versiones»

### 3.1. Hitos
| Entrega | Semana | Unidad | Contenido |
| :-: | :-: | :-: | :--- |
| 1 | 6 | 1 — Bloque combinacional | Tabla de verdad, expresión mínima, esquema simulado en Logisim-evolution |
| 2 | 11 | 2 — Se agrega memoria | Diagrama de estados, flip-flops, esquema secuencial simulado |
| 3 | 16 | 3 — Descrito en VHDL | Simulación funcional, configuración en **Basys 3**, sustentación individual |

### 3.2. Equipos y recursos
**8 equipos** con **4 roles rotativos** en cada entrega:

| Rol | Función |
| :--- | :--- |
| Especificación | Traduce el enunciado a entradas, salidas y casos de prueba |
| Diseño | Tabla de verdad, expresión mínima y esquema lógico |
| Verificación | Simula, compara con lo predicho y reporta discrepancias |
| Documentación | Informe técnico y declaración de uso de IA |

**Límites por tarjeta Basys 3 (1 por equipo):** 16 interruptores · 5 pulsadores · 16 LED · 4 dígitos de display de 7 segmentos.

---

## 4. Tareas de la semana
- [ ] **Cuestionario de autoevaluación 03** (EVA): K-maps y condiciones indiferentes (Carpinelli, 2023).
- [ ] **Martes 27 — APE 03:** traer el diseño previo en papel (mapa resuelto y conversión a NAND de la función de la guía).
- [ ] **Proyecto integrador:** subir el acta de conformación del equipo; leer guía y rúbrica en el EVA.

[⬅ Sesión 2](./02_Sesion2_Condiciones_Indiferentes_y_NAND_NOR.md) · [README](./README.md)
