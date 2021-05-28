<template>
    <div class="todo-item">
            <input type="checkbox" :checked="todo.completed" v-on:change="itemChecked">
            <span v-bind:class="{'completed': todo.completed}">{{todo.title}}</span>
            <button class="delete" @click="$emit('delete-todo', todo.id)">x</button>
    </div>
</template>

<script>
export default {
    name: "TodoItem",
    props: [
        "todo"
    ],
    methods: {
        itemChecked() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>

<style>
.todo-item {
    background: #f4f4f4;
    padding: 10px;
    border-bottom: 1px #ccc dotted;
}

.completed {
    text-decoration: line-through;
}

input[type="checkbox"] {
    margin-right: 5px;
}

.delete {
    background: #ff0000;
    color: #fff;
    border: none;
    padding: 2px 9px;
    cursor: pointer;
    float: right;
    border-radius: 50%;
}
</style>