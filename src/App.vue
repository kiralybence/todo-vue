<template>
    <div id="container">
        <div id="title">
            <h1>TODO app</h1>
            <hr>
        </div>

        <NewListItemInput
            @add-task="addTask"
        />

        <List
            :tasks="tasks"
            @remove-task="removeTask"
        />
    </div>
</template>

<script>
import NewListItemInput from './components/NewListItemInput.vue';
import List from './components/List.vue';

export default {
    components: {
        NewListItemInput,
        List,
    },
    data() {
        return {
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
        addTask(draft) {
            this.tasks.push({
                id: this.getNewId(),
                description: draft,
                completed: false,
            });
        },
        removeTask(id) {
            this.tasks = this.tasks.filter(task => task.id !== id);
        },
    },
}
</script>

<style>
@import './assets/base.css';
</style>
