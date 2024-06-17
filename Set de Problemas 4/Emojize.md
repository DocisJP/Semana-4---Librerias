## Emojize

Debido a que los emojis no son tan fáciles de escribir como el texto, al menos en laptops y computadoras de escritorio, algunos programas admiten "códigos", mediante los cuales puedes escribir, por ejemplo, `:thumbs_up:`, que se convertirá automáticamente en 👍. Algunos programas también admiten alias, mediante los cuales puedes escribir más concisamente, por ejemplo, `:thumbsup:`, que también se convertirá automáticamente en 👍.

Consulta [esta lista de códigos con alias](https://carpedm20.github.io/emoji/all.html?enableList=enable_list_alias).

En un archivo llamado `emojize.py`, implementa un programa que solicite al usuario una cadena en inglés y luego muestre la versión "emojizada" de esa cadena, convirtiendo cualquier código (o alias) en sus correspondientes emojis.

### Pistas

Nota que el módulo `emoji` viene con dos funciones, según [pypi.org/project/emoji](https://pypi.org/project/emoji), una de las cuales es `emojize`, que toma un parámetro opcional llamado `language`. Puedes instalarlo con:

```bash
pip install emoji
```

### Antes de Comenzar

1. Inicia sesión en [cs50.dev](https://cs50.dev), haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:
   ```bash
   $
   ```
2. Luego ejecuta
   ```bash
   mkdir emojize
   ```
   para crear una carpeta llamada `emojize` en tu espacio de código.
3. Luego ejecuta
   ```bash
   cd emojize
   ```
   para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como `emojize/ $`. Ahora puedes ejecutar
   ```bash
   code emojize.py
   ```
   para crear un archivo llamado `emojize.py` donde escribirás tu programa.

### Cómo Probar

Así es como puedes probar tu código manualmente:

1. Ejecuta tu programa con
   ```bash
   python emojize.py
   ```
   Escribe `:1st_place_medal:` y presiona Enter. Tu programa debería mostrar:
   ```bash
   Output: 🥇
   ```
2. Ejecuta tu programa con
   ```bash
   python emojize.py
   ```
   Escribe `:money_bag:` y presiona Enter. Tu programa debería mostrar:
   ```bash
   Output: 💰
   ```
3. Ejecuta tu programa con
   ```bash
   python emojize.py
   ```
   Escribe `:smile_cat:` y presiona Enter. Tu programa debería mostrar:
   ```bash
   Output: 😸
   ```

Puedes ejecutar lo siguiente para verificar tu código usando `check50`, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/emojize
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que `check50` te proporciona para ver la entrada que `check50` entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

### Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo.

```bash
submit50 cs50/problems/2022/python/emojize
```
