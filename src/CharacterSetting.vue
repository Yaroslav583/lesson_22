<template>
  <li class="list-group-item">
    <div class="d-inline-block me-3">{{ character.title }}</div>
    <div class="btn-group btn-group-sm" role="group" aria-label="Basic example">
      <button type="button" class="btn btn-outline-primary" @click="decrement" :disabled="character.count === 0">-</button>
      <button type="button" class="btn btn-primary" :disabled="true">{{ character.count }}</button>
      <button type="button" class="btn btn-outline-primary" @click="increment" :disabled="totalPoints === 0">+</button>
    </div>
  </li>
</template>

<script>
export default {
  props: {
    character: {
      type: Object,
      required: true,
    },
    totalPoints: {
      type: Number,
      required: true,
    },
  },
  methods: {
    increment() {
      if (this.totalPoints > 0) {
        this.$emit('increment', this.character);
      }
    },
    decrement() {
      if (this.character.count > 0) {
        this.$emit('decrement', this.character);
      }
    },
  },
}
</script>