---
sidebar_position: 8
---
# Subscribers y Mounters

## Eventos

Para la definicion de eventos Intino ocupa `Ness` como `DSL`:
```kotlin title="Events.tara"
dsl Ness
Namespace ps
    Event Push
        Attribute id as Text
        Attribute code as Text
```


## Subscriber

Es el mecanismo, para que tu definas en tu box intino `Konos` la subscripcion a un evento, cola o topico de un `Event Manager`. con esta subscripcion puedo escuchar ciertos eventos.

y para subscribirse al evento en nuestro archivo `Box.konos` agregamos la siguiente linea:

```kotlin
Subscriber(event = "ps.Push") pushSubscriber as Durable("monet_push", ReceiveAll)
```

## Mounters

Es donde se pone la logica para actuar sobre un evento recibido.
- Convierte el evento y tiene la lógica para actualizar el estatus o datamart.




