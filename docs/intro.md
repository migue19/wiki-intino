---
sidebar_position: 1
---
# INTINO

## ¿Que es Intino?

Intino es una herramienta de desarrollo Java orientada a desarrollar familias de aplicaciones con el uso del editor IntelliJ.

## Empezemos

Intino integra varias herramientas para el desarrollo e implementación de soliciones de software automatizadas.

Soporta la creación de líneas de producción de software que involucran: modelado de plataforma y producto, una arquitectura en capas que incluye interfaz gráfica de usuario, servicios de descanso, persistencia, abastecimiento de eventos e integración continua basada tanto en código fuente como en repositorios de artefactos.

Intino proporciona varios lenguajes específicos de dominio (dsl): 
- **Proteo DSL:** para modelado de productos.
- **Meta DSL:** para modelado de plataformas.
- **Konos DSL:** para modelado de arquitectura en capas.
- **Legio DSL:** para modelado de integración continua.

**Sitio oficial** de **[Intino](https://intino.systems/)**.

### Que necesitamos
- [Toolbox](https://www.jetbrains.com/es-es/) version 2.2 o superior.
- [IntelliJ](https://www.jetbrains.com/idea/download/) version 2024.1 o superior.

![Docusaurus logo](/img/toolbox.png)

## Generate a new site

Generate a new Docusaurus site using the **classic template**.

The classic template will automatically be added to your project after you run the command:

```bash
npm init docusaurus@latest my-website classic
```

You can type this command into Command Prompt, Powershell, Terminal, or any other integrated terminal of your code editor.

The command also installs all necessary dependencies you need to run Docusaurus.

## Start your site

Run the development server:

```bash
cd my-website
npm run start
```

The `cd` command changes the directory you're working with. In order to work with your newly created Docusaurus site, you'll need to navigate the terminal there.

The `npm run start` command builds your website locally and serves it through a development server, ready for you to view at http://localhost:3000/.

Open `docs/intro.md` (this page) and edit some lines: the site **reloads automatically** and displays your changes.
