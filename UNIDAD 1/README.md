# Unidad 1 — Análisis de Lógica Combinacional con Diseño Clásico

**Resultado de aprendizaje (R1):** Diseña e implementa circuitos combinacionales básicos utilizando técnicas de diseño clásico.

## Mapa de la unidad

| Semana | Tema central | Archivos |
| :---: | :--- | :--- |
| [1](./SEMANA%201/README.md) | Sistemas numéricos, códigos y compuertas lógicas | Teoría · Talleres |
| [2](./SEMANA%202/README.md) | Álgebra de Boole y formas canónicas (SOP/POS) | Teoría · Caso alarma y talleres |
| [3](./SEMANA%203/README.md) | Mapas de Karnaugh, don't care y universalidad NAND/NOR | 2 sesiones · Proyecto integrador |
| [4](./SEMANA%204/README.md) | Circuitos aritméticos, comparador y ALU | Teoría · Taller práctico |

## Hilo conductor

```text
Sistemas numéricos ─► Compuertas ─► Álgebra de Boole ─► Canónicas (Σm / ΠM)
        (S1)             (S1)            (S2)                 (S2)
                                                                │
        ALU ◄─ Aritméticos ◄─ NAND/NOR ◄─ Don't care ◄─ Karnaugh ◄┘
        (S4)      (S4)          (S3)         (S3)         (S3)
```

## Competencias integradas de la unidad
1. Convertir entre bases y representar enteros con signo (complemento a dos).
2. Traducir un enunciado verbal a tabla de verdad y a forma canónica.
3. Minimizar con álgebra y con mapas de Karnaugh (3 y 4 variables, SOP/POS, con indiferentes).
4. Implementar con una sola familia (NAND-NAND / NOR-NOR) y estimar costo en CI.
5. Diseñar sumador/restador, detectar *overflow*, comparar magnitudes y entender la ALU.



[⬅ Volver al libro](../README.md)
