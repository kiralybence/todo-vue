<template>
    <input type="text" v-model="draft">

    <button
        class="task-button"
        @click="save"
    >Save</button>

    <button
        class="task-button"
        @click="cancel"
    >Cancel</button>
</template>

<script>
export default {
    props: [
        'task',
    ],
    emits: [
        'editSaved',
        'editCancelled',
    ],
    data() {
        return {
            draft: this.task.description,
        };
    },
    methods: {
        save() {
            this.task.description = this.draft;
            this.$emit('editSaved');
        },
        cancel() {
            this.draft = this.task.description;
            this.$emit('editCancelled');
        },
    },
}
</script>