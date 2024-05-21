---
sidebar_position: 8
---
# Apéndices


Los apéndices proporcionan información adicional y recursos útiles que complementan el contenido principal del curso sobre el Intino Framework. A continuación se presentan las secciones de los apéndices, que incluyen referencias rápidas, recursos adicionales, y un glosario de términos.

#### Apéndice A: Referencias Rápidas

**A.1. Sintaxis de Legio DLS**

| Elemento          | Sintaxis de Legio                           | Descripción                            |
|-------------------|---------------------------------------------|----------------------------------------|
| Definición de Entidad | `entity NombreEntidad { ... }`            | Define una entidad.                    |
| Atributo          | `Tipo nombreAtributo;`                      | Define un atributo dentro de una entidad. |
| Clave Primaria    | `@Id Tipo nombreAtributo;`                  | Define un atributo como clave primaria.|
| Validación de Rango | `@Range(min=valorMin, max=valorMax) Tipo nombreAtributo;` | Define un rango de valores permitidos. |
| Herencia          | `entity SubEntidad extends EntidadPadre { ... }` | Define una entidad que hereda de otra.  |
| Regla de Negocio  | `rule NombreRegla { ... }`                  | Define una regla de negocio.           |

**Ejemplos:**

```legio
// Definición de una entidad con atributos y validaciones
entity Cliente {
    @Id int id;
    String nombre;
    @NotNull String direccion;
    @Range(min=18, max=99) int edad;
}

// Herencia entre entidades
entity Empleado extends Persona {
    double salario;
}

// Regla de negocio
rule validarEdad {
    Cliente.edad >= 18;
}
```

**A.2. Comandos del Generador de Código**

| Comando                 | Descripción                                 |
|-------------------------|---------------------------------------------|
| `intino generate`       | Genera el código a partir de los modelos definidos en Legio. |
| `intino generate-ui`    | Genera componentes de interfaz de usuario a partir de los modelos definidos. |
| `intino clean`          | Limpia el proyecto eliminando archivos generados previamente. |

#### Apéndice B: Recursos Adicionales

**B.1. Documentación Oficial**

- [Documentación de Intino Framework](https://www.intino.io/documentation)
- [Guía de Usuario de Legio DLS](https://www.intino.io/legio-dls-guide)

**B.2. Herramientas y Plugins**

- **IDEs Recomendados**:
  - [Eclipse IDE](https://www.eclipse.org/)
  - [IntelliJ IDEA](https://www.jetbrains.com/idea/)

- **Plugins**:
  - [Intino Plugin para Eclipse](https://www.intino.io/eclipse-plugin)
  - [Intino Plugin para IntelliJ IDEA](https://www.intino.io/intellij-plugin)

**B.3. Comunidad y Soporte**

- [Foro de la Comunidad de Intino](https://community.intino.io)
- [Grupo de Discusión en Slack](https://slack.intino.io)

#### Apéndice C: Glosario de Términos

**C.1. Términos Clave**

- **Intino Framework**: Un marco de desarrollo de software que facilita la creación de aplicaciones empresariales mediante un enfoque dirigido por modelos (MDD).
- **Legio DLS**: Lenguaje específico del dominio utilizado en el Intino Framework para definir modelos de dominio.
- **Entidad**: Representa un objeto o concepto del mundo real en el dominio de la aplicación.
- **Atributo**: Una propiedad o característica de una entidad.
- **Clave Primaria (@Id)**: Un atributo que identifica de manera única a cada instancia de una entidad.
- **Validación (@Range, @NotNull)**: Reglas que aseguran que los datos cumplan con ciertos criterios.
- **Regla de Negocio**: Define lógica de validación y comportamiento que deben cumplir los datos de las entidades.
- **Generación de Código**: Proceso de crear automáticamente código fuente a partir de los modelos definidos en Legio DLS.
- **Persistencia de Datos**: Técnica para almacenar datos de manera permanente en una base de datos.
- **Interfaz de Usuario (UI)**: Componentes visuales que permiten a los usuarios interactuar con la aplicación.
- **Servicios Web (API)**: Interfaces que permiten la comunicación entre diferentes sistemas de software.

**C.2. Abreviaturas Comunes**

- **MDD**: Model-Driven Development (Desarrollo Dirigido por Modelos).
- **DLS**: Domain Specific Language (Lenguaje Específico del Dominio).
- **API**: Application Programming Interface (Interfaz de Programación de Aplicaciones).
- **CRUD**: Create, Read, Update, Delete (Crear, Leer, Actualizar, Eliminar).
- **CI/CD**: Continuous Integration/Continuous Deployment (Integración Continua/Despliegue Continuo).

### Resumen

Estos apéndices proporcionan información adicional y recursos útiles para complementar los conocimientos adquiridos en el curso sobre el Intino Framework. La referencia rápida a la sintaxis de Legio DLS y los comandos del generador de código, junto con los recursos adicionales y el glosario de términos, ayudarán a los desarrolladores a trabajar de manera más eficiente y efectiva con el Intino Framework.