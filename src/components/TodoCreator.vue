<script setup>
import { reactive } from "vue";
import TodoButton from "./TodoButton.vue";


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
    todoState.errMssg = "Todo value cannot be empty!";
};

</script>


<template>
    <div>
        <div class="input-wrapper" :class="{'input-err': todoState.invalid }">
            <input type="text" v-model="todoState.todo">
            <TodoButton  @click="createTodo()" />

        </div>
        <p  v-show="todoState.invalid" class="err-msg"> {{ todoState.errMssg }} </p>
    </div>
</template>


<style lang="scss" scoped>
.input-wrapper {
    display: flex;
    transition: all 250ms ease;
    border: 2px solid #41b080;

    &.input-err {
        border: 2px solid red;
    }
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


}

.err-msg {
    color: red;
    font-size: 1.3rem;
    font-style: italic;
    text-align: center;
    margin-top: .375rem;
}
</style>