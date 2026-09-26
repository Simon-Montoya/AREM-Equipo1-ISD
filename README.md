# AREM - Equipo 1 - ISD Colombia

Proyecto académico de Arquitectura Empresarial desarrollado para ISD Colombia S.A.S., una empresa de tecnología y seguridad ubicada en Bogotá.

## Contexto real del proyecto

Este repositorio no corresponde a una solución financiera o bancaria, sino a un diagnóstico arquitectónico de una PyME colombiana que gestiona sus procesos comerciales, técnicos y contables de forma mayoritariamente manual.

La empresa opera con un equipo pequeño (aproximadamente 5 personas) y no cuenta con un CRM, ERP o sistema propio para centralizar la gestión de solicitudes, cotizaciones, seguimiento de proyectos y registro de facturas. La información se mueve principalmente por WhatsApp, correo electrónico, llamadas telefónicas y hojas de cálculo compartidas, y las facturas deben terminar registrándose en SIGOO.

## Objetivo del trabajo

Documentar, analizar y representar la arquitectura actual del negocio para identificar:

- puntos de fricción operativos,
- dependencia de canales informales,
- riesgos de trazabilidad y continuidad operativa,
- oportunidades de mejora en procesos comerciales, contables e infraestructura.

## Alcance del proyecto

El trabajo está centrado en los siguientes aspectos:

- caracterización del cliente y su contexto empresarial,
- mapeo de procesos de negocio con BPMN,
- modelado de información,
- arquitectura actual del sistema con enfoque C4,
- diagnóstico de infraestructura,
- identificación de riesgos y recomendaciones.

## Estructura del repositorio

- 00-preliminary-vision/: visión preliminar, ficha de caracterización y referencias.
- 01-bpmn/: modelado de procesos de negocio y análisis BPMN.
- 02-modelo-informacion/: modelo de información del dominio del problema.
- 03-arquitectura-c4/: arquitectura actual del sistema en vistas C1 y C2.
- 04-infraestructura/: mapa de infraestructura y diagnóstico técnico.
- 05-seguridad/: análisis y consideraciones de seguridad.
- 06-normatividad/: marco normativo y cumplimiento.

## Problema principal identificado

El desafío central es la gestión manual de solicitudes, cotizaciones y facturas, junto con la dispersión de la información entre distintos canales y herramientas externas. Esto genera:

- pérdida de trazabilidad,
- dependencia de una sola persona,
- duplicidad de trabajo,
- riesgo de errores en la contabilidad,
- dificultad para escalar procesos sin digitalización.

## Enfoque del entregable

La entrega busca reflejar la realidad del cliente según la evidencia recopilada: un negocio real, pequeño, con procesos informales y con necesidad de fortalecer su operación a través de una mejor estructura, documentación y visión arquitectónica.

---

Este repositorio forma parte de la entrega académica del curso AREM - Arquitectura Empresarial, Universidad de La Sabana.