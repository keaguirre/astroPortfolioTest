apuntes astro
# Instalar node fedora
- <code>sudo dnf module install nodejs:18/common</code>
- Checkear version <code>node --version</code>
# Crear un proyecto en astro
- <code>npm create astro</code>
- Cuando pida la configuracion de TS ponerla en relaxed

- <code> npm run dev</code> para ejecutar el servidor de desarrollo

<code>---<br>
bloque de codigo js a ejecutar para desarrollo<br>
---</code><br>
Con esto podemos setear valores dentro de este bloque de desarrollo como variables
y leerlas dentro de atributos o etiquetas html usando {}<br>

## Ejemplo:
<code>
    ---<br>
    let text = 'lorem ipsum'<br>
    let color = 'blue'<br>
    ---<br>
    
    < h1 class={color}> {text} < /h1>
</code>
Se genera js en las etiquetas script y estilos en styles

# Componentes Astro
## Crear e importar componente
1. Creamos una carpeta components al nivel de pages solo para ser mas ordenados con los componentes.
2. Creamos un archivo [nombre].astro
3. Introducimos el codigo html o js o ambos que queramos usar como componente
4. Vamos a la pagina que quieremos usar el componente y usaremos la etiqueta de desarrollo para importar el componente:<br>
<code>import [como se llamara el componente] from 'ruta ej: ../components/componente1.astro'</code>
5. Usar la etiqueta con el nombre del componente que le dimos para invocar a este.

## Contenido del componente
<code>
---<br>
interface Props{<br>
    title?: string;<br>
    description?: string;<br>
}<br>
const {title = "Titulo repositorio", description = "Descripción repositorio"} = Astro.props<br>
---</code><br>

- Se crea una interfaz para definir de manera estatica los tipos de datos de las variables y luego se define que variables podrán ser pasadas como parámetros mediantes astro.props.<br> en este caso al definirle un texto, este se queda por defecto en caso de que al invocar el componente pero no pasarle parámetros, usará estos valores por defecto.

# Astro Markdown
Astro también puede generar sitios desde archivos markdown, simplemente creando un archivo <code>[nombrePagina/archivo].md</code><br>
## Contenido
<code>
---<br>
Card: ../components/cards.astro<br>
Header: ../components/header.astro<br>
---</code><br>
Para importar en vez de usar import, solo hace basta el <code>[nombre]:[ruta]</code><br> y luego todo el contenido en markdown sin problemas.

# Astro Global [(Doc)](https://docs.astro.build/en/reference/api-reference/#astro-global)
Funcion para precargar multiples archivos estáticos<br>
<code>Astro.glob()</code> Ej:<br>
<code>const posts = await Astro.glob('./posts/*.md)</code><br>
Esto indica que una vez entrado a posts se cargaran todos los archivos md que estan dentro de esa carpeta/ruta