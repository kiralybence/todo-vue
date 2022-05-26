<template>
    <div>
        <div style="margin-bottom: 30px;">
            <textarea
                v-model="newTask"
                style="width: 100%;"
                rows="8"
            ></textarea>
            <br>
            <button style="padding: 10px 50px;" @click="addTask">Add</button>
        </div>

        <ul>
            <ListItem
                v-for="task in tasks"
                :task="task"
                @toggle-complete="toggleTask"
                @remove="removeTask"
            />
        </ul>
    </div>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    components: {
        ListItem,
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
        toggleTask(id) {
            this.tasks = this.tasks.map(task => {
                if (task.id === id) {
                    task.completed = !task.completed;
                }

                return task;
            });
        },
        removeTask(id) {
            this.tasks = this.tasks.filter(task => task.id !== id);
        },
    },
}
</script>