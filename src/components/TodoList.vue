<template>
    <div>
        <div v-bind:key="item.id" v-for="item in items">
            <TodoItem v-bind:todo="item" v-on:delete-todo="$emit('delete-todo', item.id)"/>
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue'

export default {
    name: "TodoList",
    components: {
        TodoItem
    },
    props: ["items"]
}
</script>