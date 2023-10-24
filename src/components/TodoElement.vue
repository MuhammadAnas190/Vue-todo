<script>
export default {
  props: ['todoList', 'addTodo', 'removeTodo', 'completeTodo'],
  data() {
    return {
      message: ''
    }
  },
  methods: {
    handleChangeTodo(evt) {
      this.message = evt.target.value
    },
    handleAddTodo() {
      console.log('add', this.message, this.todoList)
      this.addTodo(this.message)
      this.message = ''
    }
  }
}
</script>

<template>
  <div class="todo">
    <div class="todo-element" v-for="(item, index) of this.todoList" :key="item">
      <h4 :class="item.status === 1 && 'complete'" @click="completeTodo(index)">
        {{ item.message }}
      </h4>
      <div>
        <button @click="removeTodo(index)">Delete</button>
      </div>
    </div>
  </div>
  <div class="add-todo">
    <input type="text" @input="handleChangeTodo" />
    <button type="text" @click="handleAddTodo">Add</button>
  </div>
</template>

<style scoped>
.todo {
  display: flex;
  flex-wrap: nowrap;
  flex-direction: column;
  justify-content: space-between;
}
.todo-element {
  display: flex;
  flex: 1;
  flex-direction: row;
  justify-content: space-between;
  width: 100%;
}
h4 {
  font-weight: 500;
  font-size: 1.5rem;
  position: relative;
  top: -10px;
}
.add-todo {
  display: flex;
  justify-content: space-between;
  & input {
    width: 80%;
  }
}
.complete {
  color: #51b4a3;
  text-decoration: line-through;
}
</style>
