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
hugo new site blog.webartisan
```

### Paso 3: Inicializa el proyecto en git:
```bash
git init
```

### Paso 4: Agrega un tema:
Los temas los podrás encontrar en [https://themes.gohugo.io/](https://themes.gohugo.io/). En este vídeo se eligió [Ezhil](https://themes.gohugo.io/ezhil/). El siguiente comando clonará un repositorio  de git llamado ezhil en la carpeta themes.
```bash
git clone https://github.com/vividvilla/ezhil.git themes/ezhil
```

En el vídeo lo hice con submodule pero me dio problemas al momento de agregar el proyecto a github. Así que recomiendo mejor este proceso.

### Paso 5: Personaliza la configuración del tema:
La siguiente es la configuración que tiene el tema en el repositorio de github, puedes personalizarlo a tu gusto. 
La propiedad baseURL la configuraremos más adelante cuando subamos el proyecto a now.sh. Mientras tanto puedes dejarla con el default.

```toml
# Your now.sh domain. You can leave it with http://localhost:1313/
# For local purposes
baseURL = "http://localhost:1313/"
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

Este archivo se creará en la carpeta ```./content/posts/my-first-post.md```

El contenido será parecido a esto, puedes copiar el siguiente texto para fines de prueba:

```md
---
draft: false
date: 2019-09-29T21:23:39-05:00
title: "Blog oficial de WEBartisan"
slug: "2019/09/27/blog-oficial-webartisan" 
tags: ["hugo", "golang", "blog"]
description: "Cómo se creó este blog usando https://gohugo.io/"
---

Estas son las instrucciones para crear un blog como este:

## Referencias
[Página principal de Hugo](https://gohugo.io/)

```

Abajo de esas cabeceras podrás usar la sintaxis de [Markdown](https://www.markdownguide.org/) y deberás configurar la propiedad "draft" a false para que tu artículo se vea en el listado de posts.

**¡Listo! has creado tu propio blog**

## Configurar un repositorio de github para now.sh
Necesitarán tener una cuenta creada en [now.sh](https://zeit.co/signup). Recomiendo que la creen conectándose a github.

### Paso 1: Crea un repositorio en github
![Crea un repositorio](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/01-create-github-account.png)

![Repositorio creado](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/03-created-repo.png)

### Paso 2: Clona el repositorio en tu local

Primero copia la url de tu repositorio.
![Clona el repositorio](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/04-copy-repo.png)

La forma más fácil de inicializar el repositorio sería únicamente clonar el proyecto y copiar los archivos generados por hugo ahí dentro. El siguiente comando es la forma en que clonarías el proyecto, con tu propia url:

```bash
git clone git@github.com:tonirilix/blog.webartisan.git
```

*Pero en el vídeo no lo hicimos así, por lo que los siguientes son los pasos a seguir para conectar tu carpeta local al repositorio de github*

Cuando generamos el proyecto con hugo, ejecutamos el comando ```git init```el cuál lo inicializó como un proyecto de git. Sin embargo lo hizo únicamente local, no está apuntando a ningún repositorio remoto.

Para conectar el repositorio local con el repositorio remoto, ejecutamos el siguiente comando usando tu url:

```bash
git remote add origin git@github.com:tonirilix/blog.webartisan.git
```

Después necesitamos descargar las ramas que están configuradas en el repositorio remoto, en este caso es únicamente master. Así que ejecutamos:

```bash
git fetch origin
```

Y después necesitamos que nuestra rama local ```master``` se vincule a la rama master del repositorio remoto, así que ejecutamos:

```bash
git checkout master
```

Esto nos mandará un mensaje como este indicanto que ya está haciendo tracking de la rama remota:

```bash
blog.webartisan on  master [+?]
➜ git checkout master
A	.gitmodules
A	themes/ezhil
Branch 'master' set up to track remote branch 'master' from 'origin'.
Already on 'master'
```

Ahora necesitamos agregar a la raiz del proyecto un archivo de nombre ```package.json``` en el que pondremos las intrucciones que now.sh necesita para poder correr nuestro proyecto.
Básicamente las instrucciones de instalación indican a now.sh que tiene que descargar Hugo como dependencia, después extraerlo con permisos de ejecución y en las instrucciones de compilado le indican que debe ejecutar ./hugo. De esa forma aseguramos que cada que se haga un nuevo deploy nuestro proyecto se compile con la versión apropiada de Hugo. El contenido del archivo es el siguiente:

```json
{
    "name": "blog.webartisan-test",
    "version": "0.1",
    "scripts": {
        "install": "curl -L -O https://github.com/gohugoio/hugo/releases/download/v0.58.3/hugo_0.58.3_Linux-64bit.tar.gz && tar -xzf hugo_0.58.3_Linux-64bit.tar.gz",
        "build": "./hugo"
    }
}
```

Por último necesitamos agregar un archivo .gitignore, para que github no haga tracking de los archivos compilados por hugo y tampoco de otros archivos de configuración.

```.gitignore
_site
.sass-cache
.DS_Store
Gemfile.lock
*.sublime-project
*.sublime-workspace
codekit-config.json
node_modules
_asset_bundler_cache
.vscode
public
```

Si ejecutamos ```git status``` deberíamos ver algo como esto:

![git status](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/06-git-status.png)

Ahora necesitamos agregar todos archivos nuevos al stage de git, pero debemos tener cuidado ya que el tema está agregado como un repositorio dentro de nuestro repositorio y, si lo subimos de esa forma now.sh no va a saber qué hacer con ese submódulo (de hecho cualquiera que descargue el proyecto).
Entonces agreguemos primero la carpeta de themes de la siguiente forma para que git sepa que deseamos agregarla como directorio:

```
git add themes/
```
Una vez hecho esto agreguemos el resto de los archivos con:
```
git add .
```

Si por alguna razón no agregaste los temas como en el paso indicado, el warning que te arroja la consola te indica como remover themes nuevamente.
```
warning: adding embedded git repository: themes/ezhil
hint: You've added another git repository inside your current repository.
hint: Clones of the outer repository will not contain the contents of
hint: the embedded repository and will not know how to obtain it.
hint: If you meant to add a submodule, use:
hint:
hint: 	git submodule add <url> themes/ezhil
hint:
hint: If you added this path by mistake, you can remove it from the
hint: index with:
hint:
hint: 	git rm --cached themes/ezhil
hint:
hint: See "git help submodule" for more information.
```

Ahora creamos el commit de los archivos a actualizar en nuestro repo:
```bash
git commit -m "Initial blog files"
```
![commited files](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/07-git-commit.png)

Y subimos el commit al repositorio remoto:
```bash
git push
```

Y si todo salió bien, nuestros archivos ya deberían estar en el repositorio remoto:
![remote repo](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/08-files-in-repo.png)

## Configurando now.sh para escuchar nuestro repositorio
Primero deberás crear una cuenta en [now.sh](https://zeit.co/signup). Te recomiendo que te conectes vía github para que sea más fácil conectarnos con nuestro repositorio. Una vez que crees tu cuenta, continua con los siguientes pasos:

## Paso 1: Crea un nuevo proyecto, elige Github como fuente.
![new project](https://s3.amazonaws.com/blog.webartisan/20190927blog-oficial-webartisan/09-now-sh.png)

Selecc
```bash
Installing build runtime...
Build runtime installed: 668.375ms
Looking up build cache...
Installing dependencies...
yarn install v1.17.3
info No lockfile found.
[1/4] Resolving packages...
[2/4] Fetching packages...
[3/4] Linking dependencies...
[4/4] Building fresh packages...
success Saved lockfile.
$ curl -L -O https://github.com/gohugoio/hugo/releases/download/v0.58.3/hugo_0.58.3_Linux-64bit.tar.gz && tar -xzf hugo_0.58.3_Linux-64bit.tar.gz
  % Total
    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   
Spent    Left  Speed

  0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0

  0     0    0     0    0 
    0      0      0 --:--:-- --:--:-- --:--:--     0
100   620    0   620    0     0   3147      0 --:--:-- --:--:-- --:--:--  3147

 32 11.1M   32 3641k    0     0  3353k      0  0:00:03  0:00:01  0:00
:02 3353k

100 11.1M  100 11.1M 
   0     0  7756k      0  0:00:01  0:00:01 --:--:-- 19.8M
Done in 1.79s.
Running "yarn run build"
yarn run v1.17.3
$ ./hugo
Building sites … 

                   | EN  
+------------------+----+
  Pages            | 13  
  Paginator pages  |  0  
  Non-page files   |  0  
  Static files     |  4  
  Processed images |  0  
  Aliases          |  1  
  Sitemaps         |  1  
  Cleaned          
|  0  

Total in 10 ms
Done in 0.08s.
Build completed. Populating build cache...
Build cache uploaded [305 B]: 450.947ms
done
```


```toml
baseURL = "https://blogwebartisantest.tonirilix.now.sh/"
```


```
git commit -m "Modify baseUrl"
```

```
git checkout -b dev
```

```
git push -u origin dev
```

