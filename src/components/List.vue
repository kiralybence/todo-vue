<template>
    <div>
        <NewListItemInput
            @add-task="addTask"
        />

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
import NewListItemInput from './NewListItemInput.vue';
import ListItem from './ListItem.vue';

export default {
    components: {
        NewListItemInput,
        ListItem,
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