<script>
import TodoElement from '@/components/TodoElement.vue'

export default {
  data: () => ({
    todoList: []
  }),
  methods: {
    addTodo(todo) {
      const todoItem = {
        message: todo,
        status: 0 // 0 is inComplete, 1 is Complete
      }
      this.todoList = [...this.todoList, todoItem]
    },
    removeTodo(index) {
      this.todoList.splice(index, 1)
    },
    complete(index) {
      this.todoList[index].status = 1
    }
  },
  components: { TodoElement }
}
</script>

<template>
  <main class="todo-wrapper">
    <TodoElement
      :todoList="todoList"
      :addTodo="addTodo"
      :removeTodo="removeTodo"
      :completeTodo="complete"
    />
  </main>
</template>

<style scoped>
.todo-wrapper {
  width: 80dvh;
  display: flex;
  flex: 1;
  flex-direction: column;
  padding: 8dvh 0 2dvh;
}
</style>
