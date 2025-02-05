<!-- hide -->
# Second Part of the TODO list, adding fetch
<!-- endhide -->

This exercise is meant to be completed after the [TODO list React application](https://4geeks.com/interactive-coding-tutorial/todo-list) because the first part is the perfect boilerplate to start using API's.

For this second part, we will sync our to-do list with a real database, using the following [RESTful](https://4geeks.com/lesson/understanding-rest-apis) and public API made for this exercise.

🔗 Click here to access to the [TODO-list API documentation](https://playground.4geeks.com/todo/docs).

This whole exercise is about asynchronous programming because the interactions *from* and *to* the server need to be done async. That way, the user does not have to wait for the information to arrive.

<onlyfor saas="false" withBanner="false">
      
## 🌱 How to start this project

Do not clone this repository because we are going to be using a different template.

We recommend opening the `react boilerplate` using a provisioning tool like [Codespaces](https://4geeks.com/lesson/what-is-github-codespaces) (recommended) or [Gitpod](https://4geeks.com/lesson/how-to-use-gitpod). Alternatively, you can clone it on your local computer using the `git clone` command.

This is the repository you need to open or clone:

```text
https://github.com/4GeeksAcademy/react-hello
```

**👉 Please follow these steps on** [how to start a coding project](https://4geeks.com/lesson/how-to-start-a-project).

> 💡 Important: Remember to save and upload your code to GitHub by creating a new repository, updating the remote (`git remote set-url origin <your new url>`), and uploading the code to your new repository using the `add`, `commit` and `push` commands from the git terminal.

</onlyfor>

## 📝 Instructions:

- Make your to-do list sync with the backend API every time a task is added or deleted.
- Add a clean all tasks button that will `DELETE` the user from the server and empty the todo list on the front-end.

There are 3 critical moments in the application timeline (a.k.a. The runtime) to focus on while integrating this API:
- **After the list loads empty for the first time (`useEffect`)**: You should fetch (`GET`) the data from the API and update the tasks when the information finally arrives.
- **When a new task is added**: You should `PUT` the new list on the server.
- **When a task is removed**: You should `PUT` the new list on the server.

## 💡 Hint:

Use the following fetch call to create a new task on the server. Remember to first create a new user. 

```js
fetch('https://playground.4geeks.com/todo/todos/alesanchezr', {
      method: "POST",
      body: JSON.stringify(todo),
      headers: {
        "Content-Type": "application/json"
      }
    })
    .then(resp => {
        console.log(resp.ok); // Will be true if the response is successful
        console.log(resp.status); // The status code=201 or code=400 etc.
        console.log(resp.text()); // Will try to return the exact result as a string
        return resp.json(); // (returns promise) Will try to parse the result as JSON and return a promise that you can .then for results
    })
    .then(data => {
        // Here is where your code should start after the fetch finishes
        console.log(data); // This will print on the console the exact object received from the server
    })
    .catch(error => {
        // Error handling
        console.error(error);
    });
```

For any other request, you have to keep changing the same variables on the fetch: The URL, the method and the payload.

This and many other projects are built by students as part of the 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) by [Alejandro Sanchez](https://twitter.com/alesanchezr) and many other contributors. Find out more about our [Full Stack Developer Course](https://4geeksacademy.com/us/coding-bootcamps/part-time-full-stack-developer), and [Data Science Bootcamp](https://4geeksacademy.com/us/coding-bootcamps/datascience-machine-learning).
