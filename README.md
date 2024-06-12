HTML

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>To-Do List</title>
    <link rel="stylesheet" href="Priyansh.css">
</head>
<body>
    <div class="container">
        <h1>To-Do List</h1>
        <div class="input-container">
            <input type="text" id="new-task-input" placeholder="Add a new task...">
            <button id="add-task-button">Add</button>
        </div>
        <ul id="task-list"></ul>
    </div>
    <script src="Priyansh.js"></script>
</body>
</html>


CSS

body {
    font-family: Arial, sans-serif;
    background-color: #f0f0f0;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100vh;
    margin: 0;
}

.container {
    background-color: #fff;
    padding: 20px;
    border-radius: 8px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
    width: 100%;
    max-width: 400px;
}

h1 {
    text-align: center;
    color: #333;
}

.input-container {
    display: flex;
    justify-content: space-between;
    margin-bottom: 20px;
}

#new-task-input {
    flex: 1;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
}

#add-task-button {
    padding: 10px 20px;
    background-color: #28a745;
    color: white;
    border: none;
    border-radius: 4px;
    margin-left: 10px;
    cursor: pointer;
}

#add-task-button:hover {
    background-color: #218838;
}

#task-list {
    list-style: none;
    padding: 0;
    margin: 0;
}

.task-item {
    background-color: #fafafa;
    padding: 10px;
    border: 1px solid #ddd;
    border-radius: 4px;
    margin-bottom: 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
}

.task-item.completed {
    text-decoration: line-through;
    color: #777;
}

.task-item button {
    background-color: #dc3545;
    color: white;
    border: none;
    border-radius: 4px;
    padding: 5px 10px;
    cursor: pointer;
}

.task-item button:hover {
    background-color: #c82333;
}



JAVASCRIPT


document.addEventListener('DOMContentLoaded', () => {
    const taskInput = document.getElementById('new-task-input');
    const addTaskButton = document.getElementById('add-task-button');
    const taskList = document.getElementById('task-list');

    addTaskButton.addEventListener('click', () => {
        const taskText = taskInput.value.trim();
        if (taskText) {
            addTask(taskText);
            taskInput.value = '';
            taskInput.focus();
        }
    });

    taskList.addEventListener('click', (e) => {
        if (e.target.tagName === 'BUTTON') {
            const taskItem = e.target.parentElement;
            taskList.removeChild(taskItem);
        } else if (e.target.tagName === 'LI') {
            e.target.classList.toggle('completed');
        }
    });

    function addTask(taskText) {
        const taskItem = document.createElement('li');
        taskItem.className = 'task-item';
        taskItem.textContent = taskText;

        const deleteButton = document.createElement('button');
        deleteButton.textContent = 'Delete';
        taskItem.appendChild(deleteButton);

        taskList.appendChild(taskItem);
    }
});
