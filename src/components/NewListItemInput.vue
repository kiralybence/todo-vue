<template>
    <div class="new-task-input-container">
        <textarea
            class="new-task-input"
            rows="8"
            v-model="draft"
        ></textarea>

        <br>

        <button
            class="add-task-button"
            @click="addTask"
        >Add</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            draft: '',
        };
    },
    methods: {
        addTask() {
            this.$emit('addTask', this.draft);
            this.draft = '';
        },
    },
}
</script>