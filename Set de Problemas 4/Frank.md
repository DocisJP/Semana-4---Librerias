## Frank, Ian and Glen’s Letters

FIGlet, llamado así por las letras de Frank, Ian y Glen, es un programa de principios de la década de 1990 para hacer letras grandes con texto ordinario, una forma de arte ASCII:

```
 _ _ _          _   _     _
| (_) | _____  | |_| |__ (_)___
| | | |/ / _ \ | __| '_ \| / __|
| | |   <  __/ | |_| | | | \__ \
|_|_|_|\_\___|  \__|_| |_|_|___/
```

Entre las fuentes compatibles con FIGlet se encuentran las de [figlet.org/examples.html](http://figlet.org/examples.html).

FIGlet ha sido portado a Python como un módulo llamado `pyfiglet`.

En un archivo llamado `figlet.py`, implementa un programa que:

1. Espera cero o dos argumentos en la línea de comandos:
   - Cero si el usuario desea mostrar el texto en una fuente aleatoria.
   - Dos si el usuario desea mostrar el texto en una fuente específica, en cuyo caso el primero de los dos debe ser `-f` o `--font`, y el segundo debe ser el nombre de la fuente.
2. Solicita al usuario una cadena de texto.
3. Muestra ese texto en la fuente deseada.
4. Si el usuario proporciona dos argumentos en la línea de comandos y el primero no es `-f` o `--font` o el segundo no es el nombre de una fuente, el programa debe salir usando `sys.exit` con un mensaje de error.

### Pistas

Puedes instalar `pyfiglet` con:

```bash
pip install pyfiglet
```

La documentación de `pyfiglet` no es muy clara, pero puedes usar el módulo de la siguiente manera:

```python
from pyfiglet import Figlet

figlet = Figlet()
```

Puedes obtener una lista de fuentes disponibles con un código como este:

```python
figlet.getFonts()
```

Puedes configurar la fuente con un código como este, donde `f` es el nombre de la fuente como una cadena:

```python
figlet.setFont(font=f)
```

Y puedes mostrar el texto en esa fuente con un código como este, donde `s` es ese texto como una cadena:

```python
print(figlet.renderText(s))
```

Ten en cuenta que el módulo `random` viene con muchas funciones, según [docs.python.org/3/library/random.html](https://docs.python.org/3/library/random.html).

### Antes de Comenzar

1. Inicia sesión en [cs50.dev](https://cs50.dev), haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:
   ```bash
   $
   ```
2. Luego ejecuta:
   ```bash
   mkdir figlet
   ```
   para crear una carpeta llamada `figlet` en tu espacio de código.
3. Luego ejecuta:
   ```bash
   cd figlet
   ```
   para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como `figlet/ $`. Ahora puedes ejecutar:
   ```bash
   code figlet.py
   ```
   para crear un archivo llamado `figlet.py` donde escribirás tu programa.

### Cómo Probar

Así es como puedes probar tu código manualmente:

1. Ejecuta tu programa con:
   ```bash
   python figlet.py test
   ```
   Tu programa debería salir usando `sys.exit` e imprimir un mensaje de error:
   ```bash
   Invalid usage
   ```
2. Ejecuta tu programa con:
   ```bash
   python figlet.py -a slant
   ```
   Tu programa debería salir usando `sys.exit` e imprimir un mensaje de error:
   ```bash
   Invalid usage
   ```
3. Ejecuta tu programa con:
   ```bash
   python figlet.py -f invalid_font
   ```
   Tu programa debería salir usando `sys.exit` e imprimir un mensaje de error:
   ```bash
   Invalid usage
   ```
4. Ejecuta tu programa con:
   ```bash
   python figlet.py -f slant
   ```
   Escribe `CS50`. Tu programa debería imprimir lo siguiente:
   ```bash
      ___________ __________
     / ____/ ___// ____/ __ \
    / /    \__ \/___ \/ / / /
   / /___ ___/ /___/ / /_/ /
   \____//____/_____/\____/
   ```
5. Ejecuta tu programa con:
   ```bash
   python figlet.py -f rectangles
   ```
   Escribe `Hello, world`. Tu programa debería imprimir lo siguiente:
   ```bash
    _____     _ _                        _   _
   |  |  |___| | |___      _ _ _ ___ ___| |_| |
   |     | -_| | | . |_   | | | | . |  _| | . |
   |__|__|___|_|_|___| |  |_____|___|_| |_|___|
                     |_|
   ```
6. Ejecuta tu programa con:
   ```bash
   python figlet.py -f alphabet
   ```
   Escribe `Moo`. Tu programa debería imprimir lo siguiente:
   ```bash
   M   M
   MM MM
   M M M ooo ooo
   M   M o o o o
   M   M ooo ooo
   ```

Puedes ejecutar lo siguiente para verificar tu código usando `check50`, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/figlet
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que `check50` te proporciona para ver la entrada que `check50` entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

### Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo:

```bash
submit50 cs50/problems/2022/python/figlet
```
