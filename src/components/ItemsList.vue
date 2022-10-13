<template>
  <div class="shadow-lg rounded p-[15px] bg-white">
    <add-item @add-item="addItem"/>
    <div class="font-bold text-lg mt-[15px]">
      {{ itemsList.name }}:
    </div>

    <li-item
        v-for="(item, idx) in itemsList.items"
        :key="idx"
        :itemId="idx"
        :item="item"
        @delete-item="deleteItem"
        @item-change="changeItem"
    >
      <template v-slot:description>
        <item-description :description="item.description"></item-description>
      </template>
    </li-item>
  </div>
</template>

<script>
import AddItem from "@/components/AddItem";
import LiItem from "@/components/LiItem";
import ItemDescription from "@/components/ItemDescription";

export default {
  name: "ItemsList",

  components: {
    LiItem,
    AddItem,
    ItemDescription
  },

  data() {
    return {
      itemsList: {
        name: 'Список',
        items: []
      }
    }
  },

  created() {
    let itemsList = localStorage.getItem("my-todo-list")
    if (itemsList) {
      this.itemsList = JSON.parse(itemsList)
    }
  },

  methods: {
    addItem(itemData) {
      this.itemsList.items.push({title: itemData.title, description: itemData.description})
      localStorage.setItem("my-todo-list", JSON.stringify(this.itemsList))
    },

    changeItem(itemId, value) {
      this.itemsList.items[itemId]['title'] = value
      localStorage.setItem("my-todo-list", JSON.stringify(this.itemsList))
    },

    deleteItem(itemId) {
      this.itemsList.items = this.itemsList.items.filter((item, index) => index != itemId)
      localStorage.setItem("my-todo-list", JSON.stringify(this.itemsList))
    }
  }
}
</script>

<style scoped>

</style>