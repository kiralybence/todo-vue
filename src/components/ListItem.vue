<template>
    <li>
        <span
            :style="{
                'text-decoration': task.completed ? 'line-through' : 'initial',
            }"
            style="cursor: pointer;"
            @click="toggleComplete"
        >
            {{ task.description }}
        </span>

        <button style="margin-left: 10px;" @click="remove">Remove</button>
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
    }
}
</script>