<template>
    <div class="new-item-input-container">
        <textarea
            class="new-item-input"
            rows="8"
            v-model="draft"
        ></textarea>

        <br>

        <button
            class="add-item-button"
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