# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 4 - Mapa de Infraestructura y Diagnóstico Técnico_

## 👥 Integrantes del equipo
- Juan Ocampo
- Simon Montoya
- Carlos Conde

## 🧠 Descripción general del trabajo
El objetivo del taller fue construir el mapa de infraestructura del sistema del cliente real (ISD Colombia) y realizar un diagnóstico de debilidades, cuellos de botella y oportunidades de mejora, siguiendo la metodología de 5 pasos de la guía del curso. A diferencia del caso base de RedExpress (infraestructura propia distribuida en la nube), la infraestructura real de ISD Colombia es prácticamente inexistente como infraestructura propia: se apoya por completo en servicios SaaS de terceros y en el dispositivo de una sola persona.

## 🔧 Proceso de desarrollo
Se partió del C2 construido en el Taller 3, que ya identificaba los tres canales (WhatsApp Business, Correo Corporativo, Llamada Telefónica) y la hoja de cálculo compartida como infraestructura de soporte. Para este taller se agregaron los componentes de dispositivo (el equipo del Asesor Comercial, los dispositivos de clientes y proveedores) y se agruparon por zona: **Zona Clientes/Terceros** (fuera del control de ISD Colombia), **Zona Servicios en la Nube/SaaS Externos** (WhatsApp, correo, hoja de cálculo — alojados por Meta, Google/Microsoft) y **Zona ISD Colombia** (el único dispositivo interno de la empresa para este proceso).

Se conectaron los componentes según el tráfico real (mensajería por internet, correo por SMTP/IMAP, llamadas por red telefónica, acceso a la hoja de cálculo por HTTPS) y se marcó la redundancia de cada componente crítico: ninguno tiene redundancia propia, ya que ISD Colombia no administra infraestructura propia — la redundancia de WhatsApp/Correo depende del proveedor externo, mientras que el dispositivo del Asesor Comercial y la hoja de cálculo son instancias únicas bajo control directo de la empresa.

## 🧩 Análisis del modelo propuesto
- **Cómo se estructura el modelo:** El mapa separa claramente lo que está bajo control de ISD Colombia (el dispositivo del Asesor Comercial) de lo que depende de terceros (WhatsApp, correo, hoja de cálculo en la nube, red telefónica, dispositivos de clientes/proveedores). Los dos únicos componentes marcados en rojo (⚠️) son los que sí dependen directamente de la empresa: el dispositivo del Asesor Comercial y la hoja de cálculo compartida.
- **Cómo representa las necesidades del cliente:** Refleja que, al ser una empresa de 5 empleados sin sistema propio, el mayor riesgo de infraestructura de ISD Colombia no es tecnológico (los servicios SaaS que usa tienen alta disponibilidad) sino organizacional: toda la trazabilidad del negocio depende de una sola persona y un solo archivo.
- **Supuestos tomados:** Se asumió que el dispositivo del Asesor Comercial (PC + celular) es el único punto de acceso interno a los tres canales y a la hoja de cálculo, ya que no se identificó ningún otro rol o sistema de respaldo en el Taller 2 ni en el Taller 3.

## 📈 Diagrama final entregado
> Ver `mapa-final.drawio` en esta misma carpeta (`entrega/`).

## 📋 Tabla de diagnóstico priorizado

| Riesgo | Categoría | Componente afectado | Impacto | Prioridad |
|---|---|---|---|---|
| Instancia única sin backup ni control de versiones | Disponibilidad | Hoja de Cálculo Compartida | Pérdida de historial de cotizaciones y solicitudes | Alta |
| Todo el proceso depende de una sola persona | Escalabilidad | Dispositivo del Asesor Comercial | Cuello de botella: no escala si crece la demanda o si la persona no está disponible | Alta |
| Información dispersa en 3 canales sin consolidación automática | Rendimiento / Trazabilidad | WhatsApp, Correo, Teléfono | Reprocesos, demoras y riesgo de inconsistencia entre canales | Media |
| Dependencia de disponibilidad de proveedores externos (Meta, Google/Microsoft) | Disponibilidad | WhatsApp Business, Correo Corporativo | Fuera del control directo de ISD Colombia, aunque con SLA robusto | Baja |

## 🔍 Investigación complementaria
### Tema investigado:
Buenas prácticas de continuidad operativa para procesos comerciales en PYMES que dependen de herramientas SaaS sin infraestructura propia.

### Resumen:
La investigación exploró cómo pequeñas empresas sin infraestructura de TI propia pueden reducir riesgos de disponibilidad y escalabilidad sin necesidad de construir servidores propios. Las recomendaciones más consistentes apuntan a: (1) automatizar backups periódicos de archivos críticos en la nube (versionado nativo de Google Sheets/OneDrive), (2) centralizar la captura de solicitudes en un único formulario o bandeja de entrada compartida para reducir la dispersión entre canales, y (3) documentar el proceso para que no dependa del conocimiento tácito de una sola persona. Estas prácticas son directamente aplicables al diagnóstico de ISD Colombia, ya que atacan exactamente los dos riesgos de prioridad alta identificados en la tabla anterior, sin requerir inversión en infraestructura propia.

## 📚 Referencias
Ver `referencias.md` en esta misma carpeta.

---

_Este documento hace parte de la entrega del Taller 4 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
