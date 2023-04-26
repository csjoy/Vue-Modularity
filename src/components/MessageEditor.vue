<script setup lang="ts">
import { defineEmits, ref } from 'vue';

const message = ref("")
const emits = defineEmits(["send"])

function send() {
  emits("send", message.value)
}
</script>

<template>
  <input type="text" v-model="message" class="p-2 border border-gray-500 bg-gray-100 rounded">
  <button class="m-2 px-5 py-2.5 rounded bg-gray-400 text-white" @click="send()">Send to Parent via method</button>
  <button class="m-2 px-5 py-2.5 rounded bg-gray-400 text-white" @click="$emit('send', message)">Send to Parent via inline emit</button>
</template>