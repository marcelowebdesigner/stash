# Uso de `git stash` en Git

Este repositorio tiene como objetivo explicar el uso de `git stash`.

Supongamos que estamos trabajando en un proyecto de software y utilizamos la rama `develop` como la rama principal del proyecto. Para crear nuevas contribuciones a nuestro proyecto, normalmente creamos ramas locales, subimos cambios, creamos solicitudes de extracción y esperamos a que un colaborador las integre en `develop`.

Sin embargo, a veces cometemos el error de trabajar directamente en `develop` sin crear una rama. ¿Qué hacer en este caso? Aquí es donde entra en juego `git stash`.

## Almacenar los cambios

Ejecutamos el siguiente comando para guardar temporalmente todos nuestros cambios.

```bash
git stash
```

Esto guarda nuestros cambios y nos permite continuar en una nueva rama, por ejemplo: creamos una rama que se llama nuevarama. Nos movemos a esta rama con el siguiente comando.

```bash
git checkout nuevarama
```

Para recuperar los cambios debemos traer de vuelta los cambios que hicimos en develop antes de continuar en nuevarama. Para hacerlo, utilizamos el siguiente comando.

```bash
git stash pop
```

Con este comando, recuperamos los cambios que guardamos previamente y los aplicamos a nuestra rama actual (nuevarama). Esto nos permite seguir trabajando en nuestra nueva rama con los cambios que realizamos en develop.

Si deseamos añadir una descripción al stash para hacerlo más descriptivo, podemos usar el siguiente comando.

```bash
git stash -m "Descripción de nuestro stash"
```

Esto facilita la identificación de los cambios almacenados cuando vemos la lista de stash.

Para visualizar la lista de stash para verificar qué cambios temporales tenemos almacenados, podemos utilizar el siguiente comando.

```bash
git stash list
```

Esto mostrará una lista similar a esta.

```bash
stash@{0}: WIP on feature-branch: 1234567 Some work in progress
stash@{1}: On another-branch: 9876543 Another stash for a different branch
```

Si deseamos aplicar un stash específico, ya sea por su nombre o su descripción, podemos usar estos comandos.

```bash
# Aplicar un stash específico por su nombre
git stash apply stash@{1}
```

```bash
# Aplicar un stash específico por su mensaje descriptivo
git stash apply "Some work in progress"
```

Recorda que git stash apply mantiene el stash en la lista, mientras que git stash pop lo aplica y lo elimina.

Eliminar un stash:
Si ya no necesitas un stash en la lista, puedes eliminarlo con el siguiente comando.

```bash
git stash drop stash@{1}
```

Esto ayuda a mantener la lista de stash organizada.

¡Espero que estas instrucciones te ayuden a comprender mejor cómo usar git stash en tu flujo de trabajo de desarrollo!