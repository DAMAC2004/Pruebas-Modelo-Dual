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

editado desde pc para subir a github
 
subido desde kiro
