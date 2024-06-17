## Adieu, Adieu

<iframe width="560" height="315" src="https://www.youtube.com/embed/Qy9_lfjQopU" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

https://www.youtube.com/watch?v=Qy9_lfjQopU

En The Sound of Music, hay una canción cantada principalmente en inglés, So Long, Farewell, con estas letras, donde "adieu" significa "adiós" en francés:

```
Adieu, adieu, to yieu and yieu and yieu
```

Por supuesto, la línea no es gramaticalmente correcta, ya que típicamente se escribiría (con una coma de Oxford) como:

```
Adieu, adieu, to yieu, yieu, and yieu
```

Para ser justos, "yieu" ni siquiera es una palabra; ¡simplemente rima con "you"!

En un archivo llamado `adieu.py`, implementa un programa que solicite al usuario nombres, uno por línea, hasta que el usuario ingrese control-d. Asume que el usuario ingresará al menos un nombre. Luego despídete de esos nombres, separando dos nombres con "and", tres nombres con dos comas y "and", y
nombres con
comas y "and", como en el siguiente ejemplo:

```
Adieu, adieu, to Liesl
Adieu, adieu, to Liesl and Friedrich
Adieu, adieu, to Liesl, Friedrich, and Louisa
Adieu, adieu, to Liesl, Friedrich, Louisa, and Kurt
Adieu, adieu, to Liesl, Friedrich, Louisa, Kurt, and Brigitta
Adieu, adieu, to Liesl, Friedrich, Louisa, Kurt, Brigitta, and Marta
Adieu, adieu, to Liesl, Friedrich, Louisa, Kurt, Brigitta, Marta, and Gretl
```

### Pistas

Ten en cuenta que el módulo `inflect` viene con bastantes métodos, según [pypi.org/project/inflect](https://pypi.org/project/inflect). Puedes instalarlo con:

```bash
pip install inflect
```

### Antes de Comenzar

1. Inicia sesión en [cs50.dev](https://cs50.dev), haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:
   ```bash
   $
   ```
2. Luego ejecuta:
   ```bash
   mkdir adieu
   ```
   para crear una carpeta llamada `adieu` en tu espacio de código.
3. Luego ejecuta:
   ```bash
   cd adieu
   ```
   para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como `adieu/ $`. Ahora puedes ejecutar:
   ```bash
   code adieu.py
   ```
   para crear un archivo llamado `adieu.py` donde escribirás tu programa.

### Cómo Probar

Así es como puedes probar tu código manualmente:

1. Ejecuta tu programa con:
   ```bash
   python adieu.py
   ```
   Escribe `Liesl` y presiona Enter, seguido de control-d. Tu programa debería mostrar:
   ```bash
   Adieu, adieu, to Liesl
   ```
2. Ejecuta tu programa con:
   ```bash
   python adieu.py
   ```
   Escribe `Liesl` y presiona Enter, luego escribe `Friedrich` y presiona Enter, seguido de control-d. Tu programa debería mostrar:
   ```bash
   Adieu, adieu, to Liesl and Friedrich
   ```
3. Ejecuta tu programa con:
   ```bash
   python adieu.py
   ```
   Escribe `Liesl` y presiona Enter, luego escribe `Friedrich` y presiona Enter. Ahora escribe `Louisa` y presiona Enter, seguido de control-d. Tu programa debería mostrar:
   ```bash
   Adieu, adieu, to Liesl, Friedrich, and Louisa
   ```

Puedes ejecutar lo siguiente para verificar tu código usando `check50`, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/adieu
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que `check50` te proporciona para ver la entrada que `check50` entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

### Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo:

```bash
submit50 cs50/problems/2022/python/adieu
```
