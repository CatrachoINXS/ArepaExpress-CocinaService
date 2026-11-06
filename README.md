<div align="center">

  <h1>cocina-service</h1>

  <p align="center">
    <strong>Cristian Camilo Ortiz Sánchez</strong><br />
    DOSW 1 · Semana 14<br />
    Escuela Colombiana de Ingeniería Julio Garavito<br />
    cristian.ortiz-s@mail.escuelaing.edu.co
  </p>

  <p align="center">
    <strong>Arepa Express · API Gateway y RabbitMQ en Azure</strong><br />
    <em>Microservicio que representa la cocina y prepara los pedidos que llegan por RabbitMQ.</em>
  </p>

</div>

---

## Descripción

- No recibe llamadas HTTP: escucha los pedidos nuevos desde su propia cola de RabbitMQ.
- Consume los eventos desde la cola `cocina.pedidos`, unida al exchange `arepas.eventos` con el binding `pedido.*`.
- Simula la preparación de las arepas (3 segundos) y registra en el log cuando el pedido queda listo.
- Su ingress es interno y se mantiene con una réplica siempre encendida para no dejar de leer la cola.

## Tecnologías

- Java 21
- Spring Boot 3.5.9 (Spring Web, Spring for RabbitMQ)
- Maven
- RabbitMQ
- Docker

## Estructura

```
domain/
└─ model/                PedidoCreadoEvent
infrastructure/
├─ adapter/in/messaging/ CocinaListener
└─ config/               RabbitConfig
```

## Contexto

Forma parte de Arepa Express junto con `menu-service`, `pedidos-service` y `notificaciones-service`.
