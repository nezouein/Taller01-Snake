# Taller 01 - Git y Resolución de Conflictos

## Objetivos

En este taller el equipo trabajará sobre un proyecto Java del juego Snake/Gold para practicar un flujo colaborativo con Git y GitHub.

Al finalizar, cada estudiante deberá poder:

- Configurar correctamente su identidad de Git antes de crear commits.
- Clonar un repositorio remoto y trabajar sobre una copia local.
- Crear commits pequeños y con mensajes claros.
- Subir cambios a GitHub.
- Identificar y resolver conflictos de integración cuando varias personas modifican las mismas líneas de código.
- Documentar el trabajo realizado mediante capturas y un README final.

## Importante: uso de computadoras compartidas

En los laboratorios de ESPOL se debe usar GitHub Desktop. Como las computadoras son compartidas, cada estudiante es responsable de manejar correctamente su sesión.

Antes de trabajar en una computadora del laboratorio:

1. Abra GitHub Desktop.
2. Inicie sesión con su propia cuenta de GitHub.
3. Verifique que GitHub Desktop tenga configurados su nombre y correo correctos para Git.
   - En Windows: `File > Options > Git`.
   - En macOS: `GitHub Desktop > Settings > Git`.
4. Use su nombre real y el correo asociado a su cuenta de GitHub.
5. Confirme que los commits aparecen con su usuario, no con el usuario de otra persona.

Al terminar en una computadora del laboratorio:

1. Haga `push` de los cambios que correspondan.
2. Cierre sesión en GitHub Desktop.
3. Cierre sesión en cualquier navegador donde haya ingresado a GitHub.
4. No deje credenciales guardadas en el equipo.

En computadoras personales se recomienda usar Git desde consola para tener mayor control del flujo de trabajo. Aun así, pueden usar GitHub Desktop si lo prefieren.

## Requisitos

- Cuenta personal en GitHub: <https://github.com/>
- GitHub Desktop para el trabajo en laboratorio: <https://desktop.github.com/>
- Git instalado:
  - Windows: <https://gitforwindows.org/>
  - macOS: `brew install git`
  - Linux: `sudo apt-get install git`
- JDK 14 o superior.
- IDE para Java. Se recomienda Eclipse o NetBeans.
- Maven, si se desea compilar desde consola.

## Proyecto base

Este repositorio contiene un proyecto Java con Maven.

Archivos principales:

- `pom.xml`: configuración Maven del proyecto. El código está configurado para Java 14.
- `src/main/java/com/espol/taller01/snake/GUIView.java`: contiene la interfaz gráfica y el botón `Start Game`.
- `src/main/java/com/espol/taller01/snake/SnakeModel.java`: contiene la lógica del juego Snake, la cabeza de la serpiente y la fruta.
- `src/main/java/com/espol/taller01/snake/GoldModel.java`: contiene la lógica del juego Gold y el colector.

El código base corresponde con las actividades del taller:

- En `GUIView.java` existe el botón `Start Game`, que será modificado por todos los integrantes.
- En `SnakeModel.java` existe `SNAKE_HEAD_TILE`, actualmente con `Color.GRAY`.
- En `SnakeModel.java` existe `FRUIT_TILE`, que usa `Color.RED` para la fruta.
- En `GoldModel.java` existe `COLLECTOR_TILE`, que usa `Color.BLACK` para el borde del colector.

Para verificar que el proyecto compila:

```bash
mvn -q -DskipTests package
```

Para ejecutar el proyecto, impórtelo en el IDE como proyecto Maven y ejecute la clase:

```text
com.espol.taller01.snake.Main
```

## Comandos útiles de Git

Estos comandos son especialmente útiles si trabaja desde su computadora personal:

```bash
git status
git clone <repositorio_remoto>
git add .
git commit -m "Mensaje claro del cambio"
git pull origin main
git push origin main
```

Para configurar la identidad solo dentro del repositorio actual:

```bash
git config --local user.name "Nombre Apellido"
git config --local user.email "correo@dominio.com"
git config --local --get user.name
git config --local --get user.email
```

En computadoras compartidas no configure credenciales globales si no está seguro de que podrá removerlas al final.

## Parte 1: configuración del repositorio

Esta parte la realiza primero el líder del grupo.

1. Crear en GitHub un repositorio público llamado `Taller01-Snake`.
2. Agregar a todos los integrantes como colaboradores:
   - Entrar al repositorio en GitHub.
   - Ir a `Settings > Collaborators`.
   - Seleccionar `Add people`.
   - Agregar el usuario de GitHub de cada integrante.
   - Cada integrante debe ingresar a su correo y aceptar la invitación.
3. Abrir GitHub Desktop e iniciar sesión con la cuenta del líder.
4. Clonar el repositorio:
   - `File > Clone repository...`
   - Seleccionar el repositorio `Taller01-Snake`.
   - Escoger una carpeta local.
   - Dar clic en `Clone`.
5. Descomprimir el archivo `Taller01-Snake.zip`.
6. Copiar el contenido del proyecto dentro de la carpeta del repositorio clonado.
7. En GitHub Desktop, revisar los archivos agregados.
8. Crear el primer commit con un mensaje como:

```text
Agregar código base del taller
```

9. Subir el commit con `Push origin`.
10. Verificar en GitHub que el código fue subido correctamente.

Después de esto, todos los integrantes deben clonar el repositorio desde GitHub Desktop. Antes de modificar código, todos deben confirmar que tienen exactamente la misma versión inicial.

## Parte 2: trabajo en paralelo

En esta parte todos trabajan localmente al mismo tiempo.

Reglas importantes:

- Cada integrante debe modificar solo lo que corresponde a su rol.
- Todos deben crear un commit local.
- Nadie debe hacer `push` todavía, excepto cuando se indique en la Parte 3.
- El mensaje del commit debe indicar el rol y resumir el cambio realizado.

### Líder

Modificar:

- En `GUIView.java`, cambiar el texto del botón de `Start Game` a `Jugar`.
- En `SnakeModel.java`, cambiar `Color.GRAY` por `Color.BLUE` en `SNAKE_HEAD_TILE`.
- En `SnakeModel.java`, cambiar `Color.RED` por `Color.GREEN` en `FRUIT_TILE`.
- En `GoldModel.java`, cambiar `Color.BLACK` por `Color.LIGHT_GRAY` en `COLLECTOR_TILE`.

Mensaje sugerido:

```text
Líder: personalizar botón y colores principales
```

### Integrante 1

Modificar:

- En `GUIView.java`, cambiar el texto del botón de `Start Game` a `Let's Go!!!`.
- En `SnakeModel.java`, cambiar `Color.GRAY` por `Color.LIGHT_GRAY` en `SNAKE_HEAD_TILE`.

Mensaje sugerido:

```text
Integrante 1: cambiar botón y cabeza de snake
```

### Integrante 2

Modificar:

- En `GUIView.java`, cambiar el texto del botón de `Start Game` a `Let's Play`.
- En `GoldModel.java`, cambiar `Color.BLACK` por `Color.BLUE` en `COLLECTOR_TILE`.

Mensaje sugerido:

```text
Integrante 2: cambiar botón y colector de gold
```

### Integrante 3 <small>_(si hubiere)_</small>

Si el grupo tiene un tercer integrante adicional, modificar:

- En `GUIView.java`, cambiar el texto del botón de `Start Game` a `Iniciar`.
- En `GoldModel.java`, cambiar `Color.BLACK` por `Color.RED` en `COLLECTOR_TILE`.

Mensaje sugerido:

```text
Integrante 3: cambiar botón y colector
```

### Integrante 4 <small>_(si hubiere)_</small>

Si el grupo tiene un cuarto integrante adicional, modificar:

- En `GUIView.java`, cambiar el texto del botón de `Start Game` a `Start`.
- En `SnakeModel.java`, cambiar `Color.GRAY` por `Color.GREEN` en `SNAKE_HEAD_TILE`.

Mensaje sugerido:

```text
Integrante 4: cambiar botón y cabeza de snake
```

## Parte 3: subir cambios y resolver conflictos

En esta parte los integrantes suben sus cambios uno por uno. No deben trabajar todos el `push` al mismo tiempo.

Orden de trabajo:

1. Líder.
2. Integrante 1.
3. Integrante 2.
4. Integrante 3, si existe.
5. Integrante 4, si existe.

### Paso del líder

1. El líder realiza `Push origin` desde GitHub Desktop.
2. No debería aparecer ningún conflicto, porque es la primera persona en subir los cambios.
3. Tomar una captura donde se evidencie que el `push` fue exitoso.
4. Avisar al siguiente integrante que puede continuar.

### Paso de cada integrante después del líder

Cada integrante debe hacer lo siguiente, en orden:

1. Intentar subir sus cambios con `Push origin`.
2. Debe aparecer un error porque el repositorio remoto ya tiene commits nuevos.
3. Tomar una captura del error.
4. Descargar los cambios remotos con `Fetch origin` y luego `Pull origin` en GitHub Desktop.
5. GitHub Desktop indicará los archivos con conflicto.
6. Abrir cada archivo con conflicto en el IDE o editor de texto.
7. Buscar los marcadores de conflicto:

```text
<<<<<<< HEAD
código local
=======
código remoto
>>>>>>> rama/remoto
```

8. Resolver el conflicto dejando la versión que corresponde al rol del integrante que está subiendo en ese momento.
9. Eliminar completamente las líneas `<<<<<<<`, `=======` y `>>>>>>>`.
10. Guardar los archivos.
11. Verificar que el proyecto compila.
12. Crear un nuevo commit de resolución de conflicto.
13. Subir los cambios con `Push origin`.
14. Tomar una captura donde se evidencie que el `push` fue exitoso.
15. Avisar al siguiente integrante.

Mensaje sugerido para el commit de resolución:

```text
Resolver conflictos del Integrante X
```

## Parte 4: README final y evidencias

Cuando todos hayan subido sus cambios, el líder debe:

1. Actualizar su repositorio local con `Pull origin`.
2. Completar la sección de integrantes y roles en este README.
3. Agregar las capturas tomadas por todos los integrantes.
4. Confirmar que las imágenes se visualizan correctamente en GitHub.
5. Crear un commit final.
6. Subir el commit con `Push origin`.

## Integrantes y roles

Complete esta tabla al final del taller.

| Rol | Nombre | Usuario de GitHub | Commit principal |
| --- | --- | --- | --- |
| Líder |  |  |  |
| Integrante 1 |  |  |  |
| Integrante 2 |  |  |  |
| Integrante 3 |  |  |  |
| Integrante 4 |  |  |  |

## Evidencias

Coloque las capturas dentro de una carpeta llamada `capturas/` y enláselas en esta sección.

Ejemplo:

```markdown
### Líder

Push exitoso:

![Push exitoso del líder](capturas/lider_push_exitoso.png)

### Integrante 1

Error antes de resolver conflicto:

![Error Integrante 1](capturas/integrante1_error.png)

Push exitoso después de resolver conflicto:

![Push exitoso Integrante 1](capturas/integrante1_push_exitoso.png)
```

## Recomendaciones para resolver conflictos

- Lean el código antes de borrar líneas.
- No dejen marcadores de conflicto en ningún archivo.
- No hagan `push` si el proyecto no compila.
- No resuelvan conflictos de varios integrantes al mismo tiempo.
- Si el conflicto está en el texto del botón, dejen el texto asignado al integrante que está haciendo el `push`.
- Si el conflicto está en colores, dejen el color asignado al integrante que está haciendo el `push`.
- Antes de entregar, revisen el historial de commits en GitHub para confirmar que todos participaron.

## Lista de verificación final

Antes de terminar el taller, confirmen:

- Todos los integrantes configuraron su nombre y correo correctamente.
- Todos los integrantes hicieron al menos un commit.
- Todos los conflictos fueron resueltos sin dejar marcadores en el código.
- El proyecto compila.
- El README contiene nombres, roles y capturas.
- El repositorio remoto está actualizado.
- En laboratorio, todos cerraron sesión en GitHub Desktop y en el navegador.
