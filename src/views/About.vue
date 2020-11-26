<template>
  <div class="about">
    <h1>This is an about page</h1>
    <section>
      <form>
        <div>
          <input type="radio" id="one" value="one" v-model="picked" /><label
            for="one"
            >one</label
          >
          <input type="radio" id="two" value="two" v-model="picked" /><label
            for="two"
            >two</label
          >
          {{ picked }}
        </div>
        <input type="checkbox" v-model="checked" />
        {{ checked }}
        <div>
          <input
            type="checkbox"
            id="swim"
            value="swim"
            v-model="checkedNames"
          /><label for="swim">swim</label>
          <input
            type="checkbox"
            id="sport"
            value="sport"
            v-model="checkedNames"
          /><label for="sport">sport</label>
          <input
            type="checkbox"
            id="reading"
            value="reading"
            v-model="checkedNames"
          /><label for="reading">reading</label>
          {{ checkedNames }}
        </div>
      </form>
    </section>
    <section class="dom">
      <ul>
        <template v-for="(item, name) in myObject" :key="name">
          <li>{{ item }}</li></template
        >
      </ul>
    </section>
    <section class="watch">
      <p><input placeholder="search" v-model="search" /></p>
    </section>
    <p>{{ count }}</p>
    <div>
      <button @click="clearInterval(message, $event)" :title="message">
        stop
      </button>
    </div>
    <div>
      <span v-if="seen">{{ completedTodosLength }}</span>
    </div>

    <ol>
      <todo-item v-for="todo in todos" :key="todo.id" :todo="todo">{{
        todo.text
      }}</todo-item>
    </ol>
    <div v-html="rawHtml"></div>
  </div>
</template>

<script>
import TodoItem from "../components/TodoItem";
export default {
  components: {
    TodoItem
  },
  data() {
    return {
      picked: "",
      checkedNames: [],
      checked: false,
      count: 0,
      interval: null,
      message: "绑定title attribute",
      seen: true,
      todos: [
        { text: "learn javascript", id: "0" },
        { text: "learn vue", id: "1" }
      ],
      rawHtml: '<span style="color:red">this should be red</span>',
      search: "",
      myObject: {
        title: "learn vue",
        id: "random number"
      }
    };
  },
  mounted() {
    this.interval = setInterval(() => {
      this.count++;
    }, 1000);
  },
  computed: {
    completedTodosLength() {
      return `there are ${this.todos.length} items should be done`;
    }
  },
  watch: {
    search(newValue, oldValue) {
      this.searchItems();
    }
  },
  methods: {
    clearInterval(message, event) {
      console.log(message, event.target.tagName);
      clearInterval(this.interval);
    },
    searchItems() {
      setTimeout(() => {
        console.log(this.search);
      }, 500);
    }
  }
};
</script>
