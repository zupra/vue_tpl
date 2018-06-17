<template>

<div class="V-dropdown">
  <div 
    v-if="!selectedOption" 
    class="dropdown-toggle" 
    @click="open=!open">
      Please select an item
    </div>
  <div 
    v-else class="dropdown-toggle" 
    @click="open=!open">
      {{ selectedOption.name }}
    </div>
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


.V-dropdown
  user-select none  
  cursor pointer
  position relative
  ul
    position absolute
    background #FFF
    width 100%

    box-shadow 0 .2em 1.4em 0 rgba(0, 0, 0, 0.2)
  .dropdown-toggle, li
    padding 0 1em
    // H as input
    line-height: 2.4
    height 2.4em

    cursor pointer
  .dropdown-toggle
    border-radius .3em
    padding-right 2em
    border 1px solid #CCC
    background url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='22' height='12'><polygon points='0,0 12,0 6,12' fill='orange'/></svg>") right no-repeat
  li
    list-style none
    color #477dca
    border-top 1px solid #EFEFEF
    white-space nowrap
    &.selected
      color #000
    &:hover
      background #f9f9f9


</style>
