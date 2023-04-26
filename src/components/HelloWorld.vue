<template>
  <div class="container">
    <h1 class="text-4xl font-semibold">Hello {{ msg }}</h1>
  </div>
</template>

<script lang="ts">
export default {
  name: "HelloWorld",
  props: ["msg"]
}
</script>