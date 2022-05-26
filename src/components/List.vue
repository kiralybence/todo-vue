<template>
    <div>
        <textarea v-model="newTask"></textarea>
        <button @click="addTask">Add</button>

        <ul>
            <ListItem
                v-for="task in tasks"
                :task="task"
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
            this.tasks.push(this.newTask);
            this.newTask = '';
        },
    },
}
</script>