---
sidebar_position: 2
---
# Centinela

## Definicion

Intino ocupa la palabra reservada `Sentinel` para definir a este elemento

Ejemplo:

```kotlin
Sentinel doActionOnStartAnd5Minutes as BootListener ClockListener(pattern = "0 0/5 * 1/1 * ? *", mean = "Every 5 minutes and on start")
```