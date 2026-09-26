# 📄 Informe Técnico del Taller

## 🔖 Nombre del Taller
_Taller 3 - Arquitectura Actual del Sistema con el Modelo C4_

## 👥 Integrantes del equipo
- Juan Ocampo
- Simon Montoya
- Carlos Conde

## 🧠 Descripción general del trabajo
El objetivo del taller fue representar la arquitectura actual del sistema del cliente real (IS de Colombia — ISD Colombia) mediante las vistas C1 (Contexto) y C2 (Contenedores) del modelo C4. Primero se construyó el ejercicio guiado en clase sobre el caso base de RedExpress siguiendo la metodología de 4 pasos por vista, y luego se aplicó la misma metodología al sistema real del cliente, que corresponde a los Procesos 01 (búsqueda y selección de equipos) y 02 (gestión de solicitudes y cotización de clientes) ya delimitados en el Taller 2.

## 🔧 Proceso de desarrollo
Se partió del hallazgo clave del Taller 2: ISD Colombia no cuenta con un sistema de software propio para sus procesos comerciales, sino que opera de forma manual apoyándose en herramientas de terceros. Con base en esto se decidió modelar en el C1 el proceso comercial como el "sistema en alcance" (una sola caja, como pide la notación), identificando como actores al Cliente, al Asesor Comercial de ISD Colombia y al Proveedor de Equipos, y como sistemas externos las herramientas que el proceso usa hoy: WhatsApp Business, correo electrónico corporativo, la hoja de cálculo compartida de seguimiento y la red telefónica.

Para el C2 se descompuso ese "sistema" en los canales/contenedores que efectivamente lo componen (WhatsApp Business, Correo Corporativo, Llamada Telefónica) y se ubicó la hoja de cálculo compartida como la infraestructura de soporte (equivalente a la "base de datos" del caso base), ya que es allí donde se centraliza el seguimiento de solicitudes y cotizaciones. Se usó draw.io para ambos diagramas, manteniendo la paleta de colores de la leyenda de notación (persona = óvalo azul, sistema en alcance = rectángulo azul oscuro, sistema externo = rectángulo gris de doble borde, contenedor = rectángulo azul claro, infraestructura = cilindro gris).

## 🧩 Análisis del modelo propuesto
- **Cómo se estructura el modelo:** El C1 aísla el proceso comercial como una única caja y deja explícito que su "arquitectura" depende enteramente de herramientas externas (mensajería, correo, hoja de cálculo, telefonía), no de un sistema propio. El C2 abre esa caja y muestra que no hay integración automática entre canales: cada uno es independiente y converge en el Asesor Comercial, quien transcribe manualmente la información a la hoja de cálculo compartida.
- **Cómo representa las necesidades del cliente:** El modelo refleja fielmente que ISD Colombia, al ser una empresa de 5 empleados sin sistema propio, gestiona sus dos líneas de negocio (suministro de equipos e instalación de seguridad/automatización) con canales informales. Esto es coherente con el alcance definido en el Taller 2 (procesos manuales, sin inventario propio).
- **Supuestos tomados:** Se asumió que el Asesor Comercial es quien concentra la interacción con clientes y proveedores por los tres canales (WhatsApp, correo, teléfono) y quien registra manualmente el resultado en la hoja de cálculo compartida, ya que el Taller 2 documentó que la gestión de solicitudes ocurre "hoy por canales informales" sin un responsable de sistematización definido.

## 📈 Diagrama final entregado
> Ver `c1-contexto-final.drawio` y `c2-contenedores-final.drawio` en esta misma carpeta (`entrega/`).

## 📋 Tabla de actores, entidades o componentes

| Nombre del elemento | Tipo | Descripción | Responsable |
|---------------------|------|-------------|-------------|
| Cliente | Actor | Empresa corporativa, propiedad horizontal o la Embajada Americana que solicita cotización o equipos | Cliente |
| Asesor Comercial | Actor | Persona de ISD Colombia que atiende, cotiza y hace seguimiento a las solicitudes | ISD Colombia |
| Proveedor de Equipos | Actor | Tercero consultado para especificaciones, precio y disponibilidad de equipos | Proveedor |
| Gestión Comercial ISD Colombia | Sistema en alcance | Proceso comercial actual (Procesos 01 y 02), manual | ISD Colombia |
| WhatsApp Business | Sistema externo / Contenedor | Canal de mensajería instantánea con clientes y proveedores | Meta (tercero) |
| Correo Corporativo | Sistema externo / Contenedor | Canal para especificaciones técnicas y cotizaciones formales | Gmail/Outlook (tercero) |
| Llamada Telefónica | Sistema externo / Contenedor | Canal de voz para confirmar detalles | Operador móvil (tercero) |
| Hoja de Cálculo Compartida | Sistema externo / Infraestructura de soporte | Registro y seguimiento de solicitudes y cotizaciones | ISD Colombia (alojado en Excel/Google Sheets) |

## 🔍 Investigación complementaria
### Tema investigado:
Arquitecturas C4 en pequeñas empresas comercializadoras/distribuidoras de tecnología con procesos comerciales no digitalizados.

### Resumen:
La investigación se centró en cómo el modelo C4, pensado originalmente para sistemas de software, se adapta a procesos donde el "sistema" es en realidad un flujo de trabajo manual apoyado en herramientas SaaS de terceros (mensajería, correo, hojas de cálculo). Este patrón es común en PYMES colombianas del sector de comercialización de tecnología, donde la ausencia de un CRM o ERP propio hace que la trazabilidad de cotizaciones dependa de la disciplina de registro de una sola persona. Documentar esta arquitectura "as-is" con C4, aunque no describa software propio, es útil porque expone con claridad los puntos de fricción (falta de automatización, dependencia de un solo canal de registro) que luego se retoman en el diagnóstico del Taller 4 de Infraestructura.

## 📚 Referencias
Ver `referencias.md` en esta misma carpeta.

---

_Este documento hace parte de la entrega del Taller 3 del curso AREM (Arquitectura Empresarial) - Universidad de La Sabana._
