<template>
  <div class="container">
    <span v-for="(_, index) in repetitions" :key="index">{{ config.content }}</span>
  </div>
</template>

<script lang="ts">
interface Obj {
  times: number
  content: string
}
export default {
  props: {
    config: {
      type: Object,
      required: true,
      validator(value: Obj) {
        return typeof value.times === "number" && typeof value.content === "string"
      }
    }
  },
  computed: {
    repetitions() {
      return Array.from({ length: this.config.times })
    }
  }
}
</script>