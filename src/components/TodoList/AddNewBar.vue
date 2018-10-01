<template>
  <div>
    <form @submit.prevent="handleSubmit">
      <v-text-field label="New Todo" solo v-model="todo" />
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todo: ''
    };
  },
  methods: {
    handleSubmit() {
      if (this.todo) {
        this.$emit('newTodo', this.todo);
        this.todo = '';
      }
    }
  }
};
</script>
