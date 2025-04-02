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

1. Make your TODO List sync with the backend API every time a task is added or deleted.
2. Add a "clear all tasks" button that will delete the entire list from the server and update the empty list on the front-end.

**👉 Key moments for integration:**

3. Load tasks on start (`useEffect`)
    - Use the `GET` method specified in the documentation **to fetch the list** and update the state that holds the task list.

4. Add a task.
    - Use the `POST` method specified in the documentation **to add a new task** and then use `GET` to update the task list.

5. Delete a task.
    - Use the `DELETE` method **to remove a task** and then `GET` to update the list.

6. Make sure to create a user before adding tasks.

## 💡 Hint:

Use the following fetch call to create a new task on the server. Remember to create a user first.

```js
fetch('https://playground.4geeks.com/todo/todos/alesanchezr', {
        method: "POST",
        body: JSON.stringify(task),
        headers: {
          "Content-Type": "application/json"
        }
     })
     .then(resp => {
          console.log(resp.ok); // Will be true if the response is successful
          console.log(resp.status); // Status code 201, 300, 400, etc.
          return resp.json(); // Will attempt to parse the result to JSON and return a promise where you can use .then to continue the logic
     })
     .then(data => {
          // This is where your code should start after the fetch is complete
          console.log(data); // This will print the exact object received from the server to the console
     })
     .catch(error => {
          // Error handling
          console.log(error);
     });
```

> ⚠️ For any other request, you must change the variables in the fetch: **The URL, the method, and the payload**.

This and many other projects are built by students as part of the 4Geeks Academy [Coding Bootcamp](https://4geeksacademy.com/us/coding-bootcamp) by [Alejandro Sanchez](https://twitter.com/alesanchezr) and many other contributors. Find out more about our [Full Stack Developer Course](https://4geeksacademy.com/us/coding-bootcamps/part-time-full-stack-developer), and [Data Science Bootcamp](https://4geeksacademy.com/us/coding-bootcamps/datascience-machine-learning).
