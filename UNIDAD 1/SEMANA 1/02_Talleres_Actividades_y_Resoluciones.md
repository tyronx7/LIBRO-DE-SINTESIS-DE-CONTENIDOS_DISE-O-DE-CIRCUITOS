# Semana 1 — Talleres, Actividades y Resoluciones

## 1. Activación de conocimientos previos

| Pregunta | Respuesta |
| :--- | :--- |
| ¿Qué hace un interruptor? | Abierto: no pasa corriente (`0`). Cerrado: pasa corriente (`1`). |
| ¿Cómo guarda el celular la «A»? | Como el número $65=01000001_2$ (ASCII). |
| ¿Por qué 8, 16, 32, 64 GB? | Las memorias se direccionan con bits; la capacidad es potencia de 2 ($2^3,2^4,2^5,2^6$). |

---

## 2. Actividad 1 (parejas, 7 min) — Reto de conversión

### Ejercicio 1: $45_{10}$ → binario y hexadecimal
| División | Cociente | Resto |
| :-: | :-: | :-: |
| $45\div2$ | 22 | 1 |
| $22\div2$ | 11 | 0 |
| $11\div2$ | 5 | 1 |
| $5\div2$ | 2 | 1 |
| $2\div2$ | 1 | 0 |
| $1\div2$ | 0 | 1 |

$45_{10}=101101_2$ (comprobación: $32+8+4+1=45$). Agrupando `0010 1101` → $\mathbf{2D_{16}}$.

### Ejercicio 2: $\text{A7}_{16}$ → decimal
$\text{A}=10$: $10\cdot16+7=160+7=\mathbf{167_{10}}$.

### Ejercicio 3: $11100101_2$ → hexadecimal y octal
- Hex: `1110` `0101` = E, 5 → $\mathbf{E5_{16}}$.
- Octal (completando a `011 100 101`): 3, 4, 5 → $\mathbf{345_8}$.
- Comprobación: $229_{10}$ ($128+64+32+4+1$); $3\cdot64+4\cdot8+5=229$ ✓.

---

## 3. Actividad 2 (individual, 12 min) — Del enunciado a la compuerta

### Ejercicio 1: ¿Qué compuerta describe cada frase?
| Frase | Compuerta | Justificación |
| :--- | :-: | :--- |
| a) Alarma suena solo si las **dos** puertas están abiertas | **AND** | Todas las entradas en `1` |
| b) Luz se enciende si se pulsa **cualquiera** de los dos botones | **OR** | Al menos una en `1` |
| c) «Diferentes» si los jugadores eligen **distinto** | **XOR** | Entradas distintas |
| d) Bomba se **apaga** cuando el sensor está activo | **NOT** | Invierte la señal del sensor |

### Ejercicio 2: Tabla de verdad de $Y=A\cdot B+C'$
Con 3 entradas: $2^3=8$ filas.

| Dec | $A$ | $B$ | $C$ | $A\cdot B$ | $C'$ | $Y$ |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: |
| 0 | 0 | 0 | 0 | 0 | 1 | **1** |
| 1 | 0 | 0 | 1 | 0 | 0 | **0** |
| 2 | 0 | 1 | 0 | 0 | 1 | **1** |
| 3 | 0 | 1 | 1 | 0 | 0 | **0** |
| 4 | 1 | 0 | 0 | 0 | 1 | **1** |
| 5 | 1 | 0 | 1 | 0 | 0 | **0** |
| 6 | 1 | 1 | 0 | 1 | 1 | **1** |
| 7 | 1 | 1 | 1 | 1 | 0 | **1** |

Resultado: $Y=\sum m(0,2,4,6,7)$. *(La columna «Dec» es el bonus: cada fila $ABC$ convertida a decimal.)*

---

## 4. Resumen de la semana
- **Dos estados:** `0` y `1` son rangos de voltaje con zona indefinida entre ellos.
- **Bases:** binario = potencias de 2; hex = bloques de 4 bits; octal = bloques de 3 bits.
- **Complemento a dos:** negativo = invertir + 1; restar = sumar el negativo.
- **Códigos:** BCD (displays), Gray (sensores y K-maps), ASCII (texto).
- **7 compuertas** y sus tablas de verdad.
- **Datasheet:** pines, alimentación (14 y 7) y función del `74LS08`.

## 5. Tareas y próxima sesión
- [ ] **Lectura:** apartado de sistemas numéricos y códigos del texto base (aula virtual).
- [ ] **Cuestionario 01** en el aula virtual, tras la lectura.
- [ ] **Instalar Logisim-evolution:** GitHub → *Releases* (`.msi` Windows, `.dmg` macOS).
- [ ] **Martes — Práctica APE 01:** comprobación de compuertas en el simulador (traer laptop si es posible).

[⬅ Teoría](./01_Teoria_Sistemas_Codigos_y_Compuertas.md) · [README de la semana](./README.md)
