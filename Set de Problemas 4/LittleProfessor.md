## Little Professor

<iframe width="560" height="315" src="https://www.youtube.com/watch?v=ZuJwzH9BIgs&t=1s" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

https://www.youtube.com/watch?v=ZuJwzH9BIgs&t=1s

Uno de los primeros juguetes de David, curiosamente, fue el Little Professor, una "calculadora" que generaba diez problemas matemáticos diferentes para que David los resolviera. Por ejemplo, si el juguete mostrara 4 + 0 = , David (con suerte) respondería con 4. Si el juguete mostrara 4 + 1 = , David (con suerte) respondería con 5. Si David respondiera incorrectamente, el juguete mostraría EEE. Y después de tres respuestas incorrectas para el mismo problema, el juguete simplemente mostraría la respuesta correcta (por ejemplo, 4 + 0 = 4 o 4 + 1 = 5).

En un archivo llamado `professor.py`, implementa un programa que:

- Solicite al usuario un nivel, \( n \). Si el usuario no ingresa 1, 2 o 3, el programa debe solicitarlo nuevamente.
- Genere aleatoriamente diez (10) problemas matemáticos formateados como \( X + Y = \), donde cada \( X \) y \( Y \) es un número entero no negativo con \( n \) dígitos. No es necesario soportar operaciones distintas a la suma (+).
- Solicite al usuario resolver cada uno de esos problemas. Si una respuesta no es correcta (o ni siquiera es un número), el programa debe mostrar EEE y solicitar al usuario nuevamente, permitiéndole al usuario hasta tres intentos en total para ese problema. Si el usuario aún no ha respondido correctamente después de tres intentos, el programa debe mostrar la respuesta correcta.
- El programa debe finalmente mostrar la puntuación del usuario: el número de respuestas correctas de 10.

Estructura tu programa de la siguiente manera, donde `get_level` solicita (y, si es necesario, vuelve a solicitar) al usuario un nivel y devuelve 1, 2 o 3, y `generate_integer` devuelve un número entero no negativo generado aleatoriamente con dígitos de nivel o lanza un `ValueError` si el nivel no es 1, 2 o 3:

```python
import random

def main():
    level = get_level()
    score = 0

    for _ in range(10):
        x = generate_integer(level)
        y = generate_integer(level)
        answer = x + y

        for attempt in range(3):
            try:
                guess = int(input(f"{x} + {y} = "))
                if guess == answer:
                    score += 1
                    break
                else:
                    print("EEE")
            except ValueError:
                print("EEE")
        else:
            print(f"{x} + {y} = {answer}")

    print(f"Score: {score}")

def get_level():
    while True:
        try:
            level = int(input("Level: "))
            if level in [1, 2, 3]:
                return level
        except ValueError:
            pass

def generate_integer(level):
    if level == 1:
        return random.randint(0, 9)
    elif level == 2:
        return random.randint(10, 99)
    elif level == 3:
        return random.randint(100, 999)
    else:
        raise ValueError("Invalid level")

if __name__ == "__main__":
    main()
```

### Pistas

- Ten en cuenta que puedes lanzar una excepción como `ValueError` con el siguiente código:
  ```python
  raise ValueError
  ```
- El módulo random tiene bastantes funciones, según [docs.python.org/3/library/random.html](https://docs.python.org/3/library/random.html).

### Antes de Comenzar

1. Inicia sesión en [cs50.dev](https://cs50.dev), haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:
   ```bash
   $
   ```
2. Luego ejecuta:
   ```bash
   mkdir professor
   ```
   para crear una carpeta llamada `professor` en tu espacio de código.
3. Luego ejecuta:
   ```bash
   cd professor
   ```
   para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como `professor/ $`. Ahora puedes ejecutar:
   ```bash
   code professor.py
   ```
   para crear un archivo llamado `professor.py` donde escribirás tu programa.

### Cómo Probar

Así es como puedes probar tu código manualmente:

1. Ejecuta tu programa con:
   ```bash
   python professor.py
   ```
   Escribe `-1` y presiona Enter. Tu programa debería volver a solicitarte:
   ```bash
   Level:
   ```
2. Ejecuta tu programa con:
   ```bash
   python professor.py
   ```
   Escribe `4` y presiona Enter. Tu programa debería volver a solicitarte:
   ```bash
   Level:
   ```
3. Ejecuta tu programa con:
   ```bash
   python professor.py
   ```
   Escribe `1` y presiona Enter. Tu programa debería comenzar a plantear problemas de suma con enteros positivos de un solo dígito. Por ejemplo:
   ```bash
   6 + 6 =
   ```
   Tu programa debería plantear 10 problemas distintos antes de imprimir el número de preguntas que respondiste correctamente y salir.
4. Ejecuta tu programa con:
   ```bash
   python professor.py
   ```
   Escribe `1` y presiona Enter. Responde incorrectamente a la primera pregunta. Tu programa debería mostrar:
   ```bash
   EEE
   ```
   antes de volver a solicitarte la misma pregunta.
5. Ejecuta tu programa con:
   ```bash
   python professor.py
   ```
   Escribe `1` y presiona Enter. Responde incorrectamente a la primera pregunta, tres veces. Tu programa debería mostrar la respuesta correcta. Por ejemplo:
   ```bash
   6 + 6 = 12
   ```
   y luego pasar a otra pregunta. Responde correctamente a las preguntas restantes. Tu programa debería mostrar una puntuación de 9.
6. Ejecuta tu programa con:
   ```bash
   python professor.py
   ```
   Escribe `1` y presiona Enter. Responde correctamente a las 10 preguntas. Tu programa debería mostrar una puntuación de 10.

Puedes ejecutar lo siguiente para verificar tu código usando `check50`, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/professor
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que `check50` te proporciona para ver la entrada que `check50` entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

### Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo:

```bash
submit50 cs50/problems/2022/python/professor
```
