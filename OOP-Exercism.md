# Práctica 12. Programación Orientada a Objetos. Exercism.

# Factor de ponderación: 10

### Objetivos
Los objetivos de esta práctica son que el alumnado:
* Desarrolle programas sencillos en C++ utilizando clases, así como todas las características del lenguaje estudiadas anteriormente
* Conozca la plataforma Exercism y sea capaz de interaccionar con la misma para resolver problemas 
* Conozca el framework de testing de Google (Google Tests) y sea capaz de desarrollar tests unitarios sencillos
* Conozca la herramienta CMake y sepa utilizarla para construir sus programas ejecutables

### Rúbrica de evaluacion de esta práctica
Todo el código que se presente a evaluación ha de cumplir los estándares definidos en la 
[Guía de Estilo de Google para C++](https://google.github.io/styleguide/cppguide.html).

Se señalan a continuación otros aspectos (la lista no es exhaustiva) que se tendrán en cuenta a la hora de evaluar esta práctica.
El alumnado ha de acreditar que:

* Conoce los conceptos expuestos en el material de referencia de esta práctica.
* Ha realizado todos los ejercicios propuestos, así como que es capaz de desarrollar otros de complejidad similar.
* Conoce la plataforma Exercism y es capaz de descargar y realizar problemas sencillos interaccionando con
  ella.
* Es capaz de escribir un fichero CMakeLists.txt para automatizar el proceso de compilación de sus programas.
* Todos sus programas se estructuran en directorios diferentes para cada "proyecto" haciendo que cada uno de
  ellos contenga un fichero `CMakeLists.txt` con la configuración de despliegue del proyecto.
* Se ha programado un conjunto mínimo de tests unitarios que comprueban el correcto funcionamiento de las
  funciones y métodos que se desarrollan para resolver los ejercicios.
* Todas las prácticas realizadas hasta la fecha se encuentran alojadas en repositorios de
[GitHub](https://github.com/).
* Los programas deben contener comentarios adecuados en el formato requerido por 
  [Doxygen](https://www.doxygen.nl/index.html).
* Sus programas se compilan correctamente utilizando la utilidad `make` y un fichero `Makefile`.
* Todos los identificadores que utilice en su programa (constantes, variables, etc.) deberán ser
  siempre significativos. No utilice nunca identificadores de una única letra, tal vez con la excepción de las variables que utilice para iterar en un bucle.
* Sabe editar y modificar sus programas usando VSC con una conexión remota a la máquina virtual Linux de la asignatura.
* Ha realizado todos sus ejercicios en la máquina virtual Ubuntu de la asignatura.
* Todos los programas que desarrolla, antes de su ejecución imprimen en pantalla un mensaje indicando la finalidad del programa así como la información que precisará del usuario para su correcta ejecución.
* Todos sus programas contienen comentarios adecuados en el formato requerido por Doxygen.
* Todos los ficheros de código del proyecto correspondiente a esta práctica están alojados en un repositorio
  de GitHub
* Conoce las técnicas básicas de depuración usando VSC y su depurador integrado.

### Exercism
[Exercism](https://exercism.io/) es una plataforma orientada a aprender a programar o también a mejorar las
capacidades de cualquier programadora.
El objetivo de Exercism es servir como medio para aprender a programar en un determinado lenguaje, y para ello se propone
hacerlo mediante la resolución de ejercicios que otros usuarios han planteado. 
Lo que se persigue es que tanto quien resuelve el problema como quien lo planteó aprendan al mismo tiempo. 
Además, la interacción con el resto de la comunidad podrá llevar a debates para determinar cuál sería la mejor solución para un determinado problema.

La plataforma se basa en una una aplicación ejecutable en línea de comandos disponible para diferentes sistemas
operativos (Linux, Mac, Windows).
Usando esa aplicación, un usuario puede descargar una serie de ejercicios de programación disponibles en la
plataforma y realizar los correspondientes programas hasta que consiga pasar los diferentes tests que se
suministran con cada ejercicio.

La plataforma puede ser usada en "modo práctica", en cuyo caso no existe la opción de mentorización (solicitar
que una experta le ayude con sus ejercicios), pero aún
así merece la pena practicar los múltiples ejercicios que hallará en la plataforma.

## Primeros pasos en Exercism
Comience por [registrarse en Exercism](https://exercism.io/users/sign_up). 
Si lo desea, puede Ud. hacerlo usando la cuenta de GitHub de la que ya dispone.
Una vez disponga de una cuenta, configure lo básico de la misma y elija un "track" (un lenguaje) en el que
desee practicar.
Obviamente se propone que elija el track correspondiente a C++.

Propóngase a continuación resolver el problema
["Hello World"](https://exercism.org/tracks/cpp/exercises/hello-world).
En la página de ese problema (o de cualquier otro) hallará Ud. un enlace que indica 
[Learn more about solving exercises
locally](https://exercism.org/docs/using/solving-exercises/working-locally).
Si sigue ese enlace le llevará a la página *Working Locally* que explica cómo trabajar con la plataforma en su
máquina local.
Desde esa página (*Installing the CLI*) se accede al enlace
[Welcome to the Exercism installation guide!](https://exercism.org/cli-walkthrough)
donde hallará instrucciones sobre cómo instalar `Exercism` en su máquina.
En este documento se propone instalarla en la máquina virtual de la asignatura.
Eligiendo la opción *Linux* y a continuación la opción *Using snap* se le pedirá que ejecute
```
$ sudo snap install exercism
```
Ese comando instalará en primer lugar `snap` y a continuación `exercism`, que es lo que se persigue.
También en esa página se indica que se compruebe que la instalación es correcta con el comando
```
$ exercism version
```
[`snap`](https://blogubuntu.com/que-es-ubuntu-snap) es un mecanismo alternativo al ya conocido
`apt-get install` para instalar aplicaciones en Ubuntu Linux.
Si quiere Ud. saber más sobre `snap` puede consultar
[esta referencia](https://snapcraft.io/docs/getting-started),
aunque ello no es necesario para el trabajo que se propone realizar con Exercism.

Una vez instalada la aplicación `exercism` el siguiente paso es configurar la interfaz de comandos 
(*Command Line Interface*, CLI) de la aplicación.
Para ello se pide que se ejecute el comando
```
$ exercism configure --token=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
```
donde el *token* que figura en el comando anterior se encuentra (es específico de cada usuario) en la [página
de configuración](https://exercism.io/my/settings) de la cuenta de usuario que se ha creado.
Basta copiar de esa página el token y colocarlo en el comando anterior.

El comando anterior, una vez ejecutado indica:
```
You have configured the Exercism command-line client:

Config dir:                       /home/usuario/snap/exercism/5/.config/exercism
Token:         (-t, --token)      xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx
Workspace:     (-w, --workspace)  /home/usuario/snap/exercism/5/exercism
API Base URL:  (-a, --api)        https://api.exercism.io/v1
```
A continuación se puede elegir un problema para pasar a resolverlo.
Se propone, como ya se ha dicho, elegir el problema "Hello World".
En la página de cada problema figura una descripción precisa del mismo y 
en la pestaña *Your iterations* hay un enlace
[Learn more about solving exercises locally](https://exercism.org/docs/using/solving-exercises/working-locally)
en el que figuran instrucciones para:
* Download. Descargar el problema mediante el comando `exercism download --exercise=hello-world --track=cpp`
* Solve. Para resolver el problema se propone usar el editor favorito del usuario. Se recomienda usar Visual
  Studio Code
* Submit. El comando (`exercism submit`) para subir a la plataforma la solución que el usuario proponga.

Si se ejecuta el comando para descargar el problema el sistema responde:
```
$ exercism download --exercise=hello-world --track=cpp

Downloaded to
/home/usuario/snap/exercism/5/exercism/cpp/hello-world
```
indicando el directorio donde ha colocado el código necesario para trabajar en ese problema.

Si revisa Ud. los ficheros descargados observará que Exercism utiliza `.cpp` como extensión para los ficheros
con código fuente C++ en lugar de la extensión `.cc` que recomienda la Guía de Estilo de Google.
La extensión `.cpp` es muy común para ficheros de código C++.

## Ejecución de los tests para un determinado problema
El siguiente paso consiste en editar el programa (en el caso del problema "Hello World" el fichero a editar es
`hello_world.cpp`).
Edite ese fichero hasta que considere que tiene una versión operativa.
Una vez finalizado su programa, el siguiente paso consiste en pasar (superar) los tests del código.
Cada ejercicio de Exercism va acompañado de una serie de tests que el programa debe superar para ser
considerado válido.

Tal como se explica en la página [Running the Tests](https://exercism.io/tracks/cpp/tests), cada problema va
acompañado de sus tests unitarios y de un fichero `CMakeLists.txt` que se
utiliza para automatizar la compilación de los tests y del propio programa.
Tenga en cuenta que **no** debiera editar ni modificar el fichero `CMakeLists.txt`.

Tal como se indica en la página anterior y suponiendo que su ejercicio se llame `bob`, 
debieran existir los ficheros `bob.cpp` y `bob.h` antes de
ejecutar los tests. 
Esos ficheros podrían estar vacíos, pero han de existir.
En el caso del ejercicio `hello-world` los ficheros son `hello-world.cpp` y `hello-world.h`

El siguiente paso es compilar el programa y los tests unitarios.
Para ello, colóquese en el directorio del ejercicio (`/home/usuario/snap/exercism/5/exercism/cpp/hello-world`)
y ejecute:
```
$ touch hello-world.{h,cpp}
$ mkdir build
$ cd build
$ cmake -G "Unix Makefiles" ..
$ make
```
El comando [touch](https://ss64.com/bash/touch.html) modifica la fecha del fichero (ficheros) que se le pasen
como argumentos. 
El directorio `build` que se crea servirá para alojar (entre otros ficheros) un programa ejecutable que pasará
los tests a su código.
Exercism utiliza `cmake` (tendrá Ud. que instalar esa aplicación en su VM si no la tiene instalada).

Al ejecutar `cmake -G "Unix Makefiles" ..` CMake creará un fichero Makefile que le servirá para compilar su
ejercicio.
Al ejecutar `make` en el directorio `build` se compilan los tests que ha de pasar su programa.
Si se producen errores de compilación, tendrá Ud. que solucionarlos en el directorio (padre de `build`) de su
ejercicio.
Una vez que se corrijan los errores, `make` construirá y ejecutará los tests que haya disponibles para el
ejercicio en cuestión.

Normalmente cada problema viene acompañado de un conjunto de tests cuyo código se encuentra en un fichero cuyo
nombre tiene el sufijo `_test` (fichero `hello_world_test.cpp` en el caso del ejercicio "Hello
World").
La estrategia que ha de seguir a la hora de progresar en la mejora de su ejercicio es hacer que su código pase
progresivamente las diferentes pruebas (tests) que figuran en ese fichero.
Para ello basta que "mueva" en el código la línea
```
#if defined(EXERCISM_RUN_ALL_TESTS)
```
para situarla después del siguiente test que quiera probar.
Tenga en cuenta que la plataforma de testing que utiliza Exercism es 
[Catch2](https://github.com/catchorg/Catch2)
y no Google Tests, pero los tests en formato Catch2 son fáciles de entender si se conoce
cualquier otra plataforma de testing.

Cuando su solución al problema pase todos los tests y esté Ud. satisfecha con la misma, puede remitirla a la
plataforma.
Utilice para ello el comando `exercism submit` que hallará Ud. en la página correspondiente al problema.
Una vez que haya enviado su solución a Exercism recibirá un mensaje similar a este:
```
Your solution has been submitted successfully.
You can complete the exercise and unlock the next core exercise at:

https://exercism.io/my/solutions/xxxx
```
A partir de este punto puede ya ver las soluciones que otras usuarias hayan dado al mismo problema o bien
avanzar con otros problemas de ese mismo "track".

### Ejercicios
1. Solucione todos los problemas que le sea posible en la plataforma Exercism.
Ello le ayudará a mejorar sus capacidades como programadora.
Para la evaluación de esta práctica se le pedirá que, aparte del problema "Hello World!" y de otros
relacionados en este documento, presente la solución
de un problema adicional de Exercism de los etiquetados como "fáciles" (*Easy*).

2. Utilice su clase `Complejo` de la práctica anterior para resolver el ejercicio
[Complex Numbers](https://exercism.org/tracks/cpp/exercises/complex-numbers)
de Exercism. 
En Exercism el nombre de la clase ha de ser *Complex* (estudie el fichero
`complex_numbers_test.cpp` que contiene los tests de ese problema).
Es posible que tenga que realizar alguna otra modificación sobre su implementación de la 
clase *Complejo* de la práctica anterior.

3. La clase Racional.

Un 
[número racional](https://en.wikipedia.org/wiki/Rational_number)
tiene un numerador y un denominador de la forma `p/q` donde `p` es el numerador y `q` el denominador.
Por ejemplo, 1/3, 3/4 y 10/4 son números racionales.

Un número racional no puede tener denominador 0, pero sí puede ser cero el numerador.
Todo número entero `n` es equivalente al racional `n/1`.
Los números racionales se utilizan en cálculos precisos que involucran fracciones.
Por ejemplo, `1/3 = 0.33333 ...`.
Este número no puede ser representado de forma precisa en formato de punto flotante utilizando los tipos float o double.
Para obtener resultados precisos es conveniente usar números racionales.

C++ dispone de tipos de datos para enteros y números en punto flotante, pero no para racionales.
En este ejercicio se propone el diseño de una clase para representar números racionales.

Desarrolle un programa cliente `racionales.cc` que permita operar con números racionales y haga uso
de la clase `Racional` que ha de diseñarse.

Las siguientes deben tomarse como especificaciones del programa a desarrollar:
* Separe el diseño de su clase `Racional` en dos ficheros, `racional.h` y `racional.cc` conteniendo
  respectivamente la declaración y la definición de la clase.
* La clase `Racional` incluirá al menos métodos para:
    * Crear objetos de tipo `Racional`. Se debe implementar un constructor por defecto y uno parametrizado.
    * Escribir (a fichero o a pantalla) un objeto de tipo `Racional`.
    * Leer (por teclado o desde fichero) un objeto de tipo `Racional`.
    * Sumar dos objetos de tipo `Racional`.
    * Restar dos objetos de tipo `Racional`.
    * Multiplicar dos objetos de tipo `Racional`.
    * Dividir dos objetos de tipo `Racional`.
    * Comparar objetos de tipo `Racional`.
* El programa ha de permitir leer un fichero de texto en el que figuran pares de números racionales
separados por espacios de la forma:

```
a/b c/d
e/f g/h
  ...
```

y para cada par de números racionales, el programa ha de imprimir en otro fichero de salida todas las operaciones posibles
con cada uno de los pares de números del fichero de entrada, de la forma:

```
a/b + c/d = n/m
  ...
```

Si el programa se ejecuta sin pasar parámetros en la línea de comandos, debemos obtener el siguiente mensaje:

```
./racionales -- Números Racionales
Modo de uso: ./racionales fichero_entrada fichero_salida
Pruebe ./racionales --help para más información
```

Si el programa se ejecuta pasando como parámetro la opción `--help` se ha de obtener:

```
./racionales -- Números Racionales
Modo de uso: ./racionales fichero_entrada fichero_salida 

fichero_entrada: Fichero de texto conteniendo líneas con un par de números racionales: `a/b c/d` separados por un espacio
fichero_salida:  Fichero de texto que contendrá líneas con las operaciones realizadas: `a/b + c/d = n/m`
```
Desarrolle tests (Google Tests) para comprobar el correcto funcionamiento de todos los métodos de la clase
`Racional`.

4. Descargue y estudie el problema 
[Robot Simulator](https://exercism.org/tracks/cpp/exercises/robot-simulator)
de Exercism y lea también el enunciado del problema siguiente (número 5) de esta relación.
Teniendo en mente ese problema (*Robot Simulator*), diseñe una solución orientada a objetos para el problema
[Movements on the ground](https://jutge.org/problems/P79784) de Jutge.
Aunque no se requieren en Jutge, desarrolle tests unitarios (Google Tests) para comprobar la corrección de su
diseño.
Suba el problema a Jutge para su evaluación.

5. La realización de este ejercicio es **Opcional** en esta práctica.

Realice un programa orientado a objetos que resuelva el ejercicio 
[Robot Simulator](https://exercism.org/tracks/cpp/exercises/robot-simulator)
de Exercism. 
Consiga que su solución pase todos los tests y envíe su solución a la plataforma.
Si estudia el fichero `robot_simulator_test.cpp` de tests del problema observará que la clase `Robot` a
diseñar ha de contener al menos los métodos:
* *get_bearing()*
* *get_position()*
* *turn_left()*
* *advance()*
* *execute_sequence()*

Deduzca también a partir de los tests los constructores que ha de tener la clase `Robot`.

Recuerde que la estrategia a seguir en la solución del problema consiste en ir "desbloqueando" progresivamente
los distintos tests que ha de pasar el programa.

### Referencias
* [Exercism](https://exercism.io/)
* [Exercism en genbeta](https://www.genbeta.com/desarrollo/exercism-fitness-para-nuestras-habilidades-programadoras)
* [¿Qué es Ubuntu `snap`?](https://blogubuntu.com/que-es-ubuntu-snap) 
* [snap quickstart guide](https://snapcraft.io/docs/getting-started)
* [Desarrollo dirigido por Tests](https://es.wikipedia.org/wiki/Desarrollo_guiado_por_pruebas)
* [Google Test](https://en.wikipedia.org/wiki/Google_Test)
* [Cómo usar Google Test para C++ en VSC](https://docs.microsoft.com/es-es/visualstudio/test/how-to-use-google-test-for-cpp?view=vs-2019), 
* [Welcome to object-oriented programming - Tutorial learnCPP](https://www.learncpp.com/cpp-tutorial/81-welcome-to-object-oriented-programming/).
* [Complex Number](https://en.wikipedia.org/wiki/Complex_number)
* [Rational Number](https://en.wikipedia.org/wiki/Rational_number)
* [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
