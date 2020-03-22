<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add todo...">
            <input type="submit" value='submit' class="btn">
        </form>
    </div>
</template>


<script>
import uuid from "uuid"
export default {
    name: "AddTodo",
    data(){
        return{
            title: ""
        }
    },
    methods:{
        addTodo(e) {
            e.preventDefault()
            const newTodo = {
                id: uuid.v4(),
                title: this.title,
                completed: false
            }
            // send up to parent
            this.$emit("add-todo", newTodo)
            this.title = ""
        }
    }
}
</script>


<style lang="sass" scoped>
    form
        display: flex
    input[type="text"]
        flex: 10px
        padding: 5px
    input[type="submit"]
        width: 100px


</style>
