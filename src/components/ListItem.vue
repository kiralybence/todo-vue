<template>
    <li>
        <div v-if="!isEditing">
            <span
                class="item"
                :class="{ 'strikethrough': item.completed }"
                @click="toggleCompleted"
            >
                {{ item.description }}
            </span>

            <button
                class="item-button"
                @click="toggleEditor"
            >Edit</button>

            <button
                class="item-button"
                @click="removeItem"
            >Remove</button>
        </div>

        <div v-else>
            <ListItemEditor
                :item="item"
                @edit-saved="toggleEditor"
                @edit-cancelled="toggleEditor"
            />
        </div>
    </li>
</template>

<script>
import ListItemEditor from './ListItemEditor.vue';

export default {
    components: {
        ListItemEditor,
    },
    props: [
        'item',
    ],
    emits: [
        'removeItem',
    ],
    data() {
        return {
            isEditing: false,
        };
    },
    methods: {
        toggleCompleted() {
            this.item.completed = !this.item.completed;
        },
        toggleEditor() {
            this.isEditing = !this.isEditing;
        },
        removeItem() {
            this.$emit('removeItem', this.item.id);
        },
    },
}
</script>