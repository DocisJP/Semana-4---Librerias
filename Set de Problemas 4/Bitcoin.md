## Bitcoin Price Index

Bitcoin es una forma de moneda digital, también conocida como criptomoneda. En lugar de depender de una autoridad central como un banco, Bitcoin depende de una red distribuida, conocida como blockchain, para registrar transacciones.

Debido a que hay demanda de Bitcoin (es decir, los usuarios lo desean), los usuarios están dispuestos a comprarlo, intercambiando una moneda (por ejemplo, USD) por Bitcoin.

En un archivo llamado `bitcoin.py`, implementa un programa que:

- Espera que el usuario especifique como argumento de línea de comandos la cantidad de Bitcoins (\( n \)) que le gustaría comprar. Si ese argumento no se puede convertir a un `float`, el programa debe salir usando `sys.exit` con un mensaje de error.
- Consulta la API para el Índice de Precios de Bitcoin de CoinDesk en [https://api.coindesk.com/v1/bpi/currentprice.json](https://api.coindesk.com/v1/bpi/currentprice.json), que devuelve un objeto JSON, entre cuyas claves anidadas está el precio actual de Bitcoin como `float`. Asegúrate de capturar cualquier excepción, como con el siguiente código:

  ```python
  import requests

  try:
      ...
  except requests.RequestException:
      ...
  ```

- Muestra el costo actual de \( n \) Bitcoins en USD con cuatro decimales, usando `,` como separador de miles.

### Pistas

- Recuerda que el módulo `sys` viene con `argv`, según [docs.python.org/3/library/sys.html#sys.argv](https://docs.python.org/3/library/sys.html#sys.argv).
- El módulo `requests` tiene bastantes métodos, según [requests.readthedocs.io/en/latest](https://requests.readthedocs.io/en/latest), entre ellos `get`, según [requests.readthedocs.io/en/latest/user/quickstart.html#make-a-request](https://requests.readthedocs.io/en/latest/user/quickstart.html#make-a-request), y `json`, según [requests.readthedocs.io/en/latest/user/quickstart.html#json-response-content](https://requests.readthedocs.io/en/latest/user/quickstart.html#json-response-content). Puedes instalarlo con:
  ```bash
  pip install requests
  ```
- La API de CoinDesk devuelve una respuesta JSON como:
  ```json
  {
    "time": {
      "updated": "May 2, 2022 15:27:00 UTC",
      "updatedISO": "2022-05-02T15:27:00+00:00",
      "updateduk": "May 2, 2022 at 16:27 BST"
    },
    "disclaimer": "This data was produced from the CoinDesk Bitcoin Price Index (USD). Non-USD currency data converted using hourly conversion rate from openexchangerates.org",
    "chartName": "Bitcoin",
    "bpi": {
      "USD": {
        "code": "USD",
        "symbol": "&#36;",
        "rate": "38,761.0833",
        "description": "United States Dollar",
        "rate_float": 38761.0833
      },
      "GBP": {
        "code": "GBP",
        "symbol": "&pound;",
        "rate": "30,827.6198",
        "description": "British Pound Sterling",
        "rate_float": 30827.6198
      },
      "EUR": {
        "code": "EUR",
        "symbol": "&euro;",
        "rate": "36,800.2764",
        "description": "Euro",
        "rate_float": 36800.2764
      }
    }
  }
  ```
- Recuerda que puedes formatear USD a cuatro decimales con un separador de miles con el siguiente código:
  ```python
  print(f"${{amount:,.4f}}")
  ```

### Antes de Comenzar

1. Inicia sesión en [cs50.dev](https://cs50.dev), haz clic en tu ventana de terminal y ejecuta `cd` por sí solo. Deberías ver que el indicador de la ventana de tu terminal se asemeja a lo siguiente:
   ```bash
   $
   ```
2. Luego ejecuta:
   ```bash
   mkdir bitcoin
   ```
   para crear una carpeta llamada `bitcoin` en tu espacio de código.
3. Luego ejecuta:
   ```bash
   cd bitcoin
   ```
   para cambiar de directorio a esa carpeta. Ahora deberías ver el indicador de tu terminal como `bitcoin/ $`. Ahora puedes ejecutar:
   ```bash
   code bitcoin.py
   ```
   para crear un archivo llamado `bitcoin.py` donde escribirás tu programa.

### Cómo Probar

Así es como puedes probar tu código manualmente:

1. Ejecuta tu programa con:
   ```bash
   python bitcoin.py cat
   ```
   Tu programa debería salir usando `sys.exit` y mostrar un mensaje de error:
   ```bash
   Invalid number of bitcoins
   ```
2. Ejecuta tu programa con:
   ```bash
   python bitcoin.py 10
   ```
   Tu programa debería consultar la API de CoinDesk y mostrar el costo actual de 10 Bitcoins en USD con cuatro decimales, usando `,` como separador de miles. Por ejemplo:
   ```bash
   $387,610.8330
   ```

Puedes ejecutar lo siguiente para verificar tu código usando `check50`, un programa que CS50 usará para probar tu código cuando lo envíes. ¡Pero asegúrate de probarlo tú mismo también!

```bash
check50 cs50/problems/2022/python/bitcoin
```

Las caritas verdes significan que tu programa ha pasado una prueba. Las caritas rojas indicarán que tu programa mostró algo inesperado. Visita la URL que `check50` te proporciona para ver la entrada que `check50` entregó a tu programa, qué salida esperaba y qué salida dio tu programa realmente.

### Cómo Enviar

En tu terminal, ejecuta lo siguiente para enviar tu trabajo:

```bash
submit50 cs50/problems/2022/python/bitcoin
```
