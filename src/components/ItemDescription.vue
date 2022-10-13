<template>
  <div v-if="description">
    ({{description}})
  </div>

</template>

<script>
export default {
  name: "ItemDescription",

  props: {
    description: {
      type: String,
      default: 'jghjgh'
    }
  }
}
</script>

<style scoped>

</style>