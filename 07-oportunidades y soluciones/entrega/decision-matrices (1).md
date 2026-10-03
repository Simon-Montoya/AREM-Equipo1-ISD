# Anexo — Matrices de decisión ponderada
#integrantes: Carlos Conde, Simon montoya, Juan Ocampo
## A. Canal de solicitudes y gestión comercial

### Criterios y pesos
- Costo total: 20%
- Facilidad de adopción: 20%
- Seguridad y control: 20%
- Velocidad de implementación: 15%
- Escalabilidad: 15%
- Integración: 10%

### Resultado base
| Alternativa | Puntaje / 5 |
|---|---:|
| Portal web a medida | 3.55 |
| Plataforma low-code | **4.15** |
| Suite CRM | 3.70 |

**Trade-off:** se prioriza velocidad y baja carga operativa frente a libertad máxima de diseño.

### Vínculo con los Talleres 3 y 4
- **Brechas que motivan la decisión:** B03, B04 y B05 (caracterización), B15 (Taller 3: canales sin integración y hoja de cálculo como único registro) y B16 (Taller 4: dependencia de una sola persona).
- **Lectura del C2 (Taller 3):** hoy el seguimiento vive en una hoja de cálculo alimentada por transcripción manual. Las tres alternativas reemplazan ese registro, pero difieren en la operación que exigen.
- **Lectura del mapa (Taller 4):** ISD Colombia es un equipo pequeño y no administra infraestructura propia. Es coherente con ello que velocidad de implementación y facilidad de adopción sumen 35 % de los pesos y que el portal a medida puntúe 2/5 en velocidad. El Taller 4 recomendó centralizar la captura en un formulario o bandeja compartida, lo que encaja con la alternativa low-code.
- **Requisitos a verificar en la plataforma elegida:** versionado y respaldo (B14) y exportación de datos (B17).
- Los pesos y puntajes no cambian con esta incorporación; el vínculo documenta la trazabilidad de la decisión.

## B. Motor de búsqueda y validación

### Criterios y pesos
- Ajuste a especificaciones: 30%
- Integración: 20%
- Mantenibilidad: 20%
- Costo: 15%
- Velocidad: 15%

### Resultado base
| Alternativa | Puntaje / 5 |
|---|---:|
| Motor híbrido reglas + búsqueda semántica | **4.00** |
| Producto/API de terceros | 3.35 |
| Automatización manual asistida | 3.70 |

**Trade-off:** se acepta mayor complejidad inicial para mejorar la verificación de especificaciones y mantener revisión humana.

### Vínculo con los Talleres 3 y 4
- **Brechas que motivan la decisión:** B01 y B02 (caracterización) y B09 (Taller 5).
- **Lectura del C1/C2 (Taller 3):** el proveedor de equipos es un actor externo al que el asesor consulta por canales sin integración (supuesto documentado en el Taller 3). Es coherente con ello que el criterio de integración pese 20 %.
- **Lectura del mapa (Taller 4):** un equipo pequeño sin infraestructura propia es coherente con el peso de mantenibilidad (20 %) y costo (15 %). La opción B (producto/API de terceros) añadiría otra dependencia externa, tema que el Taller 4 catalogó como riesgo de prioridad baja (B17); se gestiona con exportación de datos y contratos, sin alterar el puntaje.
- Los pesos y puntajes no cambian con esta incorporación.

> Los pesos son una propuesta del equipo basada en las prioridades declaradas del cliente y deben ser validados con la Gerencia antes de una decisión de compra/implementación.
