<!DOCTYPE html>
<html>
<head>
    <style>
        body {
            font-family: Arial, sans-serif;
            text-align: center;
            background-color: #f4f4f4;
            margin: 0;
            padding: 0;
        }

        .todo-app {
            max-width: 400px;
            margin: 20px auto;
            background-color: #fff;
            border-radius: 5px;
            padding: 20px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.2);
        }

        h1 {
            color: #333;
        }

        .input-container {
            margin: 10px 0;
        }

        input[type="text"] {
            width: 70%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 3px;
            outline: none;
        }

        button {
            background: #4caf50;
            color: #fff;
            border: none;
            border-radius: 3px;
            padding: 10px 20px;
            cursor: pointer;
        }

        button:hover {
            background: #45a049;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            margin: 5px 0;
            display: flex;
            align-items: center;
            background-color: #f9f9f9;
            padding: 10px;
            border-radius: 3px;
        }

        .completed {
            text-decoration: line-through;
            color: gray;
        }

        button.delete {
            margin-left: 10px;
            background: #ff3333;
            color: #fff;
            border: none;
            border-radius: 3px;
            padding: 5px 10px;
            cursor: pointer;
        }

        button.delete:hover {
            background: #ff0000;
        }
    </style>
</head>
<body>
    <div class="todo-app">
        <h1>My To-Do List</h1>
        <div class="input-container">
            <input type="text" id="taskInput" placeholder="Add a new task">
            <button onclick="addTask()">Add</button>
        </div>
        <ul id="taskList">
        </ul>
    </div>

    <script>
        function addTask() {
            const taskInput = document.getElementById("taskInput");
            const taskText = taskInput.value.trim();

            if (taskText !== "") {
                const taskList = document.getElementById("taskList");
                const li = document.createElement("li");
                const checkbox = document.createElement("input");
                checkbox.type = "checkbox";
                checkbox.addEventListener("change", toggleTaskCompletion);
                const taskTextElement = document.createElement("span");
                taskTextElement.textContent = taskText;
                const deleteButton = document.createElement("button");
                deleteButton.className = "delete";
                deleteButton.textContent = "Delete";
                deleteButton.addEventListener("click", deleteTask);

                li.appendChild(checkbox);
                li.appendChild(taskTextElement);
                li.appendChild(deleteButton);
                taskList.appendChild(li);

                taskInput.value = "";
            }
        }

        function toggleTaskCompletion(event) {
            const taskTextElement = event.target.nextElementSibling;
            taskTextElement.classList.toggle("completed");
        }

        function deleteTask(event) {
            const li = event.target.parentElement;
            li.remove();
        }
    </script>
</body>
</html>
