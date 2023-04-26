<script setup lang="ts">
import { defineProps, computed } from "vue"

interface Obj {
  id: string
  content: string
}

const props = defineProps({
  items: {
    type: Array<Obj>,
    required: true
  },
  limit: {
    type: Number
  },
  offset: {
    type: Number
  }
})

const currentWindow = computed(() => {
  return props.items.slice(props.offset, props.limit)
})
</script>

<template>
  <ul>
    <li v-for="el in currentWindow" :key="el.id">{{ el.content }}</li>
  </ul>
</template>