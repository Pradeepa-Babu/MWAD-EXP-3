# Ex03 To-Do List using JavaScript
## Date:02/11/2026

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
###INDEX.HTML
```

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>My To-Do App</title>
    <link rel="stylesheet" href="style.css">
</head>

<body>

    <div class="container">

        <h1>My To-Do List</h1>
        <p class="subtitle">Organize your day, one task at a time!</p>

        <div class="input-section">
            <input type="text" id="taskInput"
            placeholder="Enter your task...">

            <button id="addBtn">Add Task</button>
        </div>

        <div class="task-info">
            <p>Total Tasks: <span id="totalTasks">0</span></p>
            <p>Completed: <span id="completedTasks">0</span></p>
        </div>

        <ul id="taskList"></ul>

        <button id="clearBtn" class="clear-btn">
            Clear Completed Tasks
        </button>

    </div>

    <script src="script.js"></script>

</body>
</html>

```
###SCRIPT.JS
```

const taskInput = document.getElementById("taskInput");
const addBtn = document.getElementById("addBtn");
const taskList = document.getElementById("taskList");

const totalTasks = document.getElementById("totalTasks");
const completedTasks = document.getElementById("completedTasks");
const clearBtn = document.getElementById("clearBtn");

// Load saved tasks
let tasks = JSON.parse(localStorage.getItem("tasks")) || [];

// Display tasks
function displayTasks() {

    taskList.innerHTML = "";

    tasks.forEach((task, index) => {

        const li = document.createElement("li");
        li.className = "task";

        if (task.completed) {
            li.classList.add("completed");
        }

        const checkbox = document.createElement("input");
        checkbox.type = "checkbox";
        checkbox.checked = task.completed;

        checkbox.addEventListener("change", () => {
            tasks[index].completed = checkbox.checked;
            saveTasks();
        });

        const span = document.createElement("span");
        span.textContent = task.text;

        const deleteBtn = document.createElement("button");
        deleteBtn.textContent = "Delete";
        deleteBtn.className = "delete-btn";

        deleteBtn.addEventListener("click", () => {
            tasks.splice(index, 1);
            saveTasks();
        });

        li.appendChild(checkbox);
        li.appendChild(span);
        li.appendChild(deleteBtn);

        taskList.appendChild(li);
    });

    totalTasks.textContent = tasks.length;

    completedTasks.textContent =
        tasks.filter(task => task.completed).length;
}

// Save tasks
function saveTasks() {

    localStorage.setItem("tasks", JSON.stringify(tasks));

    displayTasks();
}

// Add new task
function addTask() {

    const taskText = taskInput.value.trim();

    if (taskText === "") {
        alert("Please enter a task!");
        return;
    }

    tasks.push({
        text: taskText,
        completed: false
    });

    taskInput.value = "";

    saveTasks();
}

// Add button event
addBtn.addEventListener("click", addTask);

// Enter key event
taskInput.addEventListener("keydown", (event) => {

    if (event.key === "Enter") {
        addTask();
    }

});

// Clear completed tasks
clearBtn.addEventListener("click", () => {

    tasks = tasks.filter(task => !task.completed);

    saveTasks();
});

// Display saved tasks when page loads
displayTasks();

```
### STYLE.CSS
```

* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}

body {
    font-family: Arial, sans-serif;
    background: linear-gradient(135deg, #667eea, #764ba2);
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 20px;
}

.container {
    background: white;
    width: 100%;
    max-width: 500px;
    padding: 30px;
    border-radius: 15px;
    box-shadow: 0 10px 30px rgba(0,0,0,0.2);
}

h1 {
    text-align: center;
    color: #333;
    margin-bottom: 10px;
}

.subtitle {
    text-align: center;
    color: #777;
    margin-bottom: 25px;
}

.input-section {
    display: flex;
    gap: 10px;
    margin-bottom: 20px;
}

input {
    flex: 1;
    padding: 12px;
    border: 1px solid #ccc;
    border-radius: 8px;
    outline: none;
    min-width: 0;
}

input:focus {
    border-color: #667eea;
}

button {
    padding: 12px 16px;
    border: none;
    background: #667eea;
    color: white;
    border-radius: 8px;
    cursor: pointer;
}

button:hover {
    background: #5265c5;
}

.task-info {
    display: flex;
    justify-content: space-between;
    color: #555;
    margin-bottom: 20px;
    font-size: 14px;
}

#taskList {
    list-style: none;
}

.task {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 10px;
    background: #f4f4f9;
    padding: 12px;
    border-radius: 8px;
    margin-bottom: 10px;
}

.task span {
    flex: 1;
    overflow-wrap: anywhere;
}

.task.completed span {
    text-decoration: line-through;
    color: gray;
}

.task input[type="checkbox"] {
    flex: 0 0 auto;
    width: 18px;
    height: 18px;
}

.delete-btn {
    background: #ff4d4d;
    padding: 8px 12px;
}

.delete-btn:hover {
    background: #d93636;
}

.clear-btn {
    width: 100%;
    margin-top: 15px;
    background: #333;
}

.clear-btn:hover {
    background: #111;
}

@media (max-width: 400px) {
    .container {
        padding: 20px;
    }

    .input-section {
        flex-direction: column;
    }
}

```

## OUTPUT


## RESULT
The program for creating To-do list using JavaScript is executed successfully.
