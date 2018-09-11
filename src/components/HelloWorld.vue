<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <form
      name="todo-form"
      method="post"
      action=""
      @submit.prevent="addTask">
      <input
        v-model="addTodoInput"
        name="add-todo"
        type="text"
        class="effect-1"
        @keyup.enter="submit">
      <button type="submit">Add</button>
    </form>
    <div v-if="lists.length">
      <h3>My Todo Tasks</h3>
      <ul>
        <li
          v-for="list in lists"
          :key="list.id"
          :class="{completed: list.isComplete}">
          {{ list.title }}
        </li>
      </ul>
      <ul>
        <li>
          <a
            href="https://vuejs.org"
            target="_blank">
            Core Docs
          </a>
        </li>
        <li>
          <a
            href="https://forum.vuejs.org"
            target="_blank">
            Forum
          </a>
        </li>
        <li>
          <a
            href="https://chat.vuejs.org"
            target="_blank">
            Community Chat
          </a>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: 'Hello World',
      msg: 'Welcome to Your Vue.js to-do list App',
      addTodoInput: '', // <--- add here
      lists: []
    }
  },
  methods: {
    addTask() {
      this.lists.push({
        id: this.lists.length + 1,
        title: this.addTodoInput,
        isComplete: false
      })

      this.addTodoInput = '' // clear the input after successful submission
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}

input[type='text'] {
  font: 15px/24px 'Muli', sans-serif;
  color: #333;
  width: 30%;
  letter-spacing: 1px;
}

:focus {
  outline: none;
}

.effect-1,
.effect-2,
.effect-3 {
  border: 0;
  padding: 7px 0;
  border-bottom: 1px solid #ccc;
}

.effect-1 ~ .focus-border {
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background-color: #4caf50;
  transition: 0.4s;
}
.effect-1:focus ~ .focus-border {
  width: 100%;
  transition: 0.4s;
}
</style>
