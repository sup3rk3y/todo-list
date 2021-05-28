<template>
    <div>
        <form @submit="createTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo item">
            <input type="submit" value="Submit" class="btn btn-success">
        </form>
    </div>
</template>

<script>

export default {
    name: "CreateTodoItem",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        createTodo(e) {
            e.preventDefault();

            const newTodo = {
                title: this.title,
                completed: false
            }

            this.$emit('create-todo', newTodo);
            this.title = '';
        }
    }
}
</script>

<style>
form {
    display: flex;
}

input[type="text"] {
    flex: 10;
    padding: 5px;
}

input[type="submit"] {
    flex: 2;
}

</style>