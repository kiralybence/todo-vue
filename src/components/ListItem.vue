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
                @click="toggleEditor"
            >Edit</button>

            <button
                @click="removeItem"
            >Remove</button>
        </div>

        <ListItemEditor
            :item="item"
            v-else
            @edit-saved="toggleEditor"
            @edit-cancelled="toggleEditor"
        />
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

<style scoped>
    .strikethrough {
        text-decoration: line-through;
    }

    .item {
        cursor: pointer;
    }

    button {
        margin-left: 10px;
    }
</style>