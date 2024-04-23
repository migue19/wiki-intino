---
sidebar_position: 1
---
# Box

## ¿Que es un Box en Intino?

Para intino un `Box` es una caja o envoltura la cual representa la estructura y definicion de lo que queremos realizar.
- Entradas
- Salidas
- Puerto
- Host

Es importante mencionar que la deficion de este Box en intino es escrito utilizando el DSL Konos

![Docusaurus logo](/img/conceptos.png)

**Nota:** para terminos practicos en un proyecto intino es importante que exista un `Box` definido con `Konos DSL` el cual se encargara de gestionar las entradas de salidas de nuestra solucion.

Una vez definido nuestro box al dar click en en el boton `Build` intino se encargara de contruir los archivos necesarios para realizar esta tarea.

![Docusaurus logo](/img/conceptos-1.png)

Como se puede observar intino crea 
- Las clases `GetExampleAction` y `PostExampleAction`
- La clase `DoActionOnStartAnd5MinutesAction`
- La clase `ListenDirectoryAction`

## Analicemos un poco el codigo

Definición de la url del servicio REST

```kotlin
Service(title = "Example API") example-api as REST(host = "{host}", basePath = "/api/v1", port = "{port}")
	Resource("/example") example
```
Intino creará un endpoint de este tipo. 
```
http://localhost:8080/api/v1/example
```
Para la defición del servicio intino creara un archivo `Action` con el Prefijo del metodo HTTP: `Get` `Post`

```kotlin title="GetExampleAction.java"
public class GetExampleAction implements io.intino.alexandria.rest.RequestErrorHandler {
	public mx.intershere.mailsender.box.MailSenderBox box;
	public io.intino.alexandria.http.spark.SparkContext context;
	public String filter;

	public List<String> execute() throws BadRequest, NotFound {
		// todo: implement logic.
		Logger.info("Executing GetExampleAction with filter " + filter);
        return List.of("example1", "example2");
	}

	public void onMalformedRequest(Throwable e) throws AlexandriaException {
		//TODO
		throw new BadRequest("Malformed request");
	}
}
```

**Parametros de Entrada:**

Definicion en Konos
```kotlin
Parameter(in = query, isRequired = false) filter as Text
```

Codigo generado:
```java
public String filter;
```
**Parametros de Salida:**

Definicion en Konos
```kotlin
Response as Text
Exception(BadRequest)
Exception(NotFound)
```

Codigo generado:
```java
public String execute() throws BadRequest, NotFound {
    // todo: implement logic.
    Logger.info("parameters are: " + filter);
    return List.of("val1", "val2", "val3");
}
```

