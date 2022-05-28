<template>
    <div>
        <textarea
            rows="8"
            v-model="draft"
        ></textarea>

        <br>

        <button
            @click="addItem"
            :disabled="!draft.trim().length"
        >Add</button>
    </div>
</template>

<script>
export default {
    emits: [
        'addItem',
    ],
    data() {
        return {
            draft: '',
        };
    },
    methods: {
        addItem() {
            this.$emit('addItem', this.draft.trim());
            this.draft = '';
        },
    },
}
</script>

<style scoped>
    textarea {
        width: 100%;
        resize: none;
    }

    button {
        padding: 10px 50px;
    }
</style>