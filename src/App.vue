<template>
  <div class="container w-2/5">
    <items-list />
  </div>
</template>

<script>
//import LiItem from "@/components/LiItem";
import ItemsList from "@/components/ItemsList";

export default {
  name: 'App',
  components: {
    ItemsList
  },

}
</script>

<style>
body{
  background-color: rgb(241 245 249);
  padding: 20px;
}
</style>