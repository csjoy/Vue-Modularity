<template>
  <div class="container">
    <select>
      <option :selected="selected === o.value" v-for="o in options" :key="o.value">{{ o.label }}</option>
    </select>
  </div>
</template>

<script lang="ts">
interface Obj {
  value: string
  label: string
}
export default {
  props: {
    selected: {
      type: String,
      required: true,
    },
    options: {
      type: Array<Obj>,
      validator(options: Obj[]) {
        return options.every(o => Boolean(o.value && o.label))
      }
    }
  }
}
</script>