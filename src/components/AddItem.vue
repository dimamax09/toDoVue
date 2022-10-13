<template>
  <div>
    <div>
      <input
          v-on:keydown.enter="addItemToList"
          v-model="item.title"
          type="text"
          class="rounded border-2 border-indigo-500/75 mr-[5px]"
          placeholder="Название"
      />

      <input
          v-on:keydown.enter="addItemToList"
          v-model="item.description"
          type="text"
          placeholder="Описание"
          class="rounded border-2 border-cyan-400/75"
      />

      <button
          class="rounded p-1 mt-[5px] text- ring-2 ring-pink-300 active:bg-sky-700"
          @click="addItemToList">
        Добавить
      </button>
    </div>

  </div>
</template>

<script>
export default {
  name: "AddItem",

  data(){
    return {
      item: {title: '', description: ''}
    }
  },

  methods: {
    addItemToList(){
      if (!this.item.title) {
        return
      }
      this.$emit('add-item', this.item)
      this.item = {title: '', description: ''}
    }
  }
}
</script>

<style scoped>

</style>