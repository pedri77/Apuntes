# Curso de Stylus<!-- omit in toc -->

## Índice<!-- omit in toc -->
- [Diferencias entre Sass, Stylus y Less](#diferencias-entre-sass-stylus-y-less)
- [Estructura de CSS](#estructura-de-css)
  - [Estructura recomendada](#estructura-recomendada)
- [Compiladores](#compiladores)
- [Sintaxis](#sintaxis)
- [Variables](#variables)
  - [Escapar una variable](#escapar-una-variable)
- [Anidaciones](#anidaciones)
- [Mixins](#mixins)
  - [Parametricos](#parametricos)
- [Funciones internas](#funciones-internas)
  - [Crear funciones](#crear-funciones)
- [Condicionales](#condicionales)
  - [Directiva for](#directiva-for)
- [Enlaces de Interés](#enlaces-de-interés)

## Diferencias entre Sass, Stylus y Less

Existen muchos preprocesadores css. Entre ellos podemos encontrar:

* `Less` es un preprocesador muy simple.
* `Sass` es una herramienta muy interesante gracias a su comunidad.
* `Stylus` es muy completo pero a la vez incluso complejo.

Elegir cuál es el mejor procesador depende de lo que queremos lograr con el proyecto. Algunas de las razones están relacionadas con el equipo y las necesidades que tenemos con el proyecto.

Cuando trabajamos con preprocesadores se tiene que compilar el código para transformarlo en css y las páginas html lo puedan entender.

## Estructura de CSS

Archivo para variables: _variables.styl .
Archivo con un '_' no compila.
Todos los preprocesadores usan este tipo de nomenclatura.
Los referenciamos de la siguiente manera: `@import` .
```
@import "_variables.styl"
```
Lo deseable es un solo archivo para compilar.

### Estructura recomendada

```
styles.less
_grid.less
_tablas.less
_layout.less
_utilities.less
_mixins.less
_botones.less
_variabless.less
_tipografia.less

```

------Carpetas CSS y SCSS------

CSS contiene los archivos: style.css y styles.css.map
styless.styl

SCSS contiene las carpetas:
- Base
Contiene los archivos: _botones.styl; _tablas.styl; _tipografía.styl
- Components
Contiene los archivos: _grid.styl; _utilities.styl
- Layout 
Contiene los archivos: _layout.styl
- Lib
Contiene los archivos: _mixins.styl; _variables.styl

## Compiladores

* [CODEKIT](https://codekitapp.com)

* [PREPROS](https://prepros.io)

* [grunt-styl](https://www.npmjs.com/package/grunt-styl)
* [ember cli less preprocess](https://www.npmjs.com/package/ember-cli-css-preprocess)

* [Webpack] (https://platzi.com/clases/webpack/)

## Sintaxis

Su sintaxis es anidada.
En Stylus no es necesario usar los brackets y ; pero debemos recordar que para tener mejores prácticas deberíamos usarlas.

En CSS 

```
body {
  background: #lightyellow;
}
```

En Stylus

```
body
  background: lightyellow
```

## Variables
Una de las mayores ventajas que tienen los preprocesadores son las variables, estas nos permiten controlar un entorno porque podemos manipular un entorno. Esto quiere decir que podemos cambiar muchas cosas a través de muchas variables.

Para declarar una variables en Stylus:

```
nombre_variable = valor_variable
```
EJEMPLOS:

```
// Variables
font-size-normal = 18px
font-size-small = font-size-normal - 2px
font-size-paragraph = font-size-normal

// Texts
p
  font-sizefont-size-paragraph

span
  font-sizefont-size-normal

  &.small
    font-sizefont-size-small
```
```
color_theme = background black

body
  background color_theme
  
.box
    background color_theme
    &--light
        background color_theme

```
* [Variables](http://stylus-lang.com/docs/variables.html)

## Anidaciones
Gracias a las anidaciones podemos añadir propiedades a través de la sintaxis de Stylus. Además, esto nos permite referenciar al padre.

SUB
```
body, .light-theme
  background lightyellow
  color#2c2c2c

  .primer-hijo
    margin-bottom24px
```
CHILD. Con el uso de '>' hacemos referencia a los hijos del elemento padre.
```
body, .light-theme
  background lightyellow
  color#2c2c2c

  > .primer-hijo
    margin-bottom24px
```
REFERENCE: Con el uso de '&' hacemos referencia al nombre del elemento padre.
```
.psudoe-element
  width300px

  &:before
    content'hola'
  
  .ie-8 &
    &:before
      content'ciao'
```
NOTA: No anidar mas de 3 veces
EJEMPLO DE MODULACIÓN
```
.btn
  background white
  color black
  border-radius3px

  &-alert
    background red
    color white

  &-warn
    background orange
    color white
```
## Mixins
Un mixin nos permite reutilizar valores dentro del mismo CSS
Se declara facilmente con su nombre, y como buena práctica usamos minxin- antes del nombre que queremos darle

<code>mixin-NOMBRE():</code>

```
mixin-max-width():
	max-width 800px
	margin-left auto
	margin-right auto
```
Se aplica de la siguiente manera

```
.container
  max-width()
```

[Mixins Stylus](http://stylus-lang.com/docs/mixins.html)

### Parametricos

Darle un parámetro al mixin. Poniendolo dentro del paréntesis:

```
mixin-max-width(width)
```
Cuando le usamos hay que darle el parámetro:
```
.container
    mixin-max-width(800px)
```
También podemos usarlo así:
```
page-max-width = 1024px;
mixin-max-width(width=page-max-width)
```

## Funciones internas

En stylus podemos asignar variables dinamicas y asignarles funciones matematicas que ejecutaras cada que sean llamadas .

Por ejemplo podremos utilizar la declaracion.

```
**padding : mixin-padding-small(2px)**
```
Ubicada en la carpeta site.styl

y pasarle la la función:
```
mixin-padding-small(a)

	**a + padding**
```
Ubicada en la carpeta mixin.styl

Donde padding proviene de la carpeta ** _variables.styl**

y equivale a :

```
**minipadding = padding / 2**
```
[Funciones Stylus](http://stylus-lang.com/docs/functions.html)

## Condicionales
Stylus cuenta con condicionales if que vienen muy útiles a la hora de asegurarnos que algo tiene un valor y que se ejecute algo si eso se cumple.

```
toggleTheme = true

theme(themeSelected = toggleTheme)
    if themeSelected
    	background-color black
    	color white
    else
    	background-color white
    	color black

.area
	theme()
```

[Condcionales Stylus](http://stylus-lang.com/docs/conditionals.html)

### Directiva for





## Enlaces de interes

* [Stylus](http://stylus-lang.com)
* [Cheatsheet](https://devhints.io/stylus)
* [Variables](http://stylus-lang.com/docs/variables.html)
* [CODEKIT](https://codekitapp.com)
* [PREPROS](https://prepros.io)
* [grunt-styl](https://www.npmjs.com/package/grunt-styl)
* [ember cli less preprocess](https://www.npmjs.com/package/ember-cli-css-preprocess)
* [Webpack] (https://platzi.com/clases/webpack/)

