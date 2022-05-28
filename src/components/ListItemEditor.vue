<template>
    <input type="text" v-model="draft">

    <button
        class="item-button"
        @click="save"
        :disabled="!draft.trim().length"
    >Save</button>

    <button
        class="item-button"
        @click="cancel"
    >Cancel</button>
</template>

<script>
export default {
    props: [
        'item',
    ],
    emits: [
        'editSaved',
        'editCancelled',
    ],
    data() {
        return {
            draft: this.item.description,
        };
    },
    methods: {
        save() {
            this.item.description = this.draft.trim();
            this.$emit('editSaved');
        },
        cancel() {
            this.draft = this.item.description;
            this.$emit('editCancelled');
        },
    },
}
</script>