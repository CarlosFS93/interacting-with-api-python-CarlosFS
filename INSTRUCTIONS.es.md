# Interactuando con la API de Spotify

Spotify se puede utilizar como fuente de datos para varios proyectos de ciencia de datos. En este ejercicio, aprenderemos a interactuar con la API de esta red social. `Spotipy` es una librería de código abierto y para Python que permite hacer un uso a alto nivel de la API de Spotify.

## Paso 1: Crear una cuenta de desarrollador de Spotify

El primer paso es crear una aplicación para poder acceder a los servicios API de Spotify. Toda la información la puedes encontrar [aquí](https://developer.spotify.com/documentation/web-api).

Una vez te hayas logueado usando tu cuenta de Spotify, podrás crear la aplicación para acceder a las credenciales necesarias para consumir la API. Deberás rellenar los siguientes campos:

![Spotify create app](https://github.com/4GeeksAcademy/interacting-with-api-python-project-tutorial/blob/main/assets/spotify_1.PNG?raw=true)

> NOTA: Como no vamos a utilizar esta API desde ninguna otra aplicación web, deja el campo de **Redirect URI** como `http://localhost/`.

Una vez completes el formulario, ya tendrás tu aplicación creada. A continuación, en el apartado de **settings** podrás encontrar tu `Client ID` y `Client Secret`.

## Paso 2: Configuración inicial

- Crear un archivo `app.py` dentro de la carpeta `./src/`.
- Asegúrate de tener instalada la librería de Python que vamos a utilizar, y si no, instálala: `pip install spotipy`.

## Paso 3: Variables de entorno

Debes proporcionar la clave y el token de Spotify para poder utilizar la API y acceder a sus funcionalidades. Como vimos en el proyecto anterior, esto puedes hacerlo fácilmente creando un fichero `.env` en el directorio raíz del proyecto.

El tercer paso es crear un archivo `.env` en tu proyecto y agrega tus claves secretas o contraseñas:

```py
CLIENT_ID="insert your client key"
CLIENT_SECRET="insert your client secret"
```

> NOTA: Asegúrate de agregar el `.env` dentro de tu archivo `.gitignore`, el cual no queremos guardar en el control de fuente, para que no estés poniendo en riesgo información potencialmente confidencial.

Ahora, debes instalar `python-dotenvpackage`. Este es un paquete de Python que permite que tu aplicación de Python lea un archivo `.env`. Este paquete buscará un `.env` y, si lo encuentra, expondrá las variables que contiene a la aplicación.

Ejemplo:

```py
from dotenv import load_dotenv
load_dotenv()

import os

client_id = os.environ.get("CLIENT_ID")
client_secret = os.environ.get("CLIENT_SECRET")

```

## Paso 4: Inicializar la biblioteca Spotipy

- Importar Spotipy.
- Realizar la conexión con la API. Para ello, puedes utilizar la función `spotipy.Spotify()`.

> NOTA: Utiliza la siguiente documentación como guía sobre los parámetros: https://spotipy.readthedocs.io/en/2.22.1

## Paso 5: Realizar solicitudes a la API

- Comienza a interactuar con la API de Spotify: Obtén de tu artista favorito, el top 10 de sus canciones. Para ello, tendrás que buscar el `ID` del artista para usarlo en la librería. Este identificador es la dirección web que tiene el artista en Spotify:

![Buscar el identificador del artista en Spotify](https://github.com/4GeeksAcademy/interacting-with-api-python-project-tutorial/blob/main/assets/spotify_2.png?raw=true)

- Una vez tengas la respuesta de la API, quédate con el elemento `tracks`, que contendrá las canciones con más reproducciones del artista, quédate con el nombre de la canción, la popularidad y la duración (en minutos).

## Paso 6: Transformar a Pandas DataFrame

Puesto que el resultado obtenido en estos pasos es susceptible de tener formato de tabla, conviértelo en un DataFrame importando los datos en su formato de diccionario. A continuación, ordena las canciones por popularidad creciente y muestra el top 3 resultante.

## Paso 7: Analizar relación estadística

¿Tiene relación la duración con la popularidad? ¿Podríamos decir que una canción que dure poco tiempo puede ser más popular que otra que dure más? Analízalo graficando un `scatter plot` y argumenta tu respuesta.
