---
sidebar_position: 6
---

# Crear Box

En esta ocasion crearemos un nuevo UI Box


Lo primero que debemos hacer es agregrar el tipo de Box que queremos integrar al proyecto en este caso será `Konos`
en el archivo `Artifact`
```kotlin title="artifact.legio"
dsl Legio

Artifact(groupId = "com.intersphere", version = "1.0.0") new-proyect-intino
    Box("Konos", "11.0.5")
	Imports
		Test(groupId = "junit", artifactId = "junit", version = "4.13")
	Package(mode = ModulesAndLibrariesLinkedByManifest)
RunConfiguration local
```

Una vez agregado el box y recargar las dependencias, se nos habilitara el panel Box en el menú `Nuevo`

![Docusaurus logo](/img/box.png)

Agregamos el nombre del nuevo `Box`.

![Docusaurus logo](/img/box-1.png)

Definimos un nuevo servicio llamado `EjemploUIElements` con los argumentos `puerto`, `titulo` y `favicon`.

![Docusaurus logo](/img/box-2.png)

Para que intino pueda crear los archivos del nuevo Servicio es necesario construir el modulo.

![Docusaurus logo](/img/box-3.png)

Intino se encarga de crear los archivos necesarios para nuestro `UI Box`

![Docusaurus logo](/img/box-6.png)

**Nota:** Al construir el modulo el `IDE` nos mostrara el siguiente error.

![Docusaurus logo](/img/box-4.png)

Esto es por que intino actualizo nuestro `artifact.legio`

```kotlin title="artifact.legio"
dsl Legio

Artifact(groupId = "com.intersphere", version = "1.0.0") new-project-intino
	Box("Konos", "11.0.5")
	Imports
		Test(groupId = "junit", artifactId = "junit", version = "4.13")
		Web(groupId = "com.intersphere", artifactId = "ejemplo-u-i-elements", version = "1.0.0")
		Compile(groupId = "io.intino.alexandria", artifactId = "core-framework", version = "2.2.0")
		Compile(groupId = "io.intino.alexandria", artifactId = "logger4j", version = "1.0.1")
		Compile(groupId = "io.intino.alexandria", artifactId = "ui-framework", version = "5.1.5")
	Package(mode = ModulesAndLibrariesLinkedByManifest) as Runnable(mainClass = "com.intersphere.newprojectintino.box.Main")
RunConfiguration local
```

Y es necesario re-construir el modulo para actualizar las dependencias.

![Docusaurus logo](/img/box-5.png)

Ahora nos muestra un nuevo error por que no encuentra la carpeta `resources` y es necesario crearla

![Docusaurus logo](/img/box-7.png)

Debe de quedar de la siguiente manera

![Docusaurus logo](/img/box-8.png)
