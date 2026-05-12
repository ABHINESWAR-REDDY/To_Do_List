# Ex03 To-Do List using JavaScript
## Date:12/05/2026

## AIM
To create a To-do Application with all features using JavaScript.

## ALGORITHM
### STEP 1
Build the HTML structure (index.html).

### STEP 2
Style the App (style.css).

### STEP 3
Plan the features the To-Do App should have.

### STEP 4
Create a To-do application using Javascript.

### STEP 5
Add functionalities.

### STEP 6
Test the App.

### STEP 7
Open the HTML file in a browser to check layout and functionality.

### STEP 8
Fix styling issues and refine content placement.

### STEP 9
Deploy the website.

### STEP 10
Upload to GitHub Pages for free hosting.

## PROGRAM
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do App</title>

    <style>
        body {
            font-family: Arial, sans-serif;
            background: #111;
            color: white;
            display: flex;
            justify-content: center;
            align-items: center;
            height: 100vh;
            margin: 0;
        }

        .container {
            background: #1e1e1e;
            padding: 20px;
            border-radius: 10px;
            width: 350px;
            text-align: center;
        }

        .input-section {
            display: flex;
            gap: 10px;
        }

        input {
            flex: 1;
            padding: 10px;
            border: none;
            border-radius: 5px;
        }

        button {
            padding: 10px;
            border: none;
            background: #00adb5;
            color: white;
            border-radius: 5px;
            cursor: pointer;
        }

        ul {
            list-style: none;
            padding: 0;
            margin-top: 20px;
        }

        li {
            background: #333;
            padding: 10px;
            margin-bottom: 10px;
            border-radius: 5px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }

        .completed {
            text-decoration: line-through;
            opacity: 0.6;
        }

        .delete {
            background: red;
            padding: 5px 8px;
            border-radius: 5px;
            cursor: pointer;
            color: white;
            border: none;
        }
    </style>
</head>

<body>

<div class="container">
    <h1>To-Do List</h1>

    <div class="input-section">
        <input type="text" id="taskInput" placeholder="Enter a task">
        <button id="addBtn">Add</button>
    </div>

    <ul id="taskList"></ul>
</div>

<script>
    const input = document.getElementById("taskInput");
    const addBtn = document.getElementById("addBtn");
    const list = document.getElementById("taskList");

    let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

    function saveTasks() {
        localStorage.setItem("tasks", JSON.stringify(tasks));
    }

    function renderTasks() {
        list.innerHTML = "";

        tasks.forEach((task, index) => {
            const li = document.createElement("li");

            if (task.completed) {
                li.classList.add("completed");
            }

            li.innerHTML = `
                <span>${task.text}</span>
                <button class="delete">X</button>
            `;

            li.addEventListener("click", () => {
                task.completed = !task.completed;
                saveTasks();
                renderTasks();
            });

            li.querySelector(".delete").addEventListener("click", (e) => {
                e.stopPropagation();
                tasks.splice(index, 1);
                saveTasks();
                renderTasks();
            });

            list.appendChild(li);
        });
    }

    addBtn.addEventListener("click", () => {
        const text = input.value.trim();

        if (text === "") return;

        tasks.push({
            text: text,
            completed: false
        });

        input.value = "";

        saveTasks();
        renderTasks();
    });

    renderTasks();
</script>

</body>
</html>

```

## OUTPUT
<img width="1919" height="1078" alt="image" src="https://github.com/user-attachments/assets/073c6205-0c46-4d97-9eba-8659e2b51912" />


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
