<template>

<div class="custom-select">

  <input 
    class="select"
    placeholder="Please select an item"
    @click="open=!open"
    :value="selectedOption && selectedOption.name"
  >

  <ul v-show="open">
    <li
      v-for="(option,i) in options"
      :key="i"
      @click="updateOption(option,i)"
      :class="{selected:i==selectedItem}">
        {{ option.name }}
      </li>
  </ul>
</div>

</template>


<script>
export default {
  props: {
    options: {
      type: [Array, Object]
    },
    selected: {},
  },
  data() {
    return {
      selectedOption: {},
      open: false,
      selectedItem: null
    }
  },
   mounted() {
     this.selectedOption = this.selected;
   },
   methods: {
     updateOption(option,i) {
       this.selectedItem = i;
       this.selectedOption = option;
       this.open = false;
       this.$emit('option', option);
     }
   }
}
</script>




<style lang="stylus">

//@import 'custom-select'

</style>
