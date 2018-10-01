<template>
  <div>
    <v-btn-toggle @change="$emit('filterChange', $event)">
      <v-btn value="ALL" :disabled="filter === 'ALL'">All</v-btn>
      <v-btn value="UNDONE" :disabled="filter === 'UNDONE'">Undone</v-btn>
      <v-btn value="DONE" :disabled="filter === 'DONE'">Done</v-btn>
    </v-btn-toggle>

    <label>
      <input
        type="radio"
        value="ALL"
        :checked="'ALL' === filter"
        @change="$emit('filterChange', $event.target.value)"
      />
      <span>All</span>
    </label>
    <label>
      <input
        type="radio"
        value="DONE"
        :checked="'DONE' === filter"
        @change="$emit('filterChange', $event.target.value)"
      />
      <span>Done</span>
    </label>
    <label>
      <input
        type="radio"
        value="UNDONE"
        :checked="'UNDONE' === filter"
        @change="$emit('filterChange', $event.target.value)"
      />
      <span>Undone</span>
    </label>
  </div>
</template>

<script>
export default {
  props: {
    filter: {
      type: String,
      validator: (val) => ['ALL', 'DONE', 'UNDONE'].includes(val),
      required: true
    }
  }
};
</script>
