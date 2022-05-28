<template>
    <div>
        <input type="text" v-model="draft">

        <button
            @click="save"
            :disabled="!draft.trim().length"
        >Save</button>

        <button
            @click="cancel"
        >Cancel</button>
    </div>
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

<style scoped>
    button {
        margin-left: 10px;
    }
</style>