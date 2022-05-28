<template>
    <div id="container">
        <h1>TODO app</h1>
        <hr>

        <NewListItemInput
            class="new-list-item-input"
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

<style scoped>
    #container {
        max-width: 600px;
        margin: 0 auto;
        padding: 0 20px;
    }

    h1 {
        width: 100%;
        text-align: center;
    }

    hr {
        margin-bottom: 20px;
    }

    .new-list-item-input {
        margin-bottom: 30px;
    }
</style>