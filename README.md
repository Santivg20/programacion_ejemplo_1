# Título 1

## Título 2

### Título 3

#### Título 4

### Código MATHDOWN

## Negrillas

`**Negritas**` **Negrillas**

`__Negritas__` __Negritas__

## Cursivas

`*Cursivas*` *Cursivas*

`_Cursivas_` _Cursivas_

## Subrayado

`<u>Subrayado</ins>` <u>Subrayado</u>

## Bullet

- Elemento 1
- Elemento 2

## Numeraciones

1. Elemento 1
2. Elemento 2

`1. Elemento 1`

`2. Elemento 2`

## Listas animadas

- Elemento 1
    - Elemento 1.1
    - Elemento 1.2

````markdown
- Elemento 1
    - Elemento 1.1
    - Elemento 1.2
````

## Tablas

| Columna 1 | Columna 2 | Columna 3 |
|-----------|-----------|-----------|
| Valor 1   | Valor 2   | Valor 3   |
| Valor 4   | Valor 5   | Valor 6   |

## Código `codigo`

```python
print("Hola Mundo")
```

```javascript
console.log("Hola Mundo")
```

## Ecuaciones
$$\dfrac{-b \pm \sqrt{b^2 -4ac}}{2a}$$

$y = mx + b$

## Imagenes

![Titulo si no sale la imagen](https://static.wikia.nocookie.net/frieren/images/3/3c/Frieren_anime.png/revision/latest/smart/width/250/height/250?cb=20231202010116&path-prefix=es)

### Se debe guardar la imagen en la carpeta donde se este trabajando 
![Titulo](1354394.jpeg)


## Hipervinculo

[Google](https://www.google.com/?hl=es)

# Guía Esencial de Comandos Git

Git es un **sistema de control de versiones distribuido**, gratuito y de código abierto, diseñado para manejar desde proyectos pequeños hasta muy grandes con velocidad y eficiencia. Te permite llevar un registro de los cambios en tus archivos, volver a versiones anteriores, trabajar en paralelo con diferentes características (_ramas_) y colaborar con otros desarrolladores.

Aquí están los comandos más comunes que necesitarás:

---

## 1. Configuración Inicial (Hacer solo una vez)

Antes de empezar, es buena idea configurar tu nombre de usuario y correo electrónico. Git usará esta información en cada _commit_ que hagas.

- **`git config --global user.name "Tu Nombre"`**
  - **Función:** Establece el nombre que se asociará a tus _commits_ globalmente (para todos tus repositorios en tu máquina).
- **`git config --global user.email "tu.email@ejemplo.com"`**
  - **Función:** Establece el correo electrónico que se asociará a tus _commits_ globalmente.
- **`git config --list`**
  - **Función:** Muestra la configuración actual de Git (puedes verificar si tu nombre y email se guardaron correctamente).

---

## 2. Crear o Clonar Repositorios

- **`git init`**
  - **Función:** Inicializa un nuevo repositorio de Git en el directorio actual. Crea una subcarpeta oculta `.git` que contiene toda la información necesaria para el control de versiones.
  - **Uso:** Navega a la carpeta de tu proyecto en la terminal y ejecuta este comando.
- **`git clone <URL_del_repositorio>`**
  - **Función:** Crea una copia local de un repositorio remoto existente (por ejemplo, uno alojado en GitHub, GitLab, Bitbucket). Descarga todo el historial del proyecto.
  - **Ejemplo:** `git clone https://github.com/usuario/mi-proyecto.git`

---

## 3. Flujo de Trabajo Básico (Guardar Cambios)

El flujo básico en Git implica modificar archivos, prepararlos para ser guardados (_staging_), y luego confirmar esos cambios (_commit_).

- **`git status`**
  - **Función:** Muestra el estado actual del directorio de trabajo y del área de _staging_ (preparación). Te indica qué archivos han sido modificados, cuáles están preparados para el próximo _commit_ y cuáles no están siendo rastreados por Git. Es uno de los comandos más usados.
- **`git add <archivo>`**
  - **Función:** Agrega los cambios de un archivo específico al área de _staging_. Los archivos en esta área son los que se incluirán en el próximo _commit_.
  - **Ejemplo:** `git add index.html`
- **`git add .`** (o `git add --all`)
  - **Función:** Agrega todos los archivos nuevos y modificados (dentro del directorio actual y subdirectorios) al área de _staging_.
- **`git commit -m "Mensaje descriptivo del commit"`**
  - **Función:** Guarda permanentemente los cambios que están en el área de _staging_ en el historial del repositorio. Cada _commit_ es una "fotografía" del estado del proyecto en un momento dado. El mensaje (`-m`) debe describir brevemente los cambios realizados.
  - **Buenas prácticas:** Escribe mensajes claros y concisos.

---

## 4. Ver Historial y Cambios

- **`git log`**
  - **Función:** Muestra el historial de _commits_ del repositorio, comenzando por el más reciente. Muestra el autor, fecha y mensaje de cada _commit_.
  - **Opciones útiles:**
    - `git log --oneline`: Muestra un resumen compacto del historial.
    - `git log --graph`: Muestra el historial como un gráfico de ramas.
    - `git log --stat`: Muestra las estadísticas de los archivos modificados en cada commit.
- **`git diff`**
  - **Función:** Muestra las diferencias entre los archivos modificados en tu directorio de trabajo y lo que hay en el área de _staging_.
- **`git diff --staged`** (o `git diff --cached`)
  - **Función:** Muestra las diferencias entre los archivos en el área de _staging_ y el último _commit_. Te permite revisar lo que estás a punto de confirmar.
- **`git diff <commit1> <commit2>`**
  - **Función:** Muestra las diferencias entre dos _commits_ específicos.

---

## 5. Ramas (Branches)

Las _ramas_ permiten trabajar en diferentes características o versiones del proyecto de forma aislada sin afectar la línea principal de desarrollo (normalmente llamada `main` o `master`).

- **`git branch`**
  - **Función:** Lista todas las ramas locales. La rama actual se marca con un asterisco (`*`).
- **`git branch <nombre-nueva-rama>`**
  - **Función:** Crea una nueva rama basada en el _commit_ actual, pero no te cambia a ella.
- **`git checkout <nombre-rama>`**
  - **Función:** Cambia tu directorio de trabajo a la rama especificada. (Este comando también se usa para restaurar archivos, ver más abajo).
  - **Alternativa moderna:** `git switch <nombre-rama>` (diseñado específicamente para cambiar de rama).
- **`git checkout -b <nombre-nueva-rama>`**
  - **Función:** Crea una nueva rama y cambia a ella inmediatamente. Es un atajo para `git branch <nombre-nueva-rama>` seguido de `git checkout <nombre-nueva-rama>`.
  - **Alternativa moderna:** `git switch -c <nombre-nueva-rama>`
- **`git merge <nombre-rama-a-fusionar>`**
  - **Función:** Fusiona los cambios de la `<nombre-rama-a-fusionar>` en la rama actual. Primero debes estar en la rama que recibirá los cambios (ej. `git checkout main`), luego ejecutas `git merge <rama-feature>`.
- **`git branch -d <nombre-rama>`**
  - **Función:** Elimina una rama local que ya ha sido fusionada. Usa `-D` (mayúscula) para forzar la eliminación si no ha sido fusionada (¡con cuidado!).

---

## 6. Trabajar con Repositorios Remotos

Los repositorios remotos son versiones de tu proyecto alojadas en servidores (como GitHub).

- **`git remote -v`**
  - **Función:** Lista los repositorios remotos configurados (normalmente llamados `origin`). Muestra las URL para _fetch_ (descargar) y _push_ (subir).
- **`git remote add <nombre-remoto> <URL_del_repositorio>`**
  - **Función:** Conecta tu repositorio local con un repositorio remoto. Por convención, el nombre más común es `origin`.
  - **Ejemplo:** `git remote add origin https://github.com/usuario/mi-proyecto.git`
- **`git fetch <nombre-remoto>`**
  - **Función:** Descarga los cambios (nuevos _commits_, ramas, etc.) desde el repositorio remoto, pero _no_ los integra automáticamente en tu directorio de trabajo local. Actualiza tus ramas de seguimiento remoto (ej. `origin/main`).
  - **Ejemplo:** `git fetch origin`
- **`git pull <nombre-remoto> <nombre-rama>`**
  - **Función:** Descarga los cambios desde el repositorio remoto y los fusiona (_merge_) automáticamente en tu rama local actual. Es equivalente a ejecutar `git fetch` seguido de `git merge <nombre-remoto>/<nombre-rama>`.
  - **Ejemplo:** `git pull origin main` (Actualiza tu rama `main` local con los cambios de la rama `main` remota).
- **`git push <nombre-remoto> <nombre-rama>`**
  - **Función:** Sube tus _commits_ locales (de la rama especificada) al repositorio remoto.
  - **Ejemplo:** `git push origin main` (Sube los cambios de tu rama `main` local a la rama `main` remota).
  - **Primera vez:** Si la rama no existe en el remoto, puede que necesites usar `git push -u origin <nombre-rama>` para establecer la conexión de seguimiento.

---

## 7. Deshacer Cambios

- **`git checkout -- <archivo>`**
  - **Función:** Descarta los cambios realizados en un archivo específico en tu directorio de trabajo, volviendo a la versión del último _commit_ (o del _staging area_ si el archivo estaba allí). **¡Cuidado, los cambios se pierden!**
- **`git reset HEAD <archivo>`**
  - **Función:** Saca un archivo del área de _staging_ (_unstage_), pero mantiene los cambios en tu directorio de trabajo. Útil si añadiste un archivo por error con `git add`.
- **`git reset <commit>`**
  - **Función:** Deshace _commits_. Tiene diferentes modos (`--soft`, `--mixed`, `--hard`).
    - `--soft`: Mueve el puntero `HEAD` al commit especificado, pero mantiene los cambios de los commits deshechos en el _staging area_.
    - `--mixed` (por defecto): Mueve `HEAD` y saca los cambios del _staging area_, pero los mantiene en el directorio de trabajo.
    - `--hard`: Mueve `HEAD` y descarta _todos_ los cambios (en _staging_ y en el directorio de trabajo) de los commits deshechos. **¡Este es peligroso, úsalo con extrema precaución!**
- **`git revert <commit>`**
  - **Función:** Crea un nuevo _commit_ que deshace los cambios introducidos por un _commit_ anterior específico. Es una forma segura de deshacer cambios en el historial público, ya que no reescribe la historia.

---

## 8. Otros Comandos Útiles

- **`git rm <archivo>`**
  - **Función:** Elimina un archivo tanto del directorio de trabajo como del área de _staging_. Es como hacer `rm <archivo>` y luego `git add <archivo>` para registrar la eliminación.
- **`git mv <archivo-viejo> <archivo-nuevo>`**
  - **Función:** Renombra o mueve un archivo. Es similar a `mv <archivo-viejo> <archivo-nuevo>` seguido de `git rm <archivo-viejo>` y `git add <archivo-nuevo>`.

---

Esta guía cubre los comandos más fundamentales de Git. A medida que uses Git más a menudo, descubrirás comandos más avanzados y opciones específicas. ¡La mejor manera de aprender es practicando! Puedes crear un repositorio de prueba y experimentar con estos comandos.