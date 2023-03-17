# Second Part of the TODO list, adding fetch

This exercise is meant to be completed after the [TODO list react application](https://4geeks.com/interactive-coding-tutorial/junior/todo-list) because the first part it's the perfect boilerplate to start using API's.

For this second part, we will sync our todo list with a real database, using the following [RESTful](https://content.breatheco.de/lesson/understanding-rest-apis) and public API made for this exercise.

🔗 Click here to access to the [TODO-list API documentation](http://assets.breatheco.de/apis/fake/todos/).

This whole exercise is about asynchronous programming because the interactions `from` and `to` the server need to be done async. That way the user does not have to wait for the information to arrive.

## 🌱  How to start this project

Do not clone this repository.

The first step to start coding is cloning the [react boilerplate](https://github.com/4GeeksAcademy/react-hello) on your local computer or gitpod.

a) If using Gitpod you can clone the boilerplate by [clicking here](https://github.com/4GeeksAcademy/react-hello).

b) If working locally type the following command from your command line: `$ git clone https://github.com/4GeeksAcademy/react-hello`.

💡 Important: Remember to create a new repository, update the remote (`git remote set-url origin <your new url>`), and upload the code to your new repository using `add`, `commit` and `push`.


## 📝 Instructions:

- Make your to-do list sync with the backend API every time a task is added or deleted.
- Add a clean all tasks button that will delete the entire list from the server and update the empty list on the front-end.

There are 3 critical moments in the application timeline (a.k.a. The runtime) to focus on your integration:
- **After the list loads empty for the first time (componentDidMount)**: you should fetch (GET) the data from the API and update the tasks when the information finally arrives.
- **When a new task is added**: You should PUT the new list on the server.
- **When a task is deleted**: You should PUT the new list on the server.

## 💡 Hint

Use the following fetch call to synchronize your tasks with the server every time there is a change on the list.

```js
fetch('https://assets.breatheco.de/apis/fake/todos/user/alesanchezr', {
      method: "PUT",
      body: JSON.stringify(todos),
      headers: {
        "Content-Type": "application/json"
      }
    })
    .then(resp => {
        console.log(resp.ok); // will be true if the response is successfull
        console.log(resp.status); // the status code = 200 or code = 400 etc.
        console.log(resp.text()); // will try return the exact result as string
        return resp.json(); // (returns promise) will try to parse the result as json as return a promise that you can .then for results
    })
    .then(data => {
        //here is were your code should start after the fetch finishes
        console.log(data); //this will print on the console the exact object received from the server
    })
    .catch(error => {
        //error handling
        console.log(error);
    });
```

For any other request, you have to keep changing the same variables on the fetch: The URL, the method and the payload.
