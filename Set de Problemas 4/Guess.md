## Juego de Adivinanzas

Estoy pensando en un número entre 1 y 100…

¿Qué número es?
¡Es 50! Pero, ¿y si fuera más aleatorio?

En un archivo llamado `game.py`, implementa un programa que:

- Solicite al usuario un nivel, \( n \). Si el usuario no ingresa un número entero positivo, el programa debe solicitarlo nuevamente.
- Genere aleatoriamente un número entero entre 1 y \( n \), inclusivo, utilizando el módulo random.
- Solicite al usuario que adivine ese número. Si la conjetura no es un número entero positivo, el programa debe solicitar nuevamente al usuario.
- Si la conjetura es menor que ese número, el programa debe mostrar "¡Demasiado pequeño!" y solicitar al usuario nuevamente.
- Si la conjetura es mayor que ese número, el programa debe mostrar "¡Demasiado grande!" y solicitar al usuario nuevamente.
- Si la conjetura es igual a ese número, el programa debe mostrar "¡Justo!" y salir.

### Pistas

Ten en cuenta que el módulo random tiene bastantes funciones, según [docs.python.org/3/library/random.html](https://docs.python.org/3/library/random.html).

### Antes de Comenzar

1. Inicia sesión en [cs50.dev](https://cs50.dev), haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:
   ```bash
   $
   ```
2. Luego ejecuta:
   ```bash
   mkdir game
   ```
   para crear una carpeta llamada `game` en tu espacio de código.
3. Luego ejecuta:
   ```bash
   cd game
   ```
   para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como `game/ $`. Ahora puedes ejecutar:
   ```bash
   code game.py
   ```
   para crear un archivo llamado `game.py` donde escribirás tu programa.

### Cómo Probar

Así es como puedes probar tu código manualmente:

1. Ejecuta tu programa con:
   ```bash
   python game.py
   ```
   Escribe `cat` en un prompt que dice Level: y presiona Enter. Tu programa debería volver a solicitarte:
   ```bash
   Level:
   ```
2. Ejecuta tu programa con:
   ```bash
   python game.py
   ```
   Escribe `-1` en un prompt que dice Level: y presiona Enter. Tu programa debería volver a solicitarte:
   ```bash
   Level:
   ```
3. Ejecuta tu programa con:
   ```bash
   python game.py
   ```
   Escribe `10` en un prompt que dice Level: y presiona Enter. Tu programa ahora debería estar listo para aceptar conjeturas:
   ```bash
   Guess:
   ```
4. Ejecuta tu programa con:
   ```bash
   python game.py
   ```
   Escribe `10` en un prompt que dice Level: y presiona Enter. Luego escribe `cat`. Tu programa debería volver a solicitarte:
   ```bash
   Guess:
   ```
5. Ejecuta tu programa con:
   ```bash
   python game.py
   ```
   Escribe `10` en un prompt que dice Level: y presiona Enter. Luego escribe `-1`. Tu programa debería volver a solicitarte:
   ```bash
   Guess:
   ```
6. Ejecuta tu programa con:

   ```bash
   python game.py
   ```

   Escribe `1` en un prompt que dice Level: y presiona Enter. Luego escribe `1`. Tu programa debería mostrar:

   ```bash
   Just right!
   ```

   Solo hay un número posible que podría ser la respuesta.

7. Ejecuta tu programa con:

   ```bash
   python game.py
   ```

   Escribe `10` en un prompt que dice Level: y presiona Enter. Luego escribe `100`. Tu programa debería mostrar:

   ```bash
   Too large!
   ```

   Parece que estás adivinando fuera del rango que especificaste.

8. Ejecuta tu programa con:
   ```bash
   python game.py
   ```
   Escribe `10000` en un prompt que dice Level: y presiona Enter. Luego escribe `1`. Tu programa debería mostrar:
   ```bash
   Too small!
   ```
   Lo más probable es que veas `Too small!`, aunque podrías tener suerte y ver `Just right!`. Pero ciertamente no deberías ver `Too large!`.

Puedes ejecutar lo siguiente para verificar tu código usando `check50`, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/game
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que `check50` te proporciona para ver la entrada que `check50` entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

### Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo:

```bash
submit50 cs50/problems/2022/python/game
```
