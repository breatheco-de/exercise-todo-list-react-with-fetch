# ![alt text](https://assets.breatheco.de/apis/img/images.php?blob&random&cat=icon&tags=breathecode,32) Segunda parte de la TODO List, agregando fetch

Debes hacer este ejercicio después de la [aplicación de la TODO List](https://projects.breatheco.de/d/todo-list#readme) porque la primera parte es el boilerplate perfecto para comenzar a usar API's.

Para esta segunda parte, sincronizaremos nuestra lista de tareas con una base de datos real, usando la siguiente [RESTful](http://content.breatheco.de/lesson/understanding-rest-apis) y API pública realizada para este ejercicio.

🔗 Clic aquí para acceder a la [documentación de la API del TODO-list ](http://assets.breatheco.de/apis/fake/todos/).

👆[Aqui hay un video explicando como usar el TodoList API con Fetch.](https://www.youtube.com/watch?v=s6_-c0LFDRo)

Todo este ejercicio se trata de la programación de asincrona porque las interacciones `from` y` to` del servidor deben realizarse de forma asíncrona. De esa manera, el usuario no tiene que esperar a que llegue la información.

## 🌱  Cómo iniciar este proyecto

No clones este repositorio. El primer paso para comenzar a codificar es clonar el [react.js boilerplate](https://github.com/4GeeksAcademy/react-hello) en tu compjutador local o con Gitpod.

a) Si usas Gitpod (recomendada) puedes clonar el boilerplate [clic aquí](https://gitpod.io#https://github.com/4GeeksAcademy/react-hello).

b) Si trabajas localmente, escribe el siguiente comando en tu terminal: 
```sh
$ git clone https://github.com/4GeeksAcademy/react-hello
````

💡 Importante: Recuerda actualizar el `remote` del proyecto con el de tu repositorio usando `git remote set-url origin <your new url>`, y luego guardar tu código en tu nuevo repositorio usando `add`, `commit` y `push`.

## Instrucciones:

- Haz que tu TODO List se sincronice con la API de backend cada vez que se agregue o elimine una tarea.
- Agregue un botón de limpieza de todas las tareas que eliminará toda la lista del servidor y actualizará la lista vacía en el front-end.

Hay 3 momentos críticos en la línea de tiempo de la aplicación (denominado tiempo de ejecución) para centrarse en su integración:
- **Después de que la lista se carga vacía por primera vez (componentDidMount)**: debes obtener (GET) los datos de la API y actualizar las tareas cuando la información finalmente llegue.
- **Cuando se agrega una nueva tarea**: debes PONER (PUT) la nueva lista en el servidor.
- **Cuando se elimina una tarea**: Debes PONER (PUT) la nueva lista en el servidor.

## Pista

Utiliza la siguiente fetch call para sincronizar tus tareas con el servidor cada vez que haya un cambio en la lista.

```js
fetch('http://assets.breatheco.de/apis/fake/todos/user/alesanchezr', {
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
