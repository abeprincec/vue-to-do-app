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
        @keyup.enter="submit">
      <button type="submit">Add</button>
    </form>
    <div v-if="lists.length">
      <h3>My Todo Tasks</h3>
      <ul>
        <li
          v-for="list in lists"
          :key="list.id">
          <span :class="{completed: list.isComplete}">{{ list.title }}</span>
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
</style>
