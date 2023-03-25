<script setup>
      import TodoCreator from '../components/TodoCreator.vue';
      import TodoItem from '../components/TodoItem.vue';
      import { uid } from "uid";
      import { ref } from 'vue';

      const todoList = ref([]);

      const createTodo = (todo) => {
        todoList.value.push({
          id: uid(),
          todo,
          isCompleted: null,
          isEditing: null
        });
      };
</script>

<template>
  <main>
    <h1> Create Todos  </h1>
    <TodoCreator @create-todo="createTodo" />

    <ul>
      <TodoItem v-for="todo in todoList" :key="todo.id" :todo="todo" />
    </ul>
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
}

</style>
