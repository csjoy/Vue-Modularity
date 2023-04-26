<template>
  <div>{{ greeting }} {{ who }}</div>
</template>

<script lang="ts">
export default {
  props: ["greeting", "who"]
}
</script>