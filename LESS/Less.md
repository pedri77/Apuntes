# Curso de Less<!-- omit in toc -->

## Índice<!-- omit in toc -->
- [Diferencias entre Sass, Stylus y Less](#diferencias-entre-sass-stylus-y-less)
- [Estructura de CSS](#estructura-de-css)
- [Compiladores](#compiladores)
- [Variables](#variables)
  - [Escapar una variable](#escapar-una-variable)
- [Anidaciones](#anidaciones)
- [Mixins](#mixins)
  - [Parametricos](#parametricos)
- [Estructura recomendada](#estructura-recomendada)
- [Funciones](#funciones)
  - [Crear funciones](#crear-funciones)
- [Controles de Flujo](#controles-de-flujo)
- [Enlaces de Interés](#enlaces-de-interés)

## Diferencias entre Sass, Stylus y Less

Existen muchos preprocesadores css. Entre ellos podemos encontrar:

* `Less` es un preprocesador muy simple.
* `Sass` es una herramienta muy interesante gracias a su comunidad.
* `Stylus` es muy completo pero a la vez incluso complejo.

Elegir cuál es el mejor procesador depende de lo que queremos lograr con el proyecto. Algunas de las razones están relacionadas con el equipo y las necesidades que tenemos con el proyecto.

Cuando trabajamos con preprocesadores se tiene que compilar el código para transformarlo en css y las páginas html lo puedan entender.

## Estructura de CSS

La ventaja de los preprocesadores es poder organizar mejor nuestro código CSS. Cada preprocesador tiene una extensión de archivo. En LESS la extensión de los archivos es .less.

Para organizar e importar archivos usamos `@import`.

## Compiladores 

* [CODEKIT](https://codekitapp.com)

* [PREPROS](https://prepros.io)

* [deadsimple-less-watch-compiler](https://github.com/jonycheung/deadsimple-less-watch-compiler)

```
npm install -g less-watch-compiler
```
```
less-watch-compiler <ruta_origen><ruta_destino>"nombre_del_archivo.less"

//example
less-watch-compiler ejemplo/src ejemplo/render/css styles.less

```
La ventaja de los preprocesadores es que podemos modularizar, para ello la estrucutura de nuestros archivos puede ser:

- Carpeta SCSS/LESS/STYLUS
    - Carpeta elements ó base --> que tendrá los componentes HTML
    - Parciales: llevan el prefijo _ nos indican que están siendo compilados en otro lado.
    -  @import "base/tipogragfia.less"
    <small><a href="#Estructura recomendada">🡡 Estructura recomendada </a></small>

 ## Variables

En LESS podemos declarar las variables de la siguiente manera:

```
@atr-sing: valor
```
Atributo-significado
```
@color-brand: red;
@color-secondary: rgb(213,216,121);
```
es importante el en las variables

Para llamar a la variable:
```
@variable
```
Existen muchas variables que podemos crear para nuestros proyectos. Algunos ejemplos pueden ser:
@color-brand
@color-border
Igualar las variables:
@color-border: @color-brand

## Anidaciones

Nesting, podemos agregar pseudoselectores (tales como :hover) dentro de la clase general, con el caracter & referenciamos al padre.(anidación en castellano).

Un ejemplo pueden ser los botones:

_botones.less

```
.btn{
	//properties
	&:hover{
		//properties
	}
}
```

Con -- podemos indicar una modificación en un elemento.

```
&--alert {}

```

## Mixins

Crear un Mixins, es mezclar selectores o reutilizar selectores en base a otros.
Es muy similar a una clase ya que utiliza un punto . y despues un ():

```
.mixin-nombre(){
    width: 100%;
    background-color: red;
}
```
Archivo LESS
```
body{
	.mixin-nombre
}
```
Archivo CSS
```
body{
	.mixin-nombre
}
```

### Paramétricos

Archivo _variables.styl

```
@maxWidthDefault:1024px;

.mixinMaxWidth(@maxWidth: @maxWidthDefault){
	max-width: @maxWidth;
}
```
Archivo style.less
```
section{
	.mixinMaxWidth(80%)
}

.section{
	.mixinMaxWidth()
}
```
Archivo style.css
```
section {
  max-width: 80%;
}
.section {
  max-width: 1024px;
}
```

## Estructura recomendada


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
styless.less
SCSS contiene las carpetas:
- Base
Contiene los archivos: _botones.less; _tablas.less; _tipografía.less
- Components
Contiene los archivos: _grid.less; _utilities.less
- Layout 
Contiene los archivos: _layout.less
- Lib
Contiene los archivos: _mixins.less; _variables.less

- Ejemplo en Style-Less-Estructura-CSS

## Funciones
Un ejemplo:

```
@colorDefault: gray;
@colorModify: darken(@colorDefault, 60%);

```
Multiplicar, sumar, etc 

* [Funciones](http://lesscss.org/functions/)

### Crear funciones

Creamos una propiedad con una función darken (variable, porcentaje):

```
@colorModify: darken(@colorDefault, 60%);
```

Más complicado:

```
@some: foo;

div {
    margin: if((2 > 1), 0, 3px);
    color:  if((iscolor(@some)), darken(@some, 10%), black);
}
```
- Algunos ejemplos:

    - Sumar o restar

    @color: #fff - #000

    - Aclarar un color
    ```
    @colorDefault: gray;
    @color = lighten(@colorDefault, 80%);
    ```
    - Aumentar opacidad

    ```
    @colorDefault: gray;
    @color = darken(@colorDefault, 80%);
    ```

    - Saturar color
    ```
    @colorDefault: gray;
    @color = saturate(@colorDefault, 80%);
    ```
    - Desaturar un color
    ```
    @colorDefault: gray;
    @color = desaturate(@colorDefault, 80%);
    ```

    - (Ruleta) Girar un color
    ```
    @colorDefault: gray;
    @color = spin(@colorDefault, 80);
    ```
## Controles de Flujo

- Control de flujo con una condicion

```
.condicional (@size) when (@size =< 1024px){
	width: 100%;
}

.article{
	.condicional(800px);
}
```
- Control de flujo con dos condicionales

```
.condicional (@size) when (@size =< 1024px){
	width: 100%;
}

.condicional (@size) when (@size > 1024px){
	width: auto%;
}

.article{
	.condicional(2200px);
}
```
- Escapar una expresión en less

```
width: calc(~"50% - 12px");
```

## Enlaces de Interés
* [Diseno Web Wordpress](https://www.disenowebwordpress.com/blog)
* [Platzi LESS](https://platzi.com/cursos/less/)
* [Documentación oficial LESS](http://lesscss.org/#docs)

<div align="right">
  <small><a href="#Índice">🡡 volver al inicio</a></small>
</div



