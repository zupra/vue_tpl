<template lang="pug">
section

  fieldset
    legend Button

    button Example
    each styl in ['btn -gray','btn -red','btn -green','btn -blue']
      button(class=""+styl) Example
    button(disabled) disabled

  fieldset
    legend Input
    .form
      select
        each option in ['red','green','orange','lite','circle']
          option #{option}
      input(type='text', value='Read-only value', readonly)
      input(type='text', placeholder='*Required')
      input(type='text', disabled, placeholder='*disabled')
      input.Serch(type='text')
    hr
    h2 c-select
    .form
      my-select(:options="options", @option="selectedOption = $event")
    p selectedOption: 
      b {{selectedOption.name}}
    pre {{selectedOption}}

  fieldset
    legend Checkbox, Radio
    h2 checkbox
    each _,i in Array(3)
      label
        input(type='checkbox', name='checkbox', value=''+(i+1) )
        | Option #{i+1}

    label
      input(type='checkbox', name='checkbox', value='4', checked)
      | Checked

    h2 radio
    each _,i in Array(3)
      label
        input(type='radio', name='radio', value=''+(i+1) )
        | Option #{i+1}
    label
      input(type='radio', name='radio', value='4', checked)
      | Checked





  hr.H1
  //Text
  i.tag h1
  h1 Lorem ipsum dolor sit amet consectetur
  i.tag h2
  h2 Lorem ipsum dolor sit amet consectetur
  i.tag h3 
  h3 Lorem ipsum dolor sit amet consectetur
  i.tag p
  p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
  p Lorem ipsum dolor sit, amet consectetur 
    a(href = '#') adipisicing
    |  elit. Voluptate non ab dicta iure quibusdam deserunt assumenda nulla 
    a(href = '#') pariatur recusandae fugiat possimus 
    | commodi accusamus numquam, aliquam veniam saepe accusantium nostrum? Pariatur?

  i.tag ul.textList
  ul.textList
    each item in [1,2,3]
      li Lorem ipsum dolor sit amet consectetur
    li Nested lists styled
      ol
        li Lorem ipsum dolor sit amet consectetur
        li Lorem ipsum dolor sit amet consectetur
        li Lorem ipsum dolor sit amet consectetur
    li Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
  i.tag ol.textList
  ol.textList
    li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur
    li Nested lists styled
      ol
        li Lorem ipsum dolor sit amet consectetur
        li Lorem ipsum dolor sit amet consectetur
        li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur
    li Nested lists styled
      ol
        li Lorem ipsum dolor sit amet consectetur
        li Lorem ipsum dolor sit amet consectetur
        li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur

  hr.H1




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

$border-input =  #CCC //#607d8b

section
  padding: 1em
  margin auto
  max-width 1200px

a
  color: $link



button, input, select, textarea
  outline: 0
  box-shadow: none
  font: inherit
select, input, button, .btn
  //!TODO
  line-height: 2.4
  height 2.4em
  padding: 0 1em


button
  border: 0
  cursor: pointer
  background-color whitesmoke
button, .btn
  //border: 1px solid rgba(#BBB, .5)
  //letter-spacing: 1px
  box-shadow: 0 2px 5px 0 rgba(0, 0, 0, .16), 0 2px 10px 0 rgba(0, 0, 0, .12)
  border-radius: .3em
  & + &
    margin-left: 1em
.btn
  display: inline-block
  text-decoration: none
  color: #FFF
  white-space: nowrap
  &.-gray
    color: $link
    background: snow //#f7f7f7
  &.-red
    background: $red
  &.-green
    background: $green
  &.-blue
    background: $blue



//TST
.form
  display flex
  flex-direction column
  *
    width 240px


select, input
  border: 1px solid $border-input
  margin-bottom 1em
select
  border-radius .3em
  //height 2.4em //(line-height)FF
  cursor: pointer
  appearance: none
  background #fff url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='22' height='12'><polygon points='0,0 12,0 6,12' fill='orange'/></svg>") 100% no-repeat;


.Serch
  padding-left 2.4em  
  background url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='13' height='13'><g stroke-width='2' stroke='blueviolet'><circle cx='5' cy='5'  r='4' style='fill:none;' /><line x1='9' y1='9' x2='13' y2='13' /></g></svg>") 1em 50% no-repeat



</style>

