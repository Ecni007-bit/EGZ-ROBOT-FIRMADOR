# Evidencia, trazabilidad y estado de las pruebas

| Prueba | Evidencia disponible | Clasificación |
|---|---|---|
| Identificación J1/J2/J3 | Desconexión individual en reposo, movimiento observado; bitácora 2026-10-07 | Observado |
| Resistencia de fases | 15.5 Ω común–fase, ~30–31 Ω fase–fase | Medido |
| Fases negro/amarillo/café/azul | Osciloscopio FNIRSI 2C23T, salidas después del ULN | Interpretación sustentada |
| XIAO + 595 + ULN + J3 | Primer movimiento real del brazo izquierdo | Demostrado en banco |
| J7/J8 p2/p3 | Flancos y ráfagas en retorno a HOME, mediciones con multímetro | Observado |
| Interpretación CLK/DATA de J8 | Sin adquisición simultánea suficiente | Hipótesis, NO demostrado |
| HOME eléctrico como condición segura | No existe validación repetible bajo EGZ | Pendiente |
| Control coordinado de J1/J2/J3 Rev A | Esquema objetivo, no sistema verificado | Pendiente |
| Cinemática XY y sensor Z | No hay calibración completa | Pendiente |

## Registro de prueba recomendado

Guardar cada ejecución con: `ID, fecha, versión de sketch, placa/core, tensión, conector, posición inicial, maniobra, condición final, instrumento, archivo de evidencia, observaciones, anomalías`. Separar **observación**, **hipótesis** y **validación repetida**.

La carpeta `firmware/` incluye los sketches publicados. El [resumen de mediciones](../data/mediciones_resumidas.csv) recoge observaciones de la bitácora. Los datos sintéticos de las pruebas se generan localmente para comprobar los analizadores.
