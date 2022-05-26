<template>
    <div>
        <textarea v-model="newTask"></textarea>
        <button @click="addTask">Add</button>

        <ul>
            <ListItem
                v-for="task in tasks"
                :task="task"
                @remove="removeTask"
            />
        </ul>
    </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    components: {
        ListItem
    },
    data() {
        return {
            newTask: '',
            tasks: [],
        };
    },
    methods: {
        addTask() {
            this.tasks.push({
                id: this.tasks.length + 1,
                description: this.newTask,
                completed: false,
            });

            this.newTask = '';
        },
        removeTask(id) {
            this.tasks = this.tasks.filter(task => task.id !== id);
        },
    },
}
</script>