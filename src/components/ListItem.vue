<template>
    <li>
        {{ task.description }}

        <button @click="remove">Remove</button>
    </li>
</template>

<script>
export default {
    props: [
        'task'
    ],
    methods: {
        remove() {
            this.$emit('remove', this.task.id);
        }
    }
}
</script>