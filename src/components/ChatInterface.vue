<template>
  <textarea class="border border-gray-500 bg-gray-100" ref="textArea" v-model="message" cols="50" rows="3"></textarea>
  <button class="bg-gray-400 text-white px-5 py-2.5 rounded" @click="onSendClick()">Send</button>
</template>

<script lang="ts">

export default {
  emits: {
    send: null
  },
  data() {
    return {
      message: ""
    }
  },
  methods: {
    onSendClick() {
      this.$emit("send", this.message);
      this.message = "";
      (this.$refs.textArea as any).focus()
    }
  }
}
</script>