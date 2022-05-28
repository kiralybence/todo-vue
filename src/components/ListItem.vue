<template>
    <li>
        <div v-if="!isEditing">
            <span
                class="task"
                :class="{ 'strikethrough': task.completed }"
                @click="toggleCompleted"
            >
                {{ task.description }}
            </span>

            <button
                class="task-button"
                @click="toggleEditor"
            >Edit</button>

            <button
                class="task-button"
                @click="removeTask"
            >Remove</button>
        </div>

        <div v-else>
            <ListItemEditor
                :task="task"
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
        'task',
    ],
    data() {
        return {
            isEditing: false,
        };
    },
    methods: {
        toggleCompleted() {
            this.task.completed = !this.task.completed;
        },
        toggleEditor() {
            this.isEditing = !this.isEditing;
        },
        removeTask() {
            this.$emit('removeTask', this.task.id);
        },
    },
}
</script>