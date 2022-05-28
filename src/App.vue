<template>
    <div id="container">
        <div id="title">
            <h1>TODO app</h1>
            <hr>
        </div>

        <NewListItemInput
            @add-item="addItem"
        />

        <List
            :items="items"
            @remove-item="removeItem"
        />
    </div>
</template>

<script>
import NewListItemInput from './components/NewListItemInput.vue';
import List from './components/List.vue';

export default {
    components: {
        NewListItemInput,
        List,
    },
    data() {
        return {
            items: [],
        };
    },
    methods: {
        getNewId() {
            if (!this.items.length) {
                return 1;
            }

            let prevHighestId = this.items.reduce((a, b) => a.id > b.id ? a : b).id;

            return prevHighestId + 1;
        },
        addItem(draft) {
            this.items.push({
                id: this.getNewId(),
                description: draft,
                completed: false,
            });
        },
        removeItem(id) {
            this.items = this.items.filter(item => item.id !== id);
        },
    },
}
</script>

<style>
@import './assets/base.css';
</style>
