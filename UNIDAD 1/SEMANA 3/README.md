# Semana 3 — Mapas de Karnaugh, condiciones indiferentes y universalidad NAND/NOR

## Contenido
| Archivo | Descripción |
| :--- | :--- |
| [01_Sesion1_Mapas_de_Karnaugh_SOP_POS.md](./01_Sesion1_Mapas_de_Karnaugh_SOP_POS.md) | K-maps de 3 y 4 variables, reglas de agrupación, implicantes, SOP y POS mínimas |
| [02_Sesion2_Condiciones_Indiferentes_y_NAND_NOR.md](./02_Sesion2_Condiciones_Indiferentes_y_NAND_NOR.md) | Don't care, universalidad, conversión a NAND-NAND |
| [03_Talleres_Tickets_y_Proyecto_Integrador.md](./03_Talleres_Tickets_y_Proyecto_Integrador.md) | Taller T1–T4, tickets, proyecto «Un sistema, tres versiones», tareas |

## Resumen
- **Adyacencia:** $XY+XY'=X$; el mapa la vuelve visual gracias al código Gray.
- Grupos de $2^k$ celdas eliminan $k$ variables; el mapa es un **toroide**.
- **SOP:** se agrupan `1` y se lee directo; **POS:** se agrupan `0` y se lee invertido.
- Las **`X`** se usan solo si agrandan grupos; nunca un grupo formado solo por `X`.
- SOP mínima ⇒ **NAND-NAND**; POS mínima ⇒ **NOR-NOR**.

[⬅ Semana 2](../SEMANA%202/README.md) · [Unidad 1](../README.md) · [Semana 4 ➡](../SEMANA%204/README.md)
