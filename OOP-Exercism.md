# Práctica 12. Programación Orientada a Objetos. Tests Unitarios. Google Tests.

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

Propóngase a continuación resolver el problema "Hello World".
En la página de ese problema (o de cualquier otro) hallará Ud. un enlace que indica *Install Exercism locally* y 
[Begin walk-through](https://exercism.io/cli-walkthrough).
Si sigue ese enlace le llevará a la página *Welcome to the Exercism installation guide!* con instrucciones
sobre cómo instalar `Exercism`.
En este documento se propone instalarla en la máquina virtual Linux de la asignatura.
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

Una vez instalada la aplicación `exercism` el siguiente paso es configurar la interfaz de comandos (CLI) de la
aplicación.
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
acompañado de sus tests unitarios y un fichero `CMakeLists.txt` que se
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

### Trabajo previo
Antes de realizar los ejercicios de esta práctica, estudie detenidamente los capítulo 12 y 13(epígrafes 12.1-12.15, 13.1-13.13) del
[tutorial](https://www.learncpp.com/cpp-tutorial/81-welcome-to-object-oriented-programming/)
de referencia en la asignatura.
Muchos de los ejemplos de ese tutorial son los mismos que se utilizan en las clases de la asignatura,
cuyo material (transparencias y códigos de ejemplo) debiera Ud. también estudiar.
Las transparencias de la asignatura debieran servirle de guía a la hora de determinar qué partes del tutorial
ha de estudiar con mayor profundidad.

Ponga especial atención en estos ejercicios en seguir las normas de *Buenas prácticas* de programación a la
hora de diseñar programas orientados a objetos que se indican en las transparencias de la asignatura.

* Al realizar los ejercicios cree dentro de su repositorio de esta práctica un directorio diferente
con nombre significativo (vectors, compute, fecha, complejos p. ej.) para cada uno de ellos.
* Tómese como ejemplo el primero de los ejercicios y haga que cada uno de sus programas conste de 3 ficheros:
  * Un fichero `vector_main.cc` (programa principal) que contendrá la función `main` e incluirá el fichero de cabecera `vector.h`.
  * El fichero `vector.h` que contendrá las declaraciones correspondientes a la clase `Vector`.
  * El fichero `vector.cc` que contendrá el código (definiciones) correspondientes a la clase `Vector`.
  * Obviamente si el programa principal (`vectors.cc`) utiliza otras clases, debería incluir (`#include`) los
  correspondientes ficheros de cabecera.
  * Modifique estos nombres de ficheros para adaptarlos al ejercicio en cuestión.
* La compilación del programa correspondiente a cada ejercicio se automatizará con un fichero `CMakeLists.txt`
que se utilizará con `cmake`.
Así pues, la estructura de directorios y sus contenidos correspondiente al primero de los ejercicios
propuestos sería la siguiente:
```
 vector3D
 ├── CMakeLists.txt  // Fichero de configuración para cmake
 ├── src             // Directorio contenedor del código fuente del ejercicio
 │   ├── Makefile
 │   ├── vector.cc
 │   ├── vector.h
 │   └── vector_main.cc
 └── test            // Directorio contenedor del código de los tests del ejercicio
     ├── gtest_main.cc
     └── test_vector.cc
```
* Desarrolle cada ejercicio de forma incremental, probando cada una de las funciones que va Ud.
desarrollando. 
* Al realizar los ejercicios, ponga en práctica el ciclo de desarrollo TDD:
  * Escriba un test que falle y que define una mejora deseada o una nueva función
  * Escriba el código (función, método) que haga que la prueba pase satisfactoriamente 
  * Finalmente refactorice el nuevo código hasta obtener un resultado satisfactorio
* Utilice el depurador integrado de VSC para depurar los programas de modo que funcionen correctamente.
* Todos estos programas han de tomar su entrada (si es que hay alguna) como parámetros pasados por línea de comandos.
* Para cada una de las clases que se pide desarrollar, desarrolle también un programa cliente (el que
contendrá la función *main()*) que declare objetos de la clase en cuestión y compruebe el correcto
funcionamiento de los métodos de la clase.

### Ejercicios
1. Desarrolle una clase `Vector3D` para representar vectores en el espacio tridimensional.
La clase contemplará métodos al menos para:
  * Imprimir en pantalla las componentes de un vector en un formato adecuado 
  * Sumar un par de vectores
  * Calcular el producto de un número real por un vector
  * Calcular el producto escalar de dos vectores
  * Calcular el módulo de un vector 
  * Normalizar un vector

Para conseguir estas funcionalidades, sobrecargue los operadores que sea necesario.
Para este primer ejercicio se suministra en el directorio `vector3D` un esqueleto del código que ha de
desarrollar.
Complete el código (y los tests) necesario en los diferentes ficheros de ese proyecto.

Clase Estudiante
Clase Racional
Clase Encriptado de textos
Clase Timer https://stackoverflow.com/questions/22387586/measuring-execution-time-of-a-function-in-c
Clase Game


### Referencias
* [Exercism](https://exercism.io/)
* [Exercism en genbeta](https://www.genbeta.com/desarrollo/exercism-fitness-para-nuestras-habilidades-programadoras)
* [¿Qué es Ubuntu `snap`?](https://blogubuntu.com/que-es-ubuntu-snap) 
* [snap quickstart guide](https://snapcraft.io/docs/getting-started)
* [Desarrollo dirigido por Tests](https://es.wikipedia.org/wiki/Desarrollo_guiado_por_pruebas)
* [Google Test](https://en.wikipedia.org/wiki/Google_Test)
* [Cómo usar Google Test para C++ en VSC](https://docs.microsoft.com/es-es/visualstudio/test/how-to-use-google-test-for-cpp?view=vs-2019), 
* [Introduction to modern CMake for beginners](https://www.internalpointers.com/post/modern-cmake-beginner-introduction)
* [Welcome to object-oriented programming - Tutorial learnCPP](https://www.learncpp.com/cpp-tutorial/81-welcome-to-object-oriented-programming/).
* [Google C++ Style Guide](https://google.github.io/styleguide/cppguide.html)
