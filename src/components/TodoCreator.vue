<script setup>
import { reactive} from "vue";

const emit = defineEmits(["create-todo"])

const todoState = reactive({
    todo: "",
    invalid: null,
    errMssg: "",
});

const createTodo = () => {
    // create todo

    todoState.invalid = null;
    if (todoState.todo !== "") {

        emit("create-todo", todoState.todo);
        todoState.todo = "";

        return;
    }

    todoState.invalid = true;
    todoState.errMssg = "Todo value cannot be empty";
};

</script>


<template>
    <div class="input-wrapper">
        <input type="text" v-model="todoState.todo">
        <button @click="createTodo()">Create</button>
    </div>
</template>


<style lang="scss" scoped>
.input-wrapper {
    display: flex;
    transition: all 250ms ease;
    border: 2px solid #41b080;
    &:focus-within {
        box-shadow: 0 -4px 6px -1px rgba(0 0 0 / 0.1),
        0 -2px 4px -2px rgb(0 0 0 / 0.1);
    }
    input{
        width: 100%;
        padding: 8px 6px;
        border: none;
        &:focus{
            outline: none;
        }

    }
    button {
        padding: 8px 16px;
        border: none;
    }
}
</style>