<template>
    <div>
        <div class="new-task-input-container">
            <textarea
                class="new-task-input"
                rows="8"
                v-model="newTask"
            ></textarea>

            <br>

            <button
                class="add-task-button"
                @click="addTask"
            >Add</button>
        </div>

        <ul>
            <ListItem
                v-for="task in tasks"
                :task="task"
                @toggle-task="toggleTask"
                @remove-task="removeTask"
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
                id: this.tasks.length + 1, // FIXME: this will result in duplicate IDs (find highest ID in array instead, and increment that)
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