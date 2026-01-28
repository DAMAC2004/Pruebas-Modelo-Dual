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

## comando git hub

### Comando git push

El comando git push se utiliza para subir los cambios realizados en un repositorio local hacia un repositorio remoto. Este comando transfiere los commits de la rama local al servidor remoto, asegurando que el trabajo esté sincronizado.

Ejemplo básico

git push origin main

Este comando sube los cambios de la rama local main al repositorio remoto llamado origin.

Sintaxis general

git push <nombre-remoto> <nombre-rama>

<nombre-remoto>: Generalmente es origin, que apunta al repositorio remoto.

<nombre-rama>: Especifica la rama que deseas subir, como main o develop.

Opciones comunes

Subir todas las ramas:

git push --all origin
Copiar
Forzar un push:

git push --force origin main
Copiar
Eliminar una rama remota:

git push origin --delete <nombre-rama>
Copiar
Ignorar hooks pre-push:

git push --no-verify
Copiar
Consideraciones importantes

Antes de usar git push, asegúrate de haber realizado un commit de todos los cambios locales con git commit.

Si el remoto tiene cambios no sincronizados, es recomendable hacer un git pull antes de realizar el push.

Usa --force solo si estás seguro de que no sobrescribirás trabajo importante en el remoto.

Este comando es esencial para colaborar en proyectos compartidos y mantener el código actualizado en el servidor remoto.

### Comando git pull en Git
El comando git pull se utiliza para actualizar un repositorio local con los cambios realizados en un repositorio remoto. Es una combinación de dos comandos: git fetch y git merge, lo que significa que primero descarga los cambios del remoto y luego los fusiona automáticamente en la rama local.

Sintaxis básica

git pull [opciones] [repositorio] [refspec]
Copiar
Ejemplo de uso:

git pull origin main
Copiar
En este caso, origin es el nombre del repositorio remoto y main es la rama que se desea actualizar.

Funcionamiento

git fetch: Descarga las actualizaciones del repositorio remoto, pero no las aplica directamente.

git merge: Fusiona las actualizaciones descargadas en la rama local activa.

Por ejemplo, si estás trabajando en la rama main y ejecutas git pull, Git traerá los cambios remotos de main y los integrará en tu copia local.

Opciones comunes

--rebase: En lugar de fusionar los cambios, reescribe el historial local para que sea lineal.

git pull --rebase origin main
Copiar
--no-commit: Descarga los cambios pero no crea automáticamente una confirmación de fusión.

git pull --no-commit origin main
Copiar
--verbose: Muestra detalles adicionales sobre el proceso de descarga y fusión.

git pull --verbose
Copiar
Consideraciones importantes

Si tienes cambios locales no confirmados, git pull puede fallar durante la fusión. Es recomendable confirmar o guardar tus cambios antes de ejecutar este comando.

git pull puede generar conflictos si los cambios locales y remotos afectan las mismas líneas de código. En este caso, deberás resolver los conflictos manualmente.

Diferencia entre git pull y git fetch

git fetch: Solo descarga los cambios remotos sin aplicarlos al repositorio local.

git pull: Descarga y aplica los cambios automáticamente, lo que puede provocar conflictos si no se tiene cuidado.

Ejemplo con rebase

Si prefieres mantener un historial limpio y lineal, puedes usar la opción --rebase:

git pull --rebase origin main
Copiar
Esto asegura que tus cambios locales se reescriban sobre los cambios remotos, evitando confirmaciones de fusión innecesarias.

El comando git pull es esencial para sincronizar tu trabajo local con el remoto, especialmente en flujos de trabajo colaborativos.

git push -u origin main
040904

pull origin main
