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
                :key="task.id"
                :task="task"
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
        getNewId() {
            if (!this.tasks.length) {
                return 1;
            }

            let prevHighestId = this.tasks.reduce((a, b) => a.id > b.id ? a : b).id;

            return prevHighestId + 1;
        },
        addTask() {
            this.tasks.push({
                id: this.getNewId(),
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