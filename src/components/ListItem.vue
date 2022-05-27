<template>
    <li>
        <span
            class="task"
            :class="{ 'strikethrough': task.completed }"
            @click="toggleTask"
        >
            {{ task.description }}
        </span>

        <button
            class="remove-task-button"
            @click="removeTask"
        >Remove</button>
    </li>
</template>

<script>
export default {
    props: [
        'task',
    ],
    methods: {
        toggleTask() {
            this.$emit('toggleTask', this.task.id);
        },
        removeTask() {
            this.$emit('removeTask', this.task.id);
        },
    },
}
</script>