<template>
  <div class="container">
    <span v-for="(_, i) in repetitions" :key="i">
      {{ content }}
    </span>
  </div>
</template>

<script lang="ts">

export default {
  props: {
    times: {
      type: Number
    },
    content: {
      type: [String, Number]
    }
  },
  computed: {
    repetitions() {
      return Array<number>(this.times ? this.times : 1)
    }
  }
}
</script>