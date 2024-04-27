---
sidebar_position: 9
---
# Model

El modelado, es una de las cosas principales al empezar a construir una solución.

Es la definicion de clases, entidades o estructuras que se utilizaran en el proyecto.

para este caso utilizamos un `DSL` llamado `Proteo`

```kotlin title="Model.tara"
dsl Proteo

Entity Employee
    Attribute base as String
    Attribute foreman as String
    Attribute name as String
```