---
draft: false
date: 2019-09-29T21:23:39-05:00
title: "Blog oficial de WEBartisan"
slug: "2019/09/27/blog-oficial-webartisan" 
tags: ["hugo", "golang", "blog"]
categories: []
description: "Cómo se creó este blog usando https://gohugo.io/"
---

Después del vídeo de [Preguntas y Respuestas 2.0](https://www.youtube.com/watch?v=_6_4zdzjvOc) noté que hacía falta un lugar en donde centralizar todas las preguntas y respuestas realizadas en el canal. Muchas de las preguntas se realizan más de una vez y, en más de una ocasión, ya han sido respondidas anteriormente.

## Principales herramientas
Comparé las principales herramientas para crear contenido estático y al final consideré únicamente dos de ellas:


[![Gatsby](https://www.gatsbyjs.org/Gatsby-Logo.svg)](https://www.gatsbyjs.org)

[![HUGO](https://d33wubrfki0l68.cloudfront.net/30790d6888bd8af863fb2b5c33a7f337cdbda243/4e867/images/hugo-logo-wide.svg)](https://gohugo.io/)

Gatsby provee un [link](https://www.gatsbyjs.org/features/jamstack/gatsby-vs-jekyll-vs-hugo/) en el cual hace una comparación de los principales generadores de contenido estático y la realiza en varias categorías, tales como: 

- Performance
- Maintainability and debuggability
- Developer Experience
- Security
- Accessibility
- Documentation
- Ecosystem

Después de ver dicha comparación estaba a nada de usar Gatsby, pero considero que para los fines de este proyecto es un overkill.

Lo único que me interesa de la herramienta es lo siguiente:

1. Que genere contenido estático a partir de archivos Markdown.
2. Que sea rápido
3. Que sea estable
4. Que sea muy fácil de instalar y configurar

Se puede considerar que ambas tienen estas características, pero específicamente HUGO es el más rápido gracias a que está escrito en Go (y no necesitas saber Go para usarlo). Por otro lado si vemos en github, ambos son bastante populares, sin embargo la cantidad de issues que tiene [Gatsby](https://github.com/gatsbyjs/gatsby/issues) es un tanto mayor a los de [HUGO](https://github.com/gohugoio/hugo/issues). No por mucho en realidad, y se debe a diversos factores, pero dicho dato también me fue muy importante al tomar una decisión.

HUGO me pareció lo suficientemente simple y poderoso para las intenciones de este pequeño proyecto.
Definitivamente usaré Gatsby en un futuro, en un proyecto que en verdad lo requiera y poder explotar todo su potencial. Me emociona mucho de hecho poderlo usar, se ve super interesante.

## Instalación
La instalación va a depender de cada sistema operativo. En la página de [Quickstart](https://gohugo.io/getting-started/quick-start/) debería aparecer la forma en que tú deberías instalarlo. 
En el caso de macOS se necesitan algunas dependencias:

- [Homebrew](https://brew.sh/)
- [Git](https://git-scm.com/)

Git lo necesitan todos los sistemas operativos, específicamente para poder agregar temas al proyecto y para poder hacer el CD/CI con now.sh.

Los siguientes pasos también se encuentran en la página de [Quickstart](https://gohugo.io/getting-started/quick-start/), en caso de que tengas dudas adicionales.


### Paso 1: Instala de Hugo:
```bash
brew install hugo
```

### Paso 2: Crea un nuevo sitio:
```bash
hugo new site quickstart
```

### Paso 3: Inicializa el proyecto en git:
```bash
git init
```

### Paso 4: Agrega un tema:
Los temas los podrás encontrar en [https://themes.gohugo.io/](https://themes.gohugo.io/). En este vídeo se eligió [Ezhil](https://themes.gohugo.io/ezhil/). El siguiente comando agregará un submodulo de git llamado ezhil en la carpeta themes.
```bash
git submodule add https://github.com/vividvilla/ezhil.git themes/ezhil
```

### Paso 5: Personaliza la configuración del tema:
```toml
baseURL = "https://blog.webartisan.pw/"
languageCode = "es-ES"
title = "WEBartisan"
theme = "ezhil"

# Enable syntax highlighting.
pygmentsstyle = "vs"
pygmentscodefences = true
pygmentscodefencesguesssyntax = true

# Your Google analytics code.
googleAnalytics = "TU_CODIGO_DE_ANALYTICS"
# Your Disqus sortname.
disqusShortname = "TU_DISQUS_NICKNAME"

# Number of posts to show in recent posts list (Optional). Defaults to 10.
paginate = 20

[params]
    # Blog subtitle which appears below blog title. Supports markdown.
    subtitle = "Building the web!!!"
    # Content types which are included in home page recent posts list.
    mainSections = ["posts"]
    # Content types which are excludes Disqus comments.
    disableDisqusTypes = ["page"]
    # If social media links are enabled then enable this to fetch icons from CDN instead of hosted on your site.
    featherIconsCDN = true

# Main menu which appears below site header.
[[menu.main]]
name = "Inicio"
url = "/"
weight = 1

[[menu.main]]
name = "Posts"
url = "/posts"
weight = 2

[[menu.main]]
name = "About"
url = "/about"
weight = 3

[[menu.main]]
name = "FAQ"
url = "/faq"
weight = 4

[[menu.main]]
name = "Tags"
url = "/tags"
weight = 5

# Social media links which shows up on site header.
# Uses feather icons for icons. You can [search icon names from here](https://feathericons.com/).
[[params.social]]
name = "Github"
icon = "github"
url = "https://github.com/tonirilix/webartisan-yt-channel"

[[params.social]]
name = "Twitter"
icon = "twitter"
url = "https://twitter.com/WebArtisanPW"

# Enable tags.
[taxonomies]
   tag = "tags"
```

### Paso 6: Crea tu primer post:
```bash
hugo new posts/my-first-post.md
```

Este archivo se creará en la carpeta ./content/posts/my-first-post.md

El contenido será parecido a esto:

```md
---
draft: false
date: 2019-09-29T21:23:39-05:00
title: "Blog oficial de WEBartisan"
slug: "2019/09/27/blog-oficial-webartisan" 
tags: ["hugo", "golang", "blog"]
description: "Cómo se creó este blog usando https://gohugo.io/"
---
```

Abajo de esas cabeceras podrás usar la sintaxis de [Markdown](https://www.markdownguide.org/) y deberás configurar la propiedad "draft" a false para que tu artículo se vea en el listado de posts.

**¡Listo! has creado tu propio blog**

## Configurar un repositorio de github para now.sh
*En edición... disculpen guys, tenía mucho sueño XD.*

*En unas horas actualizaré este artículo*