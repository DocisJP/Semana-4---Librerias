## Lecture 4

### Libraries

- Random
- Statistics
- Command-Line Arguments
- slice
- Packages
- APIs
- Making Your Own Libraries
- Summing Up

### Libraries

En general, las bibliotecas son fragmentos de código escritos por ti o por otros que puedes usar en tu programa. Python te permite compartir funciones o características con otros como "módulos". Si copias y pegas código de un proyecto anterior, es probable que puedas crear un módulo o biblioteca que podrías traer a tu nuevo proyecto.

### Random

`random` es una biblioteca que viene con Python que puedes importar a tu propio proyecto. Es más fácil como programador apoyarse en el trabajo previo de otros programadores. Entonces, ¿cómo se carga un módulo en tu propio programa? Puedes usar la palabra `import` en tu programa. Dentro del módulo `random`, hay una función incorporada llamada `random.choice(seq)`. `random` es el módulo que estás importando. Dentro de ese módulo, está la función `choice`. Esa función toma una secuencia `seq` que es una lista.

En tu ventana de terminal, escribe `code generate.py`. En tu editor de texto, escribe el siguiente código:

```python
import random

coin = random.choice(["heads", "tails"])
print(coin)
```

Nota que la lista dentro de `choice` tiene corchetes, comillas y una coma. Dado que has pasado dos elementos, Python hace los cálculos y da un 50% de probabilidad para "heads" y "tails". Al ejecutar tu código, notarás que este código, de hecho, funciona bien.

Podemos mejorar nuestro código. `from` nos permite ser muy específicos sobre lo que nos gustaría importar. Anteriormente, nuestra línea de importación estaba trayendo todo el contenido de las funciones de `random`. Sin embargo, ¿y si solo queremos cargar una pequeña parte de un módulo? Modifica tu código como sigue:

```python
from random import choice

coin = choice(["heads", "tails"])
print(coin)
```

Nota que ahora podemos importar solo la función `choice` de `random`. A partir de ese momento, ya no necesitamos codificar `random.choice`. Ahora solo podemos codificar `choice` por sí sola. `choice` se carga explícitamente en nuestro programa. ¡Esto ahorra recursos del sistema y potencialmente puede hacer que nuestro código se ejecute más rápido!

Sigamos con la función `random.randint(a, b)`. Esta función generará un número aleatorio entre `a` y `b`. Modifica tu código como sigue:

```python
import random

number = random.randint(1, 10)
print(number)
```

Nota que nuestro código generará aleatoriamente un número entre 1 y 10.

Podemos introducir en nuestro código `random.shuffle(x)` donde barajará una lista en un orden aleatorio.

```python
import random

cards = ["jack", "queen", "king"]
random.shuffle(cards)
for card in cards:
    print(card)
```

Nota que `random.shuffle` barajará las cartas en su lugar. A diferencia de otras funciones, no devolverá un valor. En su lugar, tomará la lista `cards` y la barajará dentro de esa lista. Ejecuta tu código varias veces para ver cómo funciona.

Ahora tenemos estas tres formas de generar información aleatoria.

Puedes aprender más en la [documentación de random de Python](https://docs.python.org/3/library/random.html).

### Statistics

Python viene con una biblioteca de estadísticas incorporada. ¿Cómo podríamos usar este módulo?
`average` es una función de esta biblioteca que es bastante útil. En tu ventana de terminal, escribe `code average.py`. En la ventana del editor de texto, modifica tu código como sigue:

```python
import statistics

print(statistics.mean([100, 90]))
```

Nota que importamos una biblioteca diferente llamada `statistics`. La función `mean` toma una lista de valores. Esto imprimirá el promedio de estos valores. En tu ventana de terminal, escribe `python average.py`.

Considera las posibilidades de usar el módulo `statistics` en tus propios programas.
Puedes aprender más en la [documentación de statistics de Python](https://docs.python.org/3/library/statistics.html).

### Command-Line Arguments

Hasta ahora, hemos proporcionado todos los valores dentro del programa que hemos creado. ¿Qué pasa si queremos tomar la entrada desde la línea de comandos? Por ejemplo, en lugar de escribir `python average.py` en la terminal, ¿qué pasa si queremos escribir `python average.py 100 90` y obtener el promedio entre 100 y 90?
`sys` es un módulo que nos permite tomar argumentos en la línea de comandos.
`argv` es una función dentro del módulo `sys` que nos permite conocer lo que el usuario escribió en la línea de comandos. Nota cómo se utiliza `sys.argv` en el código a continuación. En la ventana de terminal, escribe `code name.py`. En el editor de texto, escribe el siguiente código:

```python
import sys

print("hello, my name is", sys.argv[1])
```

Nota que el programa va a mirar lo que el usuario escribió en la línea de comandos. Actualmente, si escribes `python name.py David` en la ventana de la terminal, verás `hello, my name is David`. Nota que `sys.argv[1]` es donde se almacena "David". ¿Por qué es eso? Bueno, en lecciones anteriores, podrías recordar que las listas comienzan en el elemento 0. ¿Qué crees que se almacena actualmente en `sys.argv[0]? Si adivinaste `name.py`, estarías en lo correcto.

Hay un pequeño problema con nuestro programa tal como está. ¿Qué pasa si el usuario no escribe el nombre en la línea de comandos? Pruébalo tú mismo. Escribe `python name.py` en la ventana de la terminal. Se presentará un error `list index out of range`. La razón de esto es que no hay nada en `sys.argv[1]` porque no se escribió nada. Aquí está cómo podemos proteger nuestro programa de este tipo de error:

```python
import sys

try:
    print("hello, my name is", sys.argv[1])
except IndexError:
    print("Too few arguments")
```

Nota que ahora se le dará al usuario una pista útil sobre cómo hacer que el programa funcione si se olvidan de escribir un nombre. Sin embargo, ¿podríamos ser más defensivos para asegurar que el usuario ingrese los valores correctos?

Nuestro programa puede mejorarse como sigue:

```python
import sys

if len(sys.argv) < 2:
    print("Too few arguments")
elif len(sys.argv) > 2:
    print("Too many arguments")
else:
    print("hello, my name is", sys.argv[1])
```

Nota que si pruebas tu código, verás cómo se manejan estas excepciones, proporcionando al usuario consejos más refinados. Incluso si el usuario escribe demasiados o muy pocos argumentos, se le proporciona al usuario instrucciones claras sobre cómo solucionar el problema.

En este momento, nuestro código es lógicamente correcto. Sin embargo, hay algo muy agradable en mantener nuestra comprobación de errores separada del resto de nuestro código. ¿Cómo podríamos separar nuestra gestión de errores? Modifica tu código como sigue:

```python
import sys

if len(sys.argv) < 2:
    sys.exit("Too few arguments")
elif len(sys.argv) > 2:
    sys.exit("Too many arguments")

print("hello, my name is", sys.argv[1])
```

Nota que estamos utilizando una función incorporada de `sys` llamada `exit` que nos permite salir del programa si se introduce un error por parte del usuario. Podemos estar seguros ahora de que el programa nunca ejecutará la última línea de código y no activará un error. Por lo tanto, `sys.argv` proporciona una forma por la cual los usuarios pueden introducir información desde la línea de comandos. `sys.exit` proporciona un medio por el cual el programa puede salir si surge un error.

Puedes aprender más en la [documentación de sys de Python](https://docs.python.org/3/library/sys.html).

### slice

`slice` es un comando que nos permite tomar una lista y decirle al compilador dónde queremos que considere el inicio y el final de la lista. Por ejemplo, modifica tu código como sigue:

```python
import sys

if len(sys.argv) < 2:
    sys.exit("Too few arguments")

for arg in sys.argv:
    print("hello, my name is", arg)
```

Nota que si escribes `python name.py David Carter Rongxin` en la ventana de la terminal, el compilador no solo producirá la salida de los nombres, sino también `hello, my name is name.py`. Entonces, ¿cómo podríamos asegurarnos de que el compilador ignore el primer elemento de la lista donde actualmente se almacena `name.py`?

`slice` se puede emplear en nuestro código para comenzar la lista en otro lugar. Modifica tu código como sigue:

```python
import sys

if len(sys.argv) < 2:
    sys.exit("Too few arguments")

for arg in sys.argv[1:]:
    print("hello, my name is", arg)
```

Nota que en lugar de comenzar la lista en 0, usamos corchetes para decirle al compilador que comience en 1 y vaya hasta el final usando el argumento `1:`. Al ejecutar este código, notarás que podemos mejorar nuestro código usando una sintaxis relativamente simple.

### Packages

Una de las razones por las que Python es tan popular es que hay numerosas bibliotecas de terceros poderosas que agregan funcionalidad. Llamamos a estas bibliotecas de terceros, implementadas como una carpeta

, "paquetes".
`PyPI` es un repositorio o directorio de todos los paquetes de terceros disponibles actualmente.
`cowsay` es un paquete bien conocido que permite que una vaca hable con el usuario.
Python tiene un administrador de paquetes llamado `pip` que te permite instalar paquetes rápidamente en tu sistema.
En la ventana de terminal, puedes instalar el paquete `cowsay` escribiendo `pip install cowsay`. Después de un poco de salida, ahora puedes usar este paquete en tu código.
En tu ventana de terminal, escribe `code say.py`. En el editor de texto, escribe el siguiente código:

```python
import cowsay
import sys

if len(sys.argv) == 2:
    cowsay.cow("hello, " + sys.argv[1])
```

Nota que el programa primero verifica que el usuario haya ingresado al menos dos argumentos en la línea de comandos. Luego, la vaca debería hablar con el usuario. Escribe `python say.py David` y verás una vaca diciendo "hello" a David.

Modifica aún más tu código:

```python
import cowsay
import sys

if len(sys.argv) == 2:
    cowsay.trex("hello, " + sys.argv[1])
```

Nota que ahora un t-rex está diciendo "hello".

Ahora puedes ver cómo podrías instalar paquetes de terceros.
Puedes aprender más en la [entrada de PyPI para cowsay](https://pypi.org/project/cowsay/).
Puedes encontrar otros paquetes de terceros en [PyPI](https://pypi.org/).

### APIs

Las APIs o "interfaces de programación de aplicaciones" te permiten conectarte con el código de otros.
`requests` es un paquete que permite que tu programa se comporte como lo haría un navegador web.
En tu terminal, escribe `pip install requests`. Luego, escribe `code itunes.py`.
Resulta que Apple iTunes tiene su propia API a la que puedes acceder en tus programas. En tu navegador de internet, puedes visitar [https://itunes.apple.com/search?entity=song&limit=1&term=weezer](https://itunes.apple.com/search?entity=song&limit=1&term=weezer) y se descargará un archivo de texto. David construyó esta URL leyendo la documentación de la API de Apple. Nota cómo esta consulta busca una canción, con un límite de un resultado, que se relaciona con el término llamado `weezer`. Al mirar este archivo de texto que se descarga, puedes encontrar que el formato es similar al que hemos programado previamente en Python.
El formato en el archivo de texto descargado se llama JSON, un formato basado en texto que se utiliza para intercambiar datos basados en texto entre aplicaciones. Literalmente, Apple está proporcionando un archivo JSON que podríamos interpretar en nuestro propio programa de Python.
En la ventana de la terminal, escribe `code itunes.py`. Codifica lo siguiente:

```python
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
print(response.json())
```

Nota que el valor devuelto de `requests.get` se almacenará en `response`. David, habiendo leído la documentación de Apple sobre esta API, sabe que lo que se devuelve es un archivo JSON. Al ejecutar `python itunes.py weezer`, verás el archivo JSON devuelto por Apple. Sin embargo, la respuesta JSON es convertida por Python en un diccionario. Al mirar la salida, ¡puede ser bastante mareante!

Resulta que Python tiene una biblioteca JSON incorporada que puede ayudarnos a interpretar los datos recibidos. Modifica tu código como sigue:

```python
import json
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=1&term=" + sys.argv[1])
print(json.dumps(response.json(), indent=2))
```

Nota que `json.dumps` se implementa de tal manera que utiliza `indent` para hacer que la salida sea más legible. Al ejecutar `python itunes.py weezer`, verás el mismo archivo JSON. Sin embargo, esta vez, es mucho más legible. Nota ahora que verás un diccionario llamado `results` dentro de la salida. Dentro de ese diccionario llamado `results` hay numerosas claves presentes. Observa el valor `trackName` en la salida. ¿Qué nombre de pista ves en tus resultados?

¿Cómo podríamos simplemente mostrar el nombre de esa pista? Modifica tu código como sigue:

```python
import json
import requests
import sys

if len(sys.argv) != 2:
    sys.exit()

response = requests.get("https://itunes.apple.com/search?entity=song&limit=50&term=" + sys.argv[1])

o = response.json()
for result in o["results"]:
    print(result["trackName"])
```

Nota que estamos tomando el resultado de `response.json()` y almacenándolo en `o` (como en la letra minúscula). Luego, estamos iterando a través de los resultados en `o` y mostrando cada `trackName`. También nota cómo hemos aumentado el número límite de resultados a 50. Ejecuta tu programa. Ve los resultados.

Puedes aprender más sobre `requests` a través de la [documentación de la biblioteca](https://docs.python-requests.org/en/master/).
Puedes aprender más sobre JSON en la [documentación de JSON de Python](https://docs.python.org/3/library/json.html).

### Making Your Own Libraries

Tienes la capacidad como programador de Python de crear tu propia biblioteca. Imagina situaciones en las que quieras reutilizar fragmentos de código una y otra vez o incluso compartirlos con otros.
Hemos estado escribiendo mucho código para decir "hello" hasta ahora en este curso. Vamos a crear un paquete para permitirnos decir "hello" y "goodbye". En tu ventana de terminal, escribe `code sayings.py`. En el editor de texto, codifica lo siguiente:

```python
def hello(name):
    print(f"hello, {name}")


def goodbye(name):
    print(f"goodbye, {name}")
```

Nota que este código en sí mismo no hace nada para el usuario. Sin embargo, si un programador importara este paquete en su propio programa, las habilidades creadas por las funciones anteriores podrían implementarse en su código.

Veamos cómo podríamos implementar el código utilizando este paquete que creamos. En la ventana de terminal, escribe `code say.py`. En este nuevo archivo en tu editor de texto, escribe lo siguiente:

```python
import sys

from sayings import goodbye

if len(sys.argv) == 2:
    goodbye(sys.argv[1])
```

Nota que este código importa las habilidades de `goodbye` del paquete `sayings`. Si el usuario ingresó al menos dos argumentos en la línea de comandos, dirá "goodbye" junto con la cadena ingresada en la línea de comandos.

### Summing Up

Las bibliotecas extienden las habilidades de Python. Algunas bibliotecas están incluidas por defecto con Python y simplemente necesitan ser importadas. Otras son paquetes de terceros que deben instalarse usando `pip`. ¡Puedes hacer tus propios paquetes para usarlos tú mismo o para otros! En esta lección, aprendiste sobre…

- Bibliotecas
- Random
- Estadísticas
- Argumentos de línea de comandos
- Slice
- Paquetes
- APIs
- Crear tus propias bibliotecas
