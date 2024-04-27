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

**Implementacion**

```Kotlin title="JMX.konos"
Service crawlerJmx as JMX
    Operation(description= "Test conection to device") testDevice
        Parameter deviceIp as Text
        Parameter version as Text
        Response as Text
```

Intino creara la clase:

```Kotlin title="TestDeviceAction.java"
public class TestDeviceAction {
	public MailSenderBox box;
	public io.intino.alexandria.Context context = new io.intino.alexandria.Context();
	public String deviceIp;
	public String version;

	public String execute() {
		return null;
	}
}
```
**Ejecutar jmx en un servidor:**

Para este procesos ejecutamos un cliente JMX

```bash
java -jar jmxterm-1.0.2-uber.jar
```
posteriormente abrimos la conexion:

```kotlin
open localhost:10006 
```
Creamos nuestro MBean personalizado:

```kotlin
bean Konos:name=Operations,type=io.provista.cosmos.box.jmx.OperationsMBean
```

Si ejecutamos el comando info el programa listará:
- atributos
- operaciones

![image](/img/jmx-1.png)

Para ejecutar una operacion de la lista ocupamos el comando `run`:

```
run help
```