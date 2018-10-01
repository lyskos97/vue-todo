<template>
  <v-card>
    <v-list>
      <ListItem
        v-for="todo in todos"
        :key="todo.id"
        :active="todo.done"
        @click="$emit('todoToggle', todo.id)"
      >
        {{ todo.text }}
      </ListItem>
    </v-list>
  </v-card>
</template>

<script>
import ListItem from './ListItem';

export default {
  props: {
    todos: {
      type: Array,
      required: true
    }
  },
  components: {
    ListItem
  }
};
</script>
