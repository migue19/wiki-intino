---
sidebar_position: 3
---
# JMX

Las Java Management Extensions (JMX) se introdujo en Java 1.5 y ha encontrado una amplia aceptación en la comunidad de desarrolladores de Java desde sus inicios.

Proporciona una infraestructura fácilmente configurable, escalable, fiable y más o menos amigable para la gestión de aplicaciones Java ya sea de forma local o remota. El framework introduce el concepto de MBeans para la gestión en tiempo real de las aplicaciones.
<div style={{textAlign: 'center'}}>
![image](/img/jmx.png)
</div>

**JXM** te permite `Monitoreas`, `Leer`, `Grabar` o `Lanzar` operaciones creando un **Bean** personalizado en tiempo de ejecucion.

Esto quiere decir que mientras esta corriendo tu aplicaciones, tu puedes extraer, consultar modificar o si asi lo deseas eliminar datos en tiempo real.

**Ejemplo:**

Tenemos definido un arreglo de mensajes que al llegar a 50 mensajes hace el `flush` del arreglo.
Utilizando JMX podemos modificar el parametro del numero de mensajes a 10 si asi lo necesitamos.

