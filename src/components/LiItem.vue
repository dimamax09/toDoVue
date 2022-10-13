<template>
  <div class="inline-flex align-middle mt-[7px] w-full border-b-2 pb-[10px] pt-[4px]">

    <li class="self-center w-4/5 list-none">
      <input
          @focus="itemTextInput = true"
          @focusout="changeText"
          @keyup.enter="enterInput"
          :class="itemTextInput ? 'shadow-lg rounded p-[4px] focus:outline-none focus:border-2 focus:border-indigo-500/75' : ''"
          :value="item.title"
          class="w-full"
      />

      <slot style="display: inline-flex" name="description"></slot>

    </li>
    <div class="w-1/5 flex flex-row-reverse">

      <svg
          class="self-center cursor-pointer ml-[10px]"
          @click="deleteItem"
          fill="#000000"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 24 24"
          width="18px"
          height="18px">

        <path d="M 4.7070312 3.2929688 L 3.2929688 4.7070312 L 10.585938 12 L 3.2929688 19.292969 L 4.7070312 20.707031 L 12 13.414062 L 19.292969 20.707031 L 20.707031 19.292969 L 13.414062 12 L 20.707031 4.7070312 L 19.292969 3.2929688 L 12 10.585938 L 4.7070312 3.2929688 z"/>
      </svg>

      <svg
          class="self-center cursor-pointer ml-[5px] opacity-75"
          xmlns="http://www.w3.org/2000/svg"
          viewBox="0 0 48 48"
          width="22px"
          height="22px"
      >
        <path fill="#22d3ee" d="M39.707,14.293l-10-10C29.52,4.105,29.266,4,29,4H13c-2.757,0-5,2.243-5,5v30c0,2.757,2.243,5,5,5h22	c2.757,0,5-2.243,5-5V15C40,14.735,39.895,14.48,39.707,14.293z"/><path fill="#324561" d="M40,16h-7c-2.757,0-5-2.243-5-5V4c0-0.552,0.447-1,1-1s1,0.448,1,1v7c0,1.654,1.346,3,3,3h7	c0.553,0,1,0.448,1,1S40.553,16,40,16z"/><path fill="#324561" d="M32,25H16c-0.553,0-1-0.448-1-1s0.447-1,1-1h16c0.553,0,1,0.448,1,1S32.553,25,32,25z"/><path fill="#324561" d="M32,30H16c-0.553,0-1-0.448-1-1s0.447-1,1-1h16c0.553,0,1,0.448,1,1S32.553,30,32,30z"/><path fill="#324561" d="M26,35H16c-0.553,0-1-0.448-1-1s0.447-1,1-1h10c0.553,0,1,0.448,1,1S26.553,35,26,35z"/>
      </svg>
    </div>

  </div>


</template>

<script>
export default {
  name: "li-item",

  data(){
    return {
      itemTextInput: false
    }
  },

  props: {
    itemId: {
      type: Number,
    },

    item: {
      type: Object,
      required: true
    },

  },

  emits: ['deleteItem', 'itemChange'],

  methods: {
    deleteItem() {
      this.$emit('deleteItem', this.itemId)
    },

    enterInput(e){
      e.target.blur()
    },

    changeText(e){
      if (e.target.value){
        this.$emit('itemChange', this.itemId, e.target.value)
      }
      this.itemTextInput = false
    }
  }
}
</script>

<style scoped>

</style>