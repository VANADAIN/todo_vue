<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">

        <input type="checkbox" v-on:change="markComplete">
        {{todo.title}}
        
        <div>
        <button @click="$emit('del-todo', todo.id)" class="del"> X </button>
        </div>
        
    </div>
</template>

<script>

export default {
    name: "TodoItem",
    props: ["todo"],
    methods: {
        markComplete(){
            this.todo.completed = ! this.todo.completed
        }
    }
}
</script>

<style scoped lang="sass">
    .todo-item
        display: flex
        justify-content: space-between
        padding: 20px
        background-color: #f4f4f4
        border-bottom: 1px #ccc dotted
        font-size: 24px
        
    .is-complete
        text-decoration: line-through

    .del
        outline: none
        cursor: pointer
        background-color: red
        color: white
        border-radius: 50px
        border: none
        width: 25px
        height: 25px
        margin-left: 50 px
</style>
