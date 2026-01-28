# FastApi

## Pasos
1. Crear entorno virtual
    - terminal: `python -m venv .venv`
    - python: usa el programa llamado python
    - -m: llama a un módulo como un script, indicaremos cuál   módulo a continuación
    - venv: usa el módulo llamado venv que normalmente viene instalado con Python
    - .venv: crea el entorno virtual en el nuevo directorio .venv
    - Podrías crear el entorno virtual en un directorio diferente, pero hay una convención de llamarlo .venv.
2. Activar entorno virtual
    - terminal: `.\.venv\Scripts\Activate.ps1`
    - Considera que la primera parte el `.venv` se cambia por el directorio donde se encuentra el entorno virtual
    - Si aparece un error de ejecución debido a que no se puede ejecutar scripts, ejecuta: `Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser` y cierra y vuelve abrir Kiro eintentalo de nuevo
        - solo se hace una vez por proyecto, depues ya solo se ejecuta la activacion
    - Nota: para desactiar escribe `deactivate`
3. Instalar fastapi y uvicorn
    - terminal: `pip install "fastapi[standard]" "uvicorn[standard]"`
    - Se instala fastapi con sus dependencias standard (las que se necesitan para usarlo)
    - Se instala uvicorn con sus dependencias standard (el servidor que usará fastapi)
    - Nota: si se quiere instalar en produccion se puede usar solo `fastapi` y `uvicorn` sin las dependencias standard
4. Crear API para un HelloWorld en el directorio principal(fuera de .venv, recuerda es con `deactivate` que sales del entorno creado)
    - crear archivo `main.py` con:

            # Hola mundo en API
            from fastapi import FastApi

            app = FastAPI()

            @app.get("/")
            def read_root():
                return {"Message": "Hello World"}
        - from fastapi import FastApi: importa el modulo FastApi de fastapi
        - app = FastAPI(): crea una isntancia de la aplicacion FastAPI
        - @app.get("/"): Crea un endpoint GET en la ruta "/"
        - def read_root():: define una funcion llamada read_root
        - return {"Message": "Hello World"}: devuelve un diccionario con un mensaje
5. Ejecutar aplicación
    - terminal: `uvicorn main:app --reload`
    - uvicorn: llama al programa uvicorn
    - main:app indica a uvicorn que importe el objeto `app` del archivo `main.py`
    - --reload: le dice a uvicorn que recargue el servidor cada vez que haya un cambio en el código
    - tambien se puede agregar al final algo como un `--port 0000` para cambiar el puerto
    - Nota: si se quiere ejecutar en produccion se puede usar `uvicorn main:app --host 0.0.0.0 --port 8000` 


## Comandos git hub

### Comando git push

El comando git push se utiliza para subir los cambios realizados en un repositorio local hacia un repositorio remoto. Este comando transfiere los commits de la rama local al servidor remoto, asegurando que el trabajo esté sincronizado.

Ejemplo básico

`git push -u origin main`

#### Consideraciones importantes

1. Antes de usar git push, asegúrate de haber realizado un commit de todos los cambios locales con git commit.

2. Si el remoto tiene cambios no sincronizados, es recomendable hacer un git pull antes de realizar el push.

3. Usa --force solo si estás seguro de que no sobrescribirás trabajo importante en el remoto.

4. Este comando es esencial para colaborar en proyectos compartidos y mantener el código actualizado en el servidor remoto.

### Comando git pull en Git

El comando git pull se utiliza para actualizar un repositorio local con los cambios realizados en un repositorio remoto. Es una combinación de dos comandos: git fetch y git merge, lo que significa que primero descarga los cambios del remoto y luego los fusiona automáticamente en la rama local.

Sintaxis básica

`git pull origin main`

#### consideraciones importantes
1. En este caso, origin es el nombre del repositorio remoto y main es la rama que se desea actualizar.
2. El comando git pull es esencial para sincronizar tu trabajo local con el remoto, especialmente en flujos de trabajo colaborativos.

## Iniciar git en kiro

### clave ssh

1. generar una clave ssh con: `ssh-keygen -t ed25519 -C "tu_correo@example.com"`
2. y despues ejecutar para copiar tu llave: `clip ~/.ssh/id_ed25519.pub`
3. ir a ajustes en github y pegarla en las claves ssh

### pasos basicos en kiro

1. primero instalar git
2. luego en la temrinal de kiro verificar si git aparece como comando usable
3. si es usable inicializar un repositorio con ´git init´
4. agregar los cambios con `git add .`
5. hacer commit con `git commit -m "mensaje"`
6. conectar con el repositorio remoto con `git remote add origin XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX`
7. subir con: `git push -u origin main`- `origin` es el nombre del repositorio remoto
    - `main` es la rama a la que se quiere subir
    - si da error de rama puede ser `git push origin main`
    - si da error de permiso puede ser por el ssh, revisar clave ssh
    - `-u` es para establecer el upstream, es decir, recordar que `origin` es el remoto y `main` es la rama
    - tambien puede llegar a pedir contraseña si la llave ssh fue colocada con contraseña ejemplo `040904`
8. si quieres bajar algo del repositorio usar `pull origin main`
