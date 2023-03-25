<script setup>
      import TodoCreator from '../components/TodoCreator.vue';
      import TodoItem from '../components/TodoItem.vue';
      import { uid } from "uid";
      import { ref } from 'vue';
      import { Icon } from '@iconify/vue';


      const todoList = ref([]);

      const createTodo = (todo) => {
        todoList.value.push({
          id: uid(),
          todo,
          isCompleted: null,
          isEditing: null
        });
};
        const toggleTodoComplete = (todoPos) => {
          todoList.value[todoPos].isCompleted = !todoList.value[todoPos].isCompleted
        };
        const toggleEditTodo = (todoPos) => {
          todoList.value[todoPos].isEditing = !todoList.value[todoPos].isEditing
        };
</script>

<template>
  <main>
    <h1> Create Todos  </h1>
    <TodoCreator @create-todo="createTodo" />

    <ul class="todo-list" v-if="todoList.length > 0">
      <TodoItem v-for="(todo, index) in todoList" :key="todo.id" :todo="todo" :index="index" @toggle-complete="toggleTodoComplete"
       @edit-todo="toggleEditTodo"

       />
    </ul>
    <p class="todo-msg" v-else>
      <Icon icon="noto-v1:sad-but-relieved-face" width="22" />
      <span>You have no todo's to complete add one</span>
    </p>
  </main>
</template>


<style lang="scss" scoped>

main {
  display: flex;
  flex-direction: column;
  max-width: 500px;
  width: 100%;
  margin: 0  auto;
  padding: 40px 16px;

  h1 {
    margin-bottom: 16px;
    text-align: center;
  }
  .todo-list {
    display: flex;
    flex-direction: column;
    list-style: none;
    margin-top:24px;
    gap: 20px;

  }
  .todo-msg {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 8px;
    margin-top: 24px;
  }
}

</style>
