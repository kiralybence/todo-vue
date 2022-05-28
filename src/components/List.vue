<template>
    <ul>
        <ListItem
            v-for="item in items"
            :key="item.id"
            :item="item"
            @remove-item="removeItem"
        />
    </ul>
</template>

<script>
import ListItem from './ListItem.vue';

export default {
    props: [
        'items',
    ],
    emits: [
        'removeItem',
    ],
    components: {
        ListItem,
    },
    methods: {
        removeItem(id) {
            this.$emit('removeItem', id);
        },
    },
}
</script>