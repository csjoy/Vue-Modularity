<template>
  <div>
    <textarea class="border border-gray-500 bg-gray-100" ref="textArea" cols="50" rows="7"></textarea>
    <ul v-if="count">
      <li>Paragraphs: {{ count.paragraphs }}</li>
      <li>Sentences: {{ count.sentences }}</li>
      <li>Words: {{ count.words }}</li>
    </ul>
  </div>
</template>

<script lang="ts">
interface Obj {
  paragraphs: number
  sentences: number
  words: number
}
let val: Obj
import * as Countable from "countable"
export default {
  data() {
    return {
      count: val
    }
  },
  mounted() {
    Countable.on(this.$refs.textArea, (count: Obj) => {
      this.count = count
    })
  },
  beforeUnmount() {
    Countable.off(this.$refs.textArea)
  }
}
</script>