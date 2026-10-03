# Taller 7 — Opportunities & Solutions
## Mejora de arquitectura — IS de Colombia (ISD Colombia)

#integrantes: Carlos Conde, Simon montoya, Juan Ocampo
**Cliente:** IS de Colombia (ISD Colombia)  
**Alcance:** Procesos 01 y 02: búsqueda/selección de equipos y gestión de solicitudes/cotización.  
**Versión:** Borrador académico consolidado con la evidencia disponible al 2026-09-27. Incorpora la evidencia de los Talleres 3 y 4; el Taller 6 queda pendiente.



# 1. Diagnóstico inicial — AS-IS

## 1.1 Contexto

ISD Colombia comercializa y suministra tecnología y desarrolla soluciones a la medida. El levantamiento del cliente identifica como procesos principales la búsqueda y selección de equipos según especificaciones técnicas y la gestión de solicitudes y cotización de clientes. Actualmente la búsqueda de equipos es manual y el contacto con clientes se realiza por canales informales como WhatsApp y redes sociales, sin CRM ni plataforma formal.

La organización tiene como objetivos estratégicos automatizar procesos para ahorrar tiempo y agilizar la operación, y consolidar la comercialización de soluciones adaptadas a las necesidades de cada cliente.

## 1.2 Fricciones

**F1 — Búsqueda manual:** la comparación exige consultar múltiples proveedores y fuentes de Internet y revisar manualmente el cumplimiento de especificaciones.

**F2 — Entrada no estructurada:** las solicitudes llegan por distintos canales y deben ser interpretadas y centralizadas manualmente.

**F3 — Reprocesamiento:** el personal debe convertir información libre en datos utilizables para compras y cotización.

**F4 — Cotización manual:** la salida comercial depende del trabajo de las personas y de la preparación manual de documentos.

## 1.3 Problemas recurrentes

1. Dependencia de actividades manuales.
2. Información distribuida entre canales y personas.
3. Dependencia del conocimiento de los empleados para buscar y validar.
4. Ausencia de una plataforma central para clientes, solicitudes y cotizaciones.
5. Ausencia de trazabilidad tecnológica formal documentada.
6. Riesgo de que la digitalización futura introduzca nuevos problemas de identidad, integridad, confidencialidad y privilegios si se implementa sin seguridad por diseño.

## 1.4 Vulnerabilidades y riesgos

El Taller 5 identificó riesgos STRIDE de suplantación, alteración, repudio, divulgación de información, disponibilidad y elevación de privilegios. En este documento estos hallazgos se tratan como **riesgos identificados**, no como incidentes que se hayan demostrado en ISD.

## 1.5 Brechas consolidadas

La matriz completa está en `matriz-brechas.xlsx`. Las brechas funcionales confirmadas son B01–B06; las B07–B12 proceden del análisis de seguridad (Taller 5); B14–B17 incorporan la evidencia de los Talleres 3 y 4 (ver 1.6); y B13 queda abierta para incorporar el Taller 6.

## 1.6 Trazabilidad con los Talleres 3 y 4

**Taller 3 — C2 AS-IS.** El C2 del cliente muestra que el proceso comercial no tiene sistema propio: WhatsApp Business, correo corporativo y llamada telefónica operan como canales independientes, sin integración automática, y convergen en el asesor comercial, quien transcribe manualmente a una hoja de cálculo compartida (la única infraestructura de soporte). Los actores son el cliente, el asesor comercial y el proveedor de equipos. Esto respalda F2 y F3 y origina **B15**. La ficha del cliente menciona además las redes sociales como canal de entrada; el C2 del Taller 3 no las modela como contenedor.

**Taller 4 — mapa de infraestructura.** El mapa separa tres zonas: clientes/terceros, servicios SaaS externos (WhatsApp, correo, hoja de cálculo) y la zona de ISD Colombia (el dispositivo del asesor). Sus cuatro riesgos priorizados se trasladan a la matriz así:

| Riesgo del Taller 4 | Prioridad en T4 | Brecha en la matriz |
|---|---|---|
| Hoja de cálculo como instancia única, sin backup ni versionado | Alta | B14 |
| Todo el proceso depende de una sola persona | Alta | B16 |
| Información dispersa en 3 canales sin consolidación automática | Media | Refuerza B03, B04 y B15 |
| Dependencia de proveedores externos (Meta, Google/Microsoft) | Baja | B17 |

No se agregan hallazgos nuevos: B14–B17 resumen lo ya diagnosticado en esos talleres. El Taller 6 (B13) sigue pendiente de incorporar.

\newpage

# 2. Propuesta de mejoras

## 2.1 Lluvia de ideas

| ID | Mejora | Horizonte | Cierra |
|---|---|---|---|
| M01 | Portal/formulario formal de solicitudes | Quick win / Fase 1 | B03-B05, B15-B16 |
| M02 | Plataforma ligera de gestión comercial/CRM | Fase 1-2 | B03-B05, B07-B11, B15-B16 |
| M03 | Motor híbrido de búsqueda y validación técnica | Fase 2 | B01-B02, B09 |
| M04 | Generador asistido de cotizaciones | Fase 2-3 | B06-B09 |
| M05 | Repositorio central de documentos | Fase 1-2 | B06-B07, B10, B13-B14 |
| M06 | Seguridad por diseño: IAM, MFA, RBAC y auditoría | Transversal desde Fase 1 | B07-B11 |
| M07 | Monitoreo, backup y recuperación | Fase 1-2 | B10-B12, B14, B17 |
| M08 | Capa de integración/API para terceros y notificaciones | Fase 2-3 | B01, B03, B06, B15 |

La investigación del Taller 4 recomendó tres prácticas para una PYME sin infraestructura propia: respaldo y versionado de los archivos críticos, un único punto de captura de solicitudes (formulario o bandeja compartida) y un proceso documentado que no dependa del conocimiento de una sola persona. M05/M07, M01/M02 y el flujo del TO-BE responden respectivamente a cada una.

## 2.2 Paquetes priorizados

**P1 — Gestión comercial digital.** Canal formal + gestión comercial central + controles de identidad y auditoría.

**P2 — Búsqueda y validación técnica.** Motor híbrido de reglas determinísticas y búsqueda semántica, con revisión humana.

**P3 — Cotización y documentos.** Generación asistida de cotizaciones + repositorio central de documentos.

Los controles de seguridad no se manejan como una mejora aislada: se integran transversalmente en los tres paquetes.

## 2.3 Matriz de decisión ponderada

Para el canal de solicitudes se compararon tres patrones: portal a medida, plataforma low-code y suite CRM. Los criterios y pesos se encuentran en `Decision_Intake` del Excel.

**Resultado preliminar:** la plataforma low-code obtiene 4,15/5 frente a 3,55 del portal a medida y 3,70 de una suite CRM. La sensibilidad de costo, adopción, seguridad y velocidad mantiene a la alternativa B en primer lugar bajo los escenarios ensayados.

**Trade-off:** menor libertad de diseño frente a desarrollo totalmente a medida, a cambio de rapidez y menor carga operativa.

Para búsqueda/validación se compararon motor híbrido, producto/API de terceros y automatización manual asistida. El motor híbrido obtiene 4,00/5. La decisión se basa en el requisito específico de comprobar el 100 % de la especificación y conservar revisión humana.

\newpage

# 3. Arquitectura objetivo (TO-BE)

## 3.1 TO-BE de Aplicaciones

La arquitectura objetivo separa cuatro capacidades:

1. **Canal y gestión comercial:** portal/formulario y plataforma central de solicitudes/clientes.
2. **Búsqueda y validación:** motor que combina reglas determinísticas, búsqueda semántica y consulta a fuentes externas, manteniendo evidencia de las fuentes.
3. **Cotización y documentos:** generador de cotizaciones con plantillas y aprobación humana, más repositorio central.
4. **Servicios transversales:** identidad, RBAC, auditoría, notificaciones y monitoreo.

Flujo objetivo:

`Cliente -> Portal -> Gestión comercial -> Motor de búsqueda/validación -> Cotización -> Aprobación -> Cliente`

**Relación con el C2 del Taller 3.** El TO-BE extiende el C2 AS-IS así:

| Elemento del C2 (Taller 3) | En el TO-BE |
|---|---|
| WhatsApp, correo y llamada como canales independientes | Se mantienen como entradas complementarias en la transición; la solicitud se registra en el portal o la plataforma (M01, M02) |
| Hoja de cálculo compartida como único registro | Plataforma de gestión comercial y repositorio central con versionado (M02, M05) |
| Asesor comercial que transcribe manualmente | Flujo con campos obligatorios y estados; el asesor revisa y aprueba (M01, M04) |
| Proveedor de equipos (actor) | Consultado por el motor de búsqueda/validación y las integraciones (M03, M08) |

La arquitectura propuesta **no automatiza el envío final sin control humano**. El analista conserva la responsabilidad de revisar la evidencia y aprobar la propuesta.

## 3.2 TO-BE de Tecnología

Se propone un patrón cloud-first de baja operación para una organización pequeña, sujeto a validación de costos y restricciones:

- WAF/reverse proxy o entrada segura.
- Aplicación web/API.
- Servicio de identidad con MFA para personal.
- Base de datos relacional administrada.
- Almacenamiento de documentos con cifrado, versionado y permisos.
- Servicio de búsqueda/validación.
- Integraciones/API con proveedores y notificaciones.
- Registro centralizado de auditoría y monitoreo.
- Backups cifrados y pruebas de restauración.
- Gestión segura de secretos.

La seguridad se diseña alrededor de identidad, autenticación y autorización por recurso, coherente con principios de Zero Trust. Para la aplicación web se propone usar ASVS como checklist de requisitos verificables y OWASP API Security Top 10 para las interfaces.

**Relación con el mapa del Taller 4.** El TO-BE conserva la separación por zonas del mapa AS-IS y añade los servicios gestionados listados arriba. Los dos componentes que el Taller 4 marcó como críticos bajo control de ISD (la hoja de cálculo compartida y el dispositivo del asesor) dejan de ser puntos únicos: el registro pasa a una plataforma central con versionado y backups (B14) y el acceso es multiusuario por roles (B16). La dependencia de SaaS externos (B17) se gestiona con exportación de datos y documentación de interfaces.

## 3.3 Controles de seguridad integrados

- MFA para usuarios internos.
- RBAC y mínimo privilegio.
- HTTPS/TLS.
- Validación de entrada.
- Registro de auditoría.
- Versionado de cotizaciones/documentos.
- Cifrado en tránsito y almacenamiento.
- Rate limiting/anti-abuso.
- Gestión de secretos.
- Backups y recuperación.
- Aprobación humana de resultados automatizados.

\newpage

# 4. Gap Analysis, beneficios y riesgos

## 4.1 Resumen de brechas y cierre

| Paquete | Brechas principales | Resultado esperado |
|---|---|---|
| P1 | B03, B04, B05, B07, B08, B10, B11, B15, B16 | Solicitudes estructuradas, historial único, roles y trazabilidad; menor dependencia de una sola persona |
| P2 | B01, B02, B09 | Menor tiempo de búsqueda y validación técnica con evidencia |
| P3 | B06, B07, B09, B10, B13 | Cotización más rápida y documentos controlados |
| Enabler | B12, B14, B17 | Mayor disponibilidad, respaldo y recuperación; dependencia de SaaS gestionada |

## 4.2 Beneficios

**Negocio:** menor tiempo operativo; reducción de reprocesos; respuesta comercial más consistente; mejor seguimiento de solicitudes.

**Aplicaciones:** información centralizada; estados y responsables visibles; reutilización de datos; menor dependencia de documentos aislados.

**Seguridad:** identidad central, mínimo privilegio, auditoría y mejor control de la información.

**Gestión:** posibilidad de medir tiempos de respuesta, volumen de solicitudes y estados del proceso.

## 4.3 Riesgos de implementación y mitigaciones

| Riesgo | Impacto | Mitigación |
|---|---|---|
| Baja adopción del nuevo canal | Medio-Alto | Implantación gradual y mantener transición corta con canales actuales |
| Complejidad del motor de búsqueda | Alto | Empezar con reglas determinísticas + revisión humana |
| Resultados incorrectos de automatización | Alto | Aprobación humana y evidencia de fuentes |
| Mala configuración de permisos | Alto | Matriz RBAC, pruebas de autorización y revisiones periódicas |
| Dependencia del proveedor de plataforma | Medio | Contratos, exportación de datos y documentación de interfaces |
| Costos superiores a lo previsto | Medio | Piloto por fases y validación de costos antes de ampliar |

\newpage

# 5. Roadmap y gobierno de la transformación

## Fase 0 — Validación (antes de comprar o construir)

- C2 del Taller 3 y mapa/riesgos del Taller 4: incorporados en esta versión (secciones 1.6, 3.1 y 3.2).
- Incorporar brechas y obligaciones del Taller 6.
- Validar costos, restricciones, responsables y presupuesto con la Gerencia.
- Definir datos mínimos y política de retención.

## Fase 1 — Quick wins

- Activar versionado y copias de respaldo de la hoja de cálculo actual mientras se migra (recomendación del Taller 4).
- Canal formal de solicitudes.
- Gestión comercial central.
- IAM/MFA/RBAC.
- Auditoría.
- Repositorio controlado.
- Backups y monitoreo.

## Fase 2 — Automatización operativa

- Motor de búsqueda/validación.
- Integraciones seleccionadas con proveedores.
- Generador asistido de cotizaciones.
- Métricas del proceso.

## Fase 3 — Optimización

- Ampliación de automatizaciones.
- Integración con nuevos proveedores.
- Analítica de tiempos y conversión.
- Revisión de costos, rendimiento y seguridad.

## Gobierno

La Gerencia General debe actuar como patrocinador y validador de prioridades. Comercial debe ser dueño funcional del flujo de solicitudes/cotizaciones. Compras debe validar la lógica de búsqueda. TI/Seguridad debe gobernar identidad, permisos, auditoría, continuidad y controles técnicos.

# 6. Conclusiones

El diagnóstico muestra que la principal oportunidad de arquitectura de ISD Colombia no es incorporar tecnología aislada, sino **estructurar el flujo completo de información desde la recepción de la solicitud hasta la cotización**, reduciendo actividades manuales y creando trazabilidad.

El TO-BE propuesto conecta una plataforma de gestión comercial, búsqueda/validación asistida y generación controlada de cotizaciones, con seguridad transversal. La propuesta se diseñó para una empresa pequeña y por ello prioriza servicios gestionados y una implantación gradual, evitando una infraestructura innecesariamente compleja.




## Referencias técnicas y normativas principales

- NIST CSF 2.0: https://www.nist.gov/publications/nist-cybersecurity-framework-csf-20
- NIST SP 800-207 Zero Trust Architecture: https://www.nist.gov/publications/zero-trust-architecture
- OWASP ASVS: https://owasp.org/projects/asvs
- OWASP API Security Top 10: https://api-security.owasp.org/
- SIC - Ley 1581 de 2012: https://sedeelectronica.sic.gov.co/transparencia/normativa/ley-estatutaria-1581-de-2012

## Entregables previos del equipo

- Taller 3 (C4, arquitectura actual) y Taller 4 (mapa de infraestructura y diagnóstico): https://github.com/Simon-Montoya/AREM-Equipo1-ISD
