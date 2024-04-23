---
sidebar_position: 2
---
# Centinela

## Definicion

Un Centinela es un mecanismo que funciona por medio del patron observador y como su nombre lo indica se encarga de vigilar y escuchar los eventos que ocurran en nuestra aplicación.

**Intino ocupa la palabra reservada `Sentinel` para definir a este elemento**

Ejemplo:

```kotlin
Sentinel doActionOnStartAnd5Minutes as BootListener ClockListener(pattern = "0 0/5 * 1/1 * ? *", mean = "Every 5 minutes and on start")
```

**Tipos de Listeners**
- **BootListener:** Un listener que se ejecuta al arrancar la aplicacion.
- **ClockListener:** Un listener que se ejecuta cada sierto periodo de tiempo.
- **FileListener:** Un listener que se ejecuta al arrancar la aplicacion.