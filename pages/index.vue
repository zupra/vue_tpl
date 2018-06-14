<template lang="pug">
section

  h2 Link
  p Lorem ipsum dolor sit, amet consectetur 
    a(href = '#') adipisicing
    |  elit. Voluptate non ab dicta iure quibusdam deserunt assumenda nulla 
    a(href = '#') pariatur recusandae fugiat possimus 
    | commodi accusamus numquam, aliquam veniam saepe accusantium nostrum? Pariatur?

  h2 Button
  button Example
  each styl in ['btn -gray','btn -red','btn -green','btn -blue']
    button(class=""+styl) Example
  button(disabled) disabled

  h2 Form Styling


  


  form
    .form__item
      select
        each option in ['red','green','orange','lite','circle']
          option #{option}
    .form__item
      input(type='text', value='Read-only value', readonly)
    .form__item
      input(type='text', placeholder='*Required')
    .form__item
      input(type='text', disabled, placeholder='*disabled')
    .form__item
      input.Serch(type='text')



  my-select(:options="options", @option="OnSelect")
  h3 selectedOption: {{selectedOption.name}}
  pre {{selectedOption}}

</template>

<script>
import mySelect from "~/components/MySelect.vue";

export default {
  components: {
    mySelect
  },
  data() {
    return {
      selectedOption: {},
      options: [
        {
          name: 'First Option',
          val: 1
        },
        {
          name: 'Second Option',
          val: 2
        },
        {
          name: 'Third Option',
          val: 3
        },
        {
          name: 'Lorem ipsum',
          val: 4
        }
      ]
    }
  }
};
</script>

<style lang="stylus">
$red = #ed5565 // #f05f5c
$green = #26a69a
$blue = #4285f4
$link = #477dca

section, h2
  padding: 1em

a
  color: $link

button, input, select, textarea
  outline: 0
  box-shadow: none
  font: inherit



select, input, button, .btn
  line-height: 2.4
  padding: 0 1em // .7em 1em


button
  border: 0
  cursor: pointer

button, .btn
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, .16), 0 2px 10px 0 rgba(0, 0, 0, .12)
  & + &
    margin-left: 1em

.btn
  display: inline-block
  text-decoration: none
  color: #FFF
  border-radius: 6px
  letter-spacing: 1px
  white-space: nowrap
  &.-gray
    color: $link
    background: #f7f7f7
  &.-red
    background: $red
  &.-green
    background: $green
  &.-blue
    background: $blue

//TST
form
  display flex
  flex-direction column

select, input
  border: 1px solid #CCC
  margin-bottom 1em
  min-width 300px

select
  border-radius 0 //mac
  height 2.4em //(line-height)FF
  cursor: pointer
  appearance: none
  background #fff url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='22' height='12'><polygon points='0,0 12,0 6,12' fill='orange'/></svg>") 100% no-repeat;


.Serch
  padding-left 2.4em  
  background url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='13' height='13'><g stroke-width='2' stroke='blueviolet'><circle cx='5' cy='5'  r='4' style='fill:none;' /><line x1='9' y1='9' x2='13' y2='13' /></g></svg>") 1em 50% no-repeat



</style>

