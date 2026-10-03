# DFD — Proceso 02: Gestión de solicitudes y cotización de clientes

```mermaid
flowchart LR
    C["Cliente"]

    subgraph ISD["IS de Colombia — Límite organizacional"]
        P1["P1: Recepción de solicitud"]
        P2["P2: Centralización y estructuración<br/>de información"]
        P3["P3: Identificación de solución<br/>tecnológica"]
        P4["P4: Elaboración de cotización"]
        D1[("D1: Información de solicitudes")]
        D2[("D2: Cotizaciones y propuestas")]
    end

    C -->|"F1: Solicitud del cliente<br/>(WhatsApp, redes, correo)"| P1
    P1 -->|"F2: Datos de la solicitud"| P2
    P2 -->|"F3: Requerimiento estructurado"| P3
    P3 -->|"F4: Solución / especificaciones"| P4
    P2 -->|"F5: Registro de solicitud"| D1
    P4 -->|"F6: Registro de cotización"| D2
    P4 -->|"F7: Cotización"| C
    C -->|"F8: Retroalimentación"| P1
```

## Nota de modelado

D1 y D2 son **almacenes lógicos de información**. La documentación disponible del cliente no establece que actualmente exista una base de datos o aplicación formal equivalente. Esto evita confundir el estado actual manual con una arquitectura futura aún no definida.
