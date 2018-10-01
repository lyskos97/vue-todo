<template>
  <div>
    <v-app>
      <v-toolbar app></v-toolbar>
      <v-content app>
        <v-container>
          <AddNewBar @newTodo="addTodo" />
          <List :todos="todos" @todoToggle="toggleTodo" />
          <FilterBar :filter="filter" @filterChange="handleFilterChange" />
        </v-container>
      </v-content>
      <v-footer app></v-footer>
    </v-app>
  </div>
</template>

<script>
import FilterBar from './FilterBar';
import AddNewBar from './AddNewBar';
import List from './List';

export default {
  data() {
    return {
      allTodos: [
        { id: 1, text: 'Kek', done: true },
        { id: 2, text: 'Bols', done: false },
        { id: 3, text: 'Fak vju', done: false }
      ],
      filter: 'ALL' // ALL, DONE, UNDONE
    };
  },
  computed: {
    todos() {
      if (this.filter === 'DONE') {
        return this.allTodos.filter(t => t.done);
      } else if (this.filter === 'UNDONE') {
        return this.allTodos.filter(t => !t.done);
      } else {
        return this.allTodos;
      }
    }
  },
  methods: {
    handleFilterChange(newFilter) {
      this.filter = newFilter;
    },
    addTodo(todo) {
      const newId = this.allTodos[this.allTodos.length - 1].id + 1;
      this.allTodos.push({
        id: newId,
        text: todo,
        done: false
      });
    },
    toggleTodo(id) {
      this.allTodos = this.allTodos.map(t => {
        if (t.id === id) {
          return { ...t, done: !t.done };
        }

        return t;
      });
    }
  },
  components: {
    FilterBar,
    AddNewBar,
    List
  }
};
</script>
