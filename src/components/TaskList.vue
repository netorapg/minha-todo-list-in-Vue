<template>
    <div>
        <input v-model="newTask" @keyup.enter="addTask" placeholder="Adicionar nova tarefa" class="input-bar" />
        <button @click="addTask" class="add-button">Adicionar</button>
        <ul class="task-list">
            <li v-for="(task, index) in tasks" :key="index">
                <span :class="{ done: task.done }" @click="toggleTask(index)">
                    <i v-if="task.done" class="fas fa-check-circle"></i>{{ task.text }}</span>
                <button @click="removeTask(index)" class="remove-button">Remover</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTask: '',
            tasks: []
        };
    },
    methods: {
        addTask() {
            if (this.newTask.trim() !== '') {
                this.tasks.push({ text: this.newTask, done: false });
                this.newTask = '';
            }
        },
        removeTask(index) {
            this.tasks.splice(index, 1);
        },
        toggleTask(index) {
            this.tasks[index].done = !this.tasks[index].done;
        }
    }
};
</script>

<style>
.done {
    text-decoration: line-through;
}

.add-button {
    background-color: #4CAF50;
    color: white;
    border: none;
    padding: 10px 20px;
    text-align: center;
    display: inline-block;
    font-size: 16px;
    margin: 10px 2px;
    cursor: pointer;
    border-radius: 12px;
    transition: background-color 0.3s ease;
}

.add-button:hover {
    background-color: #4Ca049;
}

.remove-button {
    background-color: #f44336;
    color: white;
    border: none;
    padding: 5px 10px;
    text-align: center;
    display: inline-block;
    font-size: 14px;
    margin: 5px 2px;
    cursor: pointer;
    border-radius: 8px;
    transition: background-color 0.3s ease;
}

.remove-button:hover {
    background-color: #e53935;
}

.input-bar {
    width: calc(100% - 44px);
    padding: 10px;
    margin: 10px 2px;
    font-size: 16px;
    border: 2px solid #ccc;
    border-radius: 12px;
    box-sizing: border-box;
    transition: border-color 0.3s ease;
}

.input-bar:focus {
    border-color: #4caf50;
    outline: none;
}

.task-list {
    list-style-type: none;
    padding: 0;
}

.task-list li {
    margin-bottom: 10px;
}

.task-list li span {
    display: inline-block;
    margin-right: 10px;
    vertical-align: middle;
}

.task-list li .fa-check-circle {
    color: #4CAF50;
    margin-right: 5px;
}
</style>
