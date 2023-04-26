<script setup lang="ts">
import { defineProps } from "vue"
const props = defineProps({
  message: {
    type: Array<string>,
    required: true
  }
})
</script>

<template>
  <p v-for="(msg, index) in props.message" :key="index">{{ msg }}</p>
</template>