<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List App</title>
    <style>
        body {
            font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
            margin: 0;
            padding: 0;
            display: flex;
            justify-content: center;
            align-items: center;
            min-height: 100vh;
            background-color: #5B9A8B;
        }

        .container {
            background-color: #fff;
            padding: 20px;
            border-radius: 10px;
            box-shadow: 0px 0px 20px rgba(0, 0, 0, 0.1);
            width: 300px;
            text-align: center;
        }

        h1 {
            font-size: 24px;
            margin-bottom: 20px;
            color: #333;
        }

        #taskInput {
            width: 100%;
            padding: 10px;
            border: 1px solid #ccc;
            border-radius: 5px;
            margin-bottom: 10px;
            font-size: 14px;
        }

        #addTaskButton {
            display: block;
            width: 100%;
            padding: 10px;
            background-color: #F7E987;
            color: white;
            border: none;
            border-radius: 5px;
            cursor: pointer;
            font-size: 14px;
            transition: background-color 0.3s ease;
        }

        #addTaskButton:hover {
            background-color: #C8E4B2;
        }

        ul {
            list-style-type: none;
            padding: 0;
        }

        li {
            display: flex;
            justify-content: space-between;
            align-items: center;
            padding: 10px 0;
            border-bottom: 1px solid #e0e0e0;
            color: #555;
            font-size: 14px;
        }

        .deleteTaskButton {
            padding: 2px 8px;
            background-color: #7EAA92;
            color: white;
            border: none;
            border-radius: 3px;
            cursor: pointer;
            font-size: 12px;
            transition: background-color 0.3s ease;
        }

        .deleteTaskButton:hover {
            background-color: #d12f24;
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <input type="text" id="taskInput" placeholder="Enter a task">
        <button id="addTaskButton">Add Task</button>
        <ul id="taskList"></ul>
    </div>
    <script>
        const taskInput = document.getElementById("taskInput");
        const addTaskButton = document.getElementById("addTaskButton");
        const taskList = document.getElementById("taskList");

        addTaskButton.addEventListener("click", addTask);

        function addTask() {
            const taskText = taskInput.value.trim();

            if (taskText !== "") {
                const li = document.createElement("li");
                li.innerHTML = `
                    <span>${taskText}</span>
                    <button class="deleteTaskButton">Delete</button>
                `;

                taskList.appendChild(li);
                taskInput.value = "";

                const deleteTaskButton = li.querySelector(".deleteTaskButton");
                deleteTaskButton.addEventListener("click", () => {
                    taskList.removeChild(li);
                });
            }
        }
    </script>
</body>
</html>
