<template>
    <li>
        <span
            class="task"
            :class="{ 'strikethrough': task.completed }"
            @click="toggleComplete"
        >
            {{ task.description }}
        </span>

        <button
            class="removeTaskButton"
            @click="remove"
        >Remove</button>
    </li>
</template>

<script>
export default {
    props: [
        'task'
    ],
    methods: {
        toggleComplete() {
            this.$emit('toggleComplete', this.task.id);
        },
        remove() {
            this.$emit('remove', this.task.id);
        },
    },
}
</script>