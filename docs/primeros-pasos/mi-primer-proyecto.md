---
sidebar_position: 2
---

# Mi Primer Proyecto Intino

1.- Abir intelliJ y seleccionar Nuevo Proyecto:

![Docusaurus logo](/img/intellij-2.png)

2.- Seleccionar Intino en la parte de Templates:
    - Agregar nombre del proyecto.
    - Ubicacion donde guardar el proyecto.
    - Identificador del Grupo.
    - Nombre del Artefacto.
    - Seleccionar la version de JDK.

![Docusaurus logo](/img/intellij-3.png)

3.- En **Tipo de Modulo** seleccionamos Bussiness y dar click en el boton **Crear**.

![Docusaurus logo](/img/intellij-4.png)

4.- Al entra al proyecto, te mostrar el archivo `artifact.legio`:
```kotlin title="artifact.legio"
dsl Legio

Artifact(groupId = "com.intersphere", version = "1.0.0") new-proyect-intino
	Imports
		Test(groupId = "junit", artifactId = "junit", version = "4.13")
	Package(mode = ModulesAndLibrariesLinkedByManifest)
RunConfiguration local
```