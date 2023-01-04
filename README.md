# nauta-reconnect

Script para mantener la conexión nauta activa.
> - Una conexión Nauta Hogar se desconecta automáticamente luego de unos minutos de inactividad, de igual forma pasado 12h de haberse iniciado una conexión será desconectada aunque haya actividad.
> - Con una cuenta [nautaplus](https://www.etecsa.cu/es/preguntas-frecuentes?faq=4356) resulta incómodo no poder mantener la conexión sin interrupciones.

### Cómo usar el script:
0. Crear una carpeta `nauta` en el home del usuario autenticado, comunmente `~` o `$HOME`, y dentro de esta carpeta un archivo `credentials.txt`.
1. El archivo debe contener una structura json array simple con las credenciales de autenticación que se desea usar, por ejemplo:
```json
[
    {
        "user": "12345@nautaplus",
        "pass": "mypassword"
    },
        {
        "user": "6789@nautaplus",
        "pass": "myotherpassword"
    }
]
```
2. Configurar el script para que se ejecute cada cierto tiempo, por ejemplo usando `crontab -e`, puede crear una entrada en el crontab con la frecuencia deseada, por ejemplo: `*/3 * * * * /home/pi/scripts/nauta-reconnect` esto sería ejecutar el script cada 3 minutos.


### Notas:
- El script es bash *(para Linux y MacOS)*, pero debería poderse usar sin problemas en Windows con [WSL](https://learn.microsoft.com/en-us/windows/wsl/) y el programador de tareas de windows en vez de crontab...
- La idea de usar un json array que puede contener múltiples credenciales de autenticación es para en caso de tener varias cuentas y querer usar una inmediatamente que se acabe la otra.
- El archivo `credentials.txt` es texto plano y contendría las credenciales de autenticación, úselo solo en un host que confie.
- Cualquier mejora es bienvenida, haga PR y lo mejoramos.