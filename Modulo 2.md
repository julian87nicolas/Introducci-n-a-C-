# Contenido del módulo
* [Condicionales](#condicionales)
* [Tipos de datos](#tipos-de-datos)
    * [Otros tipos de floats](#otros-tipos-de-floats)
    * [Bits](#bits)
    * [Estructuras](#estructuras)
# Condicionales
El lenguaje C++, permite la siguiente estructura `if-else`:
```cpp
if(the_weather_is_good)
    go_for_a_walk();
else if(tickets_are_available)
    go_to_the_theater();
else if(table_is_available)
    go_for_lunch();
else
    play_chess_at_home();
``` 
# Tipos de datos
Para especificar nuestros requerimientos de memoria, podemos usar algunas palabras claves llamadas *modificadores*:
* **`long`** - usado para declarar que necesitamos un rango más amplio de enteros que el `int` estandar.
* **`short`** - usado para determinar que necesitamos un rango más estrecho de enteros que el `int` estandar.
* **`unsigned`** - usado para declara que una variable es usada solo apra números no negativos.

Estos modificadores pueden usarse justo antes del int o solos sin el int posterior:
```cpp
short int counter
```

Es lo mismo que:
```cpp
short counter
```
Sucede lo mismo con `long` y `unsigned`.

Además pueden usarse combinados, es decir:
```cpp
unsigned short int lambs;
```
Lo cual es igual a:
```cpp
unsigned short lambs;
```

## Otros tipos de floats
Los modificadores `long` y `short` no pueden ser usados junto con `float` pero esto no significa que el tipo float no tenga otras variables. De hecho, tenemos al menos dos de ellas: `double` y `long double`. Las variables de tipo `double` y `long double` pueden diferir de las variables de tipo `float`, no solo en **rango** sino también en **precisión**.

## Bits
| Simbolo | Operación |
|---------|-----------|
|   `&`	  |  bitand   |
|	`|`   |  bitor    |
|   `~`	  |  compl (as in compliment) |
|   `^`	  |  xor |

## Estructuras
Una estructura contiene cualquier número de elementos de cualquier tipo. Cada uno de estos elementos se denomina campo. Cada campo se identifica por su nombre, no por su número. Obviamente, los nombres de los campos deben ser únicos y no pueden duplicarse dentro de una misma estructura. Vamos a mostrar cómo declarar una estructura adecuada a nuestras necesidades y explicaremos su significado.

Vemos la declaración de una estructura en el siguiente código:
```cpp
struct Student {
  string name;
  float time_spent;
  int recent_chapter;
};
```

* La delcaración de la estructura siempre comienza con la palabra clave `struct`.
* Nuestra estructura tiene tres campos: el primero es una cadena y se llama `name`; el segundo es un float y se llama `time_spent`; el tercero es un int y se llama `recent_chapter`.
* La declaración termina con la llave de cierre seguida de un punto y coma.
