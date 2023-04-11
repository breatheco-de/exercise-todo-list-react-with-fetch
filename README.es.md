<!-- hide -->
# Segunda parte de la TODO List, agregando fetch
<!-- endhide -->

Debes hacer este ejercicio después de la [aplicación de la TODO List](https://4geeks.com/interactive-coding-tutorial/junior/todo-list) porque la primera parte es el boilerplate perfecto para comenzar a usar API's.

Para esta segunda parte, sincronizaremos nuestra lista de tareas con una base de datos real, usando la siguiente [RESTful](http://content.breatheco.de/lesson/understanding-rest-apis) y API pública realizada para este ejercicio.

🔗 Clic aquí para acceder a la [documentación de la API del TODO-list ](http://assets.breatheco.de/apis/fake/todos/).

👆[Aqui hay un video explicando como usar el TodoList API con Fetch.](https://www.youtube.com/watch?v=s6_-c0LFDRo)

Todo este ejercicio se trata de la programación de asíncrona porque las interacciones `from` y` to` del servidor deben realizarse de forma asíncrona. De esa manera, el usuario no tiene que esperar a que llegue la información.

## 🌱 Cómo comenzar este proyecto

No clones este repositorio porque vamos a usar una plantilla diferente.

Recomendamos abrir el `react boilerplate` usando una herramienta de aprovisionamiento como [Codespaces](https://4geeks.com/es/lesson/tutorial-de-github-codespaces) (recomendado) o [Gitpod](https://4geeks.com/es/lesson/como-utilizar-gitpod). Alternativamente, puedes clonarlo en tu computadora local usando el comando `git clone`.

Este es el repositorio que necesitas abrir o clonar:

```
https://github.com/4GeeksAcademy/react-hello
```

**👉 Por favor sigue estos pasos** [cómo comenzar un proyecto de codificación](https://4geeks.com/es/lesson/como-comenzar-un-proyecto-de-codificacion).

💡 Importante: Recuerda guardar y subir tu código a GitHub creando un nuevo repositorio, actualizando el remoto (`git remote set-url origin <your new url>`) y subiendo el código a tu nuevo repositorio usando los comandos `add`, `commit` y `push` desde la terminal de git.

## 📝 Instrucciones:

- Haz que tu TODO List se sincronice con la API de backend cada vez que se agregue o elimine una tarea.
- Agregue un botón de limpieza de todas las tareas que eliminará toda la lista del servidor y actualizará la lista vacía en el front-end.

Hay 3 momentos críticos en la línea de tiempo de la aplicación (denominado tiempo de ejecución) para centrarse en su integración:
- **Después de que la lista se carga vacía por primera vez (componentDidMount)**: debes obtener (GET) los datos de la API y actualizar las tareas cuando la información finalmente llegue.
- **Cuando se agrega una nueva tarea**: debes PONER (PUT) la nueva lista en el servidor.
- **Cuando se elimina una tarea**: Debes PONER (PUT) la nueva lista en el servidor.

## 💡 Pista

Utiliza la siguiente fetch call para sincronizar tus tareas con el servidor cada vez que haya un cambio en la lista.

```js
fetch('https://assets.breatheco.de/apis/fake/todos/user/alesanchezr', {
      method: "PUT",
      body: JSON.stringify(todos),
      headers: {
        "Content-Type": "application/json"
      }
    })
    .then(resp => {
        console.log(resp.ok); // Será true (verdad) si la respuesta es exitosa.
        console.log(resp.status); // el código de estado = 200 o código = 400 etc.
        console.log(resp.text()); // Intentará devolver el resultado exacto como cadena (string)
        return resp.json(); // (regresa una promesa) will try to parse the result as json as return a promise that you can .then for results
    })
    .then(data => {
        //Aquí es donde debe comenzar tu código después de que finalice la búsqueda
        console.log(data); //esto imprimirá en la consola el objeto exacto recibido del servidor
    })
    .catch(error => {
        //manejo de errores
        console.log(error);
    });
```

Para cualquier otra solicitud, debes seguir cambiando las variables en el fetch:El URL, el método y el payload (carga útil).

Este y otros proyectos son usados para [aprender a programar](https://4geeksacademy.com/es/aprender-a-programar/aprender-a-programar-desde-cero) por parte de los alumnos de 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) realizado por [Alejandro Sánchez](https://twitter.com/alesanchezr) y muchos otros contribuyentes. Conoce más sobre nuestros [Curso de Programación](https://4geeksacademy.com/es/curso-de-programacion-desde-cero?lang=es) para convertirte en [Full Stack Developer](https://4geeksacademy.com/es/coding-bootcamps/desarrollador-full-stack/?lang=es), o nuestro [Data Science Bootcamp](https://4geeksacademy.com/es/coding-bootcamps/curso-datascience-machine-learning).
