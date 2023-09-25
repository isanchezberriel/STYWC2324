# Introducción a Sass
* CSS más limpio y flexible, facilita el mantenimiento.
* Reduce la repetición, es más productivo que CSS
* Características para especificar estilos de forma modular.
* No son reconocidos por el navegador, necesitamos instalar el procesador y generarlo antes del despliegue.

Usaremos la sintaxis SCSS

## Instalación:

```ruby
sudo apt-get install ruby

$ sudo gem install sass

$ sass -v
 ```
### Herramienta: 
Para realizar los ejercicios se puede usar la herramienta: https://www.sassmeister.com/

## Variables
```ruby 
$nombre: valor
 ```
## Listas 
Sass permite definir las listas de varias maneras: 
* Conjunto de valores separados por , ó espacios. 
* Conjunto de valores entre paréntesis separados por , ó espacios.
* Conjunto de valores entre corchetes separados por espacios
Acceso a un elemento:  nth($list_name, index);
```ruby
$list-1: "Segoe UI",sans-serif;
$list-2: 10px 12px 10px 20px;
$list-3: ("Segoe UI",sans-serif);
$list-4: (10px 12px 10px 20px);
$list-5: [grid-line1 grid-line2];
```
```ruby
$list-2: 10px 12px 10px 20px;
$nth3 nth($list_name, index);
```
## Mapas 
* Un mapa es similar a una lista pero que admite indexación clave:valor
* Sintaxis: $map_name: ("key":value, "key":value);
* Acceso a un elemento: map-get(map_name, key);
```ruby
$font-weight: ("light": 300, "regular": 400, "bold": 700);
```

### Ámbito:
El ámbito de las variables, es el del nivel en el que esté incluida. Las variables al inicio son globales. Las variables anidadas se pueden convertir a globales con !

 ## Operadores
* Matemáticos: 
```ruby 
+, -, *, /, %
 ``` 
* Referencia a su elemento padre.
```ruby
&: 
```
 ## Anidamiento

Sass permite anidar selectores como en HTML. También se puede simplificar la sintaxis de propiedades con el mismo prefijo mediante anidamiento. 
```ruby
prefijo
{
	sufijo1: valor1
	sufijo2: valor2
}
```

### Ejemplo:
```ruby
ul {
  li {
    margin: 0;
    padding: 0;
    list-style: none;
    display: inline-block;
  }
  a {
    display: block;
    padding: 6px 12px;
    text-decoration: none;
  }
}
```
### Resultado:
```ruby
ul li {
  margin: 0;
  padding: 0;
  list-style: none;
  display: inline-block;
}
ul a {
  display: block;
  padding: 6px 12px;
  text-decoration: none;
}
```
### Ejemplo:
```ruby
.alert, .warning {
  ul, p {
    margin: {
    right: 0;
    left: 0;
    }
    padding-bottom: 0;
  }
}
```
### Resultado:
```ruby
.alert ul, .alert p, .warning ul, .warning p {
  margin-right: 0;
  margin-left: 0;
  padding-bottom: 0;
}
```
Experimenta a eliminar los : después de margin
## Organización del código:

### Mixings
Crear fragmentos de código
```ruby
@mixin name {
  property: value;
  property: value;
  ...
} 
```
Se utilizan con ```@include```
### Ejemplo:
```ruby
@mixin list-reset {
  margin: 0;
  padding: 0;
  list-style: none;
}

ul {
  @include list-reset;
}
```
### Resultado:
```ruby
ul {
  margin: 0;
  padding: 0;
  list-style: none;
}
```
### Import
Se utiliza para recursos css: ``` @import ``` 
No supone peticiones adicionales al servidor, se transpila todo el código en el css junto con el código Sass del fichero que lo contiene.

### Herencia
Se usa para estilos que son compartidos, en su mayoría, y que se aplican con alguna diferencia según qué elemento:
* Declarar el estilo base 
* Incorporarlo en el estilo que hereda con ``` @extend ```
* También se puede usar con ```%nombre_estilo```
### Ejemplo:
```ruby
.error {
  border: 1px #f00;
  background-color: #fdd;
}

.error--serious {
  @extend .error;
  border-width: 3px;
}
```
### Resultado:
```ruby
.error, .error--serious {
  border: 1px #f00;
  background-color: #fdd;
}

.error--serious {
  border-width: 3px;
}
```
## Funciones
* Color: set, get o manipulación
```ruby
rgb(red, green, blue), rgba(red, green, blue, alfa), 
hsl(hue, saturation, lightness), hsla(hue, saturation, lightness, alpha), 
grayscale(color), 
mix(color1, color2, weight), adjust-color(color, red, green, blue, hue, saturation, lightness, alpha), … 
```
* Cadenas:
``` ruby 
quote(string), str-length(string), str-index(string, substring), to-lower-case(string), ... 
```
 * Números:
```ruby
abs(number), ceil(number), comparable(num1, num2), max(number...), ...
```
## Sentencias de Control

### if-else
``` ruby 
@if condition-1 {
  //Se ejecuta el código
  //si la condición es verdadera
}
@else if condition-2 {
  // si no, se evalúa condición 2
  // se ejectua esta regla si condición 2 es verdadera
}
@else if condition-3 {
  // ---
}
```
### Bucles: @for @each @while
``` ruby 
@for $counter from number through number {
  // código a ejecutar en cada iteración
}
```
``` ruby 
@while condition {
  // código a ejecutar en cada iteración
  //si se cumple condition
}
```
``` ruby 
@each temp_variable in list {
  // código a ejecutar para 
  //cada valor en la lista
```
## Ejemplo
``` ruby 
@for $i from 1 to 4 {
 .font-size-#{$i} {
      font-size: #{$i}px;
    line-height: #{$i + 2}px;
}
  
}

```

## Resultado
``` ruby 
.font-size-1 {
  font-size: 1px;
  line-height: 3px;
}

.font-size-2 {
  font-size: 2px;
  line-height: 4px;
}

.font-size-3 {
  font-size: 3px;
  line-height: 5px;
}
```
## Ejemplo:
``` ruby 
$font-size: 16;

@while $font-size <= 24 {

  .font-size-#{$font-size} {
    font-size: #{$font-size}px;
    line-height: #{$font-size + 2}px;
  }

  $font-size: $font-size + 3;
}

```
## Resultado
``` ruby 
.font-size-16 {
  font-size: 16px;
  line-height: 18px;
}

.font-size-19 {
  font-size: 19px;
  line-height: 21px;
}

.font-size-22 {
  font-size: 22px;
  line-height: 24px;
}
```
## Ejemplo:
``` ruby 
$font-sizes: (16, 18, 20, 22);

@each $size in $font-sizes {

  .font-size-#{$size} {
    font-size: #{$size}px;
    line-height: #{$size + 2}px;
  }
}
```
## Resultado
``` ruby 
.font-size-16 {
  font-size: 16px;
  line-height: 18px;
}

.font-size-18 {
  font-size: 18px;
  line-height: 20px;
}

.font-size-20 {
  font-size: 20px;
  line-height: 22px;
}

.font-size-22 {
  font-size: 22px;
  line-height: 24px;
}
```


## Ejercicios

1. Instalar Sass en la máquina del pool TWFE

```
$ sudo apt-get install ruby

$ sudo gem install sass

$ sass -v
```
2. Escribir el código Sass que simplifique las reglas CSS:
```css
header {
    background-color: #531946;
  }
  .header a {
    color: #fff;
  }
  .header a:hover {
    color: #095169;
  }
  
  .footer {
    background-color: #30162B;
    color: #fff;
  }
  .footer a {
    color: #095169;
  }
  .footer a:hover {
    color: #fff;
  }
  
  .feature a {
    background-color: #30162B;
    color: #fff;
  }
  
  .feature a:hover {
    color: #531946;
  }
  
  .content {
    background-color: #fff;
    color: #222;
  }
```
3. Escribir el código Sass más simplificado posible que genere:

```css
.header {
    background-color: #531946;
    border-radius: 5px;
    padding: 5px 20px;
  }
  .header a {
    color: #fff;
  }
  .header a:hover {
    color: #095169;
  }
  
  .footer {
    background-color: #30162B;
    color: #fff;
    border-radius: 5px;
    padding: 5px 20px;
  }
  .footer a {
    color: #095169;
  }
  .footer a:hover {
    color: #fff;
  }
  
  .feature a {
    background-color: #30162B;
    color: #fff;
    border-radius: 5px;
    padding: 5px 20px;
  }
  .feature a:hover {
    color: #531946;
  }
  
  .content {
    background-color: #fff;
    color: #222;
    border-radius: 5px;
    padding: 5px 20px;
  }
```
4. Dado el código HTML a continuación, escribir el código Sass para los estilos css que se incluyen:
```html
<nav class="navigation">
  <ul>
    <li><a href="#">Home</a></li>
    <li><a href="#about">About</a></li>
    <li><a href="#contact">Contact</a></li>
  </ul>
</nav>
```

Código CSS esperado:

```css

.navigation {
  float: right;
}
.navigation li {
  display: inline-block;
  list-style-type: none;
  margin-left: 1.5em;
}
.navigation a {
  display: block;
  text-decoration: none;
}
```

5. Crear el código Sass adecuado para obtener el CSS a continución:
```ruby
 a {
    color: #beedee;
  }
  
  a:hover {
    color: #cbbebb;
  }
  
  a.btn {
    background: #deede6;
  }
  
  a .btn {
    display: block;
  }
```
6. Crear el código Sass más estructurado posible que genere el código CSS:

```css
header {
    border-radius: 5px;
    padding: 5px 20px;
  }
  
  .footer {
    border-radius: 5px;
    padding: 5px 20px;
  }
  
  .feature a {
    border-radius: 5px;
    padding: 5px 20px;
  }
  
  .content {
    border-radius: 5px;
    padding: 5px 20px;

  }
  ```
  
 7. Crear el código Sass más estructurado posible que genere el código CSS:

```css
  .header {
    -webkit-border-radius: 5px;
       -moz-border-radius: 5px;
            border-radius: 5px;
    /* ... */
  }
  
  .footer {
    -webkit-border-radius: 10px;
       -moz-border-radius: 10px;
            border-radius: 10px;
    /* ... */
  }
 ```
 

