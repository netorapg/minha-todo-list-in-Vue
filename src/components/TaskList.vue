<template>
    <div>
        <input v-model="newTask" @keyup.enter="addTask" placeholder="Adicionar nova tarefa" />
        <button @click="addTask">Adicionar</button>
        <ul>
            <li v-for="(task, index) in tasks" :key="index">
                <span :class="{ done: task.done }" @click="toggleTask(index)">{{ task.text }}</span>
                <button @click="removeTask(index)">Remover</button>
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
</style>
