<template>
  <ul>
    <li v-for="el in currentWindow" :key="el.id">
      <slot :item="el" />
    </li>
  </ul>
</template>

<script lang="ts">
interface Obj {
  id: string
  content: string
}
export default {
  props: {
    items: {
      type: Array<Obj>,
      default() {
        return []
      }
    },
    limit: {
      type: Number,
      default: 2
    },
    offset: {
      type: Number,
      default: 0
    }
  },
  computed: {
    currentWindow() {
      return this.items.slice(this.offset, this.limit)
    }
  }
}
</script>

