<template>
    <ul>
        <ListItem
            v-for="task in tasks"
            :key="task.id"
            :task="task"
            @remove-task="removeTask"
        />
    </ul>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    props: [
        'tasks',
    ],
    components: {
        ListItem,
    },
    methods: {
        removeTask(id) {
            this.$emit('removeTask', id);
        },
    },
}
</script>