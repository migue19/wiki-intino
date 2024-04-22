---
sidebar_position: 7
---

# Crear UI Box desde el template

Una manera mas sencilla de tener un **Web UI** es usando el template que nos proporciona Intino:

Seleccionamos `WEB UI` y pulsamos **Crear**.

![Docusaurus logo](/img/intellij-9.png)

Esto crear un `Box Vacio` en cual es necesario `Renombrar`

![Docusaurus logo](/img/box-template.png)

Una vez Renombrado presionamos `Build` lo cual nos creara los archivos necesarios para nuestro modulo **UI**

![Docusaurus logo](/img/box-template-1.png)

Se presiona `Re-Build` para recargar dependecias y sincronizar el proyecto. 

![Docusaurus logo](/img/box-template-2.png)

Para probar este Modulo agregaremos la dependecia de `Spire Doc Free`

```kotlin title="artifact.legio"
dsl Legio

Artifact(groupId = "com.intersphere", version = "1.0.0") intino-web-ui
	Box("Konos", "11.1.3")
	Imports
		Test(groupId = "junit", artifactId = "junit", version = "4.13")
		Web(groupId = "com.intersphere", artifactId = "demo-u-i-elements", version = "1.0.0")
		Compile(groupId = "io.intino.alexandria", artifactId = "core-framework", version = "2.2.0")
		Compile(groupId = "io.intino.alexandria", artifactId = "logger4j", version = "1.0.1")
		Compile(groupId = "io.intino.alexandria", artifactId = "ui-framework", version = "5.1.5")
		Compile("e-iceblue", "spire.doc.free", "5.2.0")
	Package(mode = ModulesAndLibrariesLinkedByManifest) as Runnable(mainClass = "com.intersphere.intinowebui.box.Main")
	Parameter(name = "port")
Repository("iceblue") > Release("https://repo.e-iceblue.cn/repository/maven-public/")
RunConfiguration local
```

Para probar que la dependencia fue agregada correctamente creamos la clase `Test` y agregamos una instancia de `documents`

![Docusaurus logo](/img/box-template-3.png)

Corremos la clase test y notamos como fue agregada correctamente la depencia.

![Docusaurus logo](/img/box-template-4.png)
