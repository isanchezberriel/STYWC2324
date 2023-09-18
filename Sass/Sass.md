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

Simplificar sintaxis de propiedades con el mismo prefijo mediante anidamiento. Sass permite anidar selectores como en HTML
```ruby
prefijo
{
	sufijo1: valor1
	sufijo2: valor2
}
```
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

### Import
Se utiliza para recursos css: ``` @import ```

### Herencia
Se usa para estilos que son compartidos, en su mayoría, y que se aplican con alguna diferencia según qué elemento:
* Declarar el estilo base 
* Incorporarlo en el estilo que hereda con ``` @extend ```
* También se puede usar con ```%nombre_estilo```

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
 

