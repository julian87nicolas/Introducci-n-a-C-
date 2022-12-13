# Contenido del módulo

* [Nuestro primer programa](#nuestro-primer-programa)
* [Conexion con el mundo real: inputs](#conexion-con-el-mundo-real-inputs)
	* [Manipulators](#manipulators)
* [Conexino con el mundo real: outputs](#conexion-con-el-mundo-real-outputs)
# Nuestro primer programa
Comenzamos viendo el siguiente programa:
```cpp
#include <iostream>

using namespace std;

int main()
{
  cout << "It's me, your first program.";
  return 0;
}
``` 
El simbolo `#` indica que esta linea es una **directiva de preprocesamiento**. En este programa estamos tratando con la directiva **include**. Cuando el preprocesador encuentra esta directiva la reemplaza con el contenido del archivo cuyo nombre indica la misma (`iostream` en nuestro caso).

En el lenguaje C++, todos los elementos estándar de la infraestructura C++ son declarados dentro del nombre de espacio (**namespace**) llamado `std`. Un namespace es un contenedor o entorno abstracto creado para mantener un agrupamiento lógico de entidades únicas (bloques).

Una entidad definida en un namespace es asociada solo con este namespace. Si deseamos usar muchas de las entidades estandar de C++ debemos insertar la instrucción `using namespace` en la parte superior del archivo, fuera de cualquier función.

La instrucción debe especificar el nombre del namespace deseado (`std` en este caso). De este modo, las instalaciones estándar estarán disponibles durante todo el programa.

Se puedes omitir el uso del espacio de nombres en tu código, pero el coste de tal omisión no es cero. Ahora tienes que informar al compilador de dónde viene el bloque `cout` y debes hacerlo cada vez que utilices cualquiera de las entidades derivadas del espacio de nombres `std`. En otras palabras, tienes que escribir:
```cpp
std::cout
```

En lugar de: 
```cpp
cout
```

Dentro de la función `main` de nuestro programa tenemos una sentencia particular que dice: instruye a la entidad llamada `cout` de mostrar el siguiente texto en pantalla (indicado por el dígrafo `<<`, que especifica la dirección en que el texto es enviado). Sabemos que `cout` puede hacer esto por nosotros porque es lo que nos dice el estandar del lenguaje C++.

La entidad `cout` (es un objeto) debe ser alimentada con algo que se pretenda mostrar por pantalla. En nuestro ejemplo, la alimentación es solo texto (string).

La forma anterior del código fuente es la más natural y quizás la más fácil de leer por los humanos, pero aún así eres libre de escribirlo de otra manera. Por ejemplo:
```cpp
cout
<<
"It's me, your first program."
;
```

Ya casi hemos llegado al final. Sólo queda una línea en nuestro programa. Esta es:

```cpp
return 0;
```

# Conexion con el mundo real: inputs
Podemos conectar más de un operador `<<` en una sentencia `cout` y cada uno de los elementos imprimidos podría ser de un tipo y naturaleza diferente.

El siguiente ejemplo utiliza un **string literal** y una **variable integer** en una operación `cout`.

En este ejemplo:
```cpp
int herd_size = 123;
cout << "Sheep counted so far: " << herd_size;
```

Este fragmento de código da como resultado la cadena `Sheep counted so far: 123` impresa en la pantalla.

Una expresión también es un elemento `cout` legal. El siguiente ejemplo muestra uno de estos casos:
```cpp
int square_side = 12;
cout << "The square perimeter is: " << 4 * square_side;
```
## Manipulators
Si deseamos que un valor de tipo `int` sea representado como un número de punto flotante hexadecimal, necesitamos utilizar el denominado **manipulator**. Un manipulator es un tipo especial de entidad que le dice al stream que el formato de los datos debe ser modificado inmediatamente. Todos los elementos dados como salida luego de la activación del manipulator serán presentados en la forma deseada.

Un manipulator que es diseñado para cambiar el stream a un modo hexadecimal es llamado `hex`. El siguiente fragmento de código dará como salida un string que consiste en dos caracteres "F":
```cpp
int byte = 255;
cout << "Byte in hex: " << hex << byte;
```

Hay dos hechos imporantes que debemos entender aquí:

1. Cualquier manipulator comienza su trabajo desde el punto en que ha sido colocado y continua hasta el final de la sentencia `cout`. Este finaliza el trabajo solo cuando otro manipulator cancela su acción.
2. En el mismo manipulator podrían haber conflictos con otros nombres declarados por el programador; por ejemplo si tenemos nuestra propia variable llamada `hex` que podría ocultar el nombre del manipulador; estos conflictos son resueltos por un mecanismo especializado llamado *namespace*.

El siguiente ejemplo muestra como los manipulator comienzan y terminan su trabajo:
```cpp
int byte = 255;
cout << hex << byte;
cout << byte << dec << byte;
``` 
> Nota: el manipulador `dec` cambia el stream a un formato decimal. Es el manipulador por defecto.

El framgento de código anterior dará como salida 3 formas del mismo vaor:
1. `FF` como una representación hexadecimal de 255.
2. `FF` de nuevo (el manipulador anterior sigue actuando).
3. `255` como resultado de la activación del manipulador `dec`.

El manipulador `oct` cambia el stream de salida a modo **octal**.

Los tres manipulators vistos anteriormente son solo una implementación del manipulator `setbase`. Este solo acepta como parámetros los valores 8, 10 y 16:
* 8 -> oct
* 10 -> dec
* 16 -> hex

> Nota: este manipulator necesita de la inclusion de la librería `iomanip`.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main() {
	int byte = 255;
	cout << setbase(16) << byte;
}
```

En general, los streams de salida son capaces de reconocer el tipo del valor imprimido y actuar de acuerdo a ello. Si  bien `cout` es capaz de reconocer valores de diferentes tips, toma a los valores booleans como integers.

`cout` es capaz de reconocer el tipo real de su elemento incluso cuando es un efecto de una conversión. Una frase escrita como:
```cpp
static_cast<newtype>(expr)
```
Cambia el tipo de la expressiñon `expr` al tipo `newtype`.

# Conexion con el mundo real: outputs
La forma más sencilla es invertir mentalmente el sentido de la transferencia y reconocerlo para la entrada de datos:
* Utilizamos el flujo `cin` en lugar de `cout`
* Utilizamos el operador `>>` en lugar de `<<`

El operador `>>` suele denominarse operador de extracción.

El stream `cin`, junto con el operador de extraccióon es responsable de:
* Transferir los datos de forma legiblae para humanos desde el dispositivo de entrada, por ejemplo, la consola.
* Convertir los datos a representación interna (maquina) del valor de entrada.

Un codigo de ejemplo que recibe e imprime valores es:
```cpp
#include <iostream>

using namespace std;

int main() {
	string nombre;
	int edad;
	cout << "Ingrese nombre: ";
	cin >> nombre;
	cout << "Ingrese edad: ";
	cin >> edad;
	cout << "Nombre: " << nombre << "\nEdad: " << edad;
	return 0;
}
```

