---
sidebar_position: 2
---
# Mi primer servicio

## Creando mi primera definición de servicio

```kotlin title="Box.konos"
Service(title = "Example API") example-api as REST(host = "{host}", basePath = "/api/v1", port = "{port}")
    Resource("/reports") example
	    Get(description = "Get sales reports", tags = "reporte ventas")
                Parameter(in = query, isRequired = true) division as Text
                Parameter(in = query, isRequired = true) zona as Text
                Parameter(in = query, isRequired = true) aniomes as Text
                Response as Text
                Exception(BadRequest)
                Exception(NotFound)
```

URL obtenida:
```kotlin
http://localhost:8080/api/v1/reports
```

Clase `Action` generada

```kotlin title="GetExampleAction.java"
public class GetExampleAction implements io.intino.alexandria.rest.RequestErrorHandler {
	public String aniomes;
	public String zona;
	public String division;
	public mx.intershere.mailsender.box.MailSenderBox box;
	public io.intino.alexandria.http.spark.SparkContext context;
	public String filter;

	public String execute() throws BadRequest, NotFound {
		// todo: implement logic.
		Logger.info("parameters are: " + aniomes + " " + zona + " " + division);
        return String.join(",", List.of("val1", "val2", "val3"));
	}

	public void onMalformedRequest(Throwable e) throws AlexandriaException {
		//TODO
		throw new BadRequest("Malformed request");
	}
}
```
Para ejecutar el codigo generado demos correr la clase Main

![Docusaurus logo](/img/service.png)

Si no se define un puerto por defecto intino utilizara el puerto `8080``

![Docusaurus logo](/img/service-1.png)