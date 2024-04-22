---
sidebar_position: 4
---

# Manejo de Dependecias

El manejo de depencias en intino es demasiado sencillo. El primer paso es definir el repositorio, donde esta alojado el artefacto:

- Nombre del repositorio.
- Url del repositorio.

**Ejemplo con release repository:**
```kotlin
Repository("iceblue") > Release("https://repo.e-iceblue.cn/repository/maven-public/")
```
**Ejemplo con release y snapshot repository:**
```kotlin
Repository("intersphere-maven")
	Release("http://intersphere.jfrog.io/artifactory/inter-libs-release-local")
	Snapshot("http://intersphere.jfrog.io/artifactory/inter-libs-snapshot-local")
```

Posteriormente agregamos el artefacto usando `Compile`
- GroupId
- ArtifactId
- Version

```kotlin
Compile("e-iceblue", "spire.doc.free", "5.2.0")
```

Tu `artifact.legio` quedaria de la siguiente manera
```kotlin title="artifact.legio"
dsl Legio

Artifact(groupId = "com.intersphere", version = "1.0.0") new-proyect-intino
	Imports
		Test(groupId = "junit", artifactId = "junit", version = "4.13")
		Compile("e-iceblue", "spire.doc.free", "5.2.0")
	Package(mode = ModulesAndLibrariesLinkedByManifest)
Repository("iceblue") > Release("https://repo.e-iceblue.cn/repository/maven-public/")
Repository("intersphere-maven")
	Release("http://intersphere.jfrog.io/artifactory/inter-libs-release-local")
	Snapshot("http://intersphere.jfrog.io/artifactory/inter-libs-snapshot-local")
RunConfiguration local
```