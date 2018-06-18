<template lang="pug">
.Wrap

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


  fieldset
    legend Autocomplete
    my-autocomplete


  hr.H1
  //Text
  i.tag h1
  h1 Lorem ipsum dolor sit amet consectetur
  i.tag h2
  h2 Lorem ipsum dolor sit amet consectetur
  i.tag h3 
  h3 Lorem ipsum dolor sit amet consectetur
  i.tag p
  p Lorem ipsum dolor <b>sit amet consectetur</b>, adipisicing elit. Blanditiis explicabo porro, <s>voluptatum laborum</s> cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
  p Lorem ipsum dolor sit, amet consectetur 
    a(href = '#') adipisicing
    |  elit. Voluptate non ab dicta iure quibusdam deserunt assumenda nulla 
    a(href = '#') pariatur recusandae fugiat possimus 
    | commodi accusamus numquam, aliquam veniam saepe accusantium nostrum? Pariatur?

  i.tag ul.textList
  ul.textList
    each item in [1,2,3]
      li Lorem ipsum dolor sit amet consectetur
    
    li Nested <b>[OL]</b> ordered list styled
      ol
        li Lorem ipsum dolor sit amet consectetur
        li Nested <b>[OL]</b> ordered list styled
          ol
            each _,i in Array(3)
              li Lorem ipsum dolor sit amet consectetur
                ol
                  each _,i in Array(3)
                    li Lorem ipsum dolor sit amet consectetur

        li Nested <b>[OL]</b> ordered list styled
          ol
            each _,i in Array(3)
              li Lorem ipsum dolor sit amet consectetur

    li Nested <b>[UL]</b> unordered list styled
      ul
        each _,i in Array(3)
          li Quam sint ducimus libero distinctio
    li Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.

  i.tag ol.textList
  ol.textList
    li Lorem ipsum dolor sit amet consectetur
    li Nested <b>[OL]</b> ordered list styled
      ol
        each _,i in Array(3)
          li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur
    li Nested <b>[UL]</b> unordered list styled
      ul
        each _,i in Array(3)
          li Lorem ipsum dolor sit amet consectetur
    li Nested <b>[OL]</b> ordered list styled
      ol
        each _,i in Array(3)
          li Lorem ipsum dolor sit amet consectetur
    li Lorem ipsum dolor sit amet consectetur



  hr.H1
  h1 Модалки <b>!!!TODO</b>
  each item,i in ['Modal', 'Modal(toCenter)', 'Small Modal', 'Small(toCenter)', 'Large Modal', 'Right Modal']
    button.btn.-blue(@click="showModal_"+(i+1)+" = true") #{item}

  my-modal(:show.sync="showModal_1", title="Base Modal")
    p Lorem ipsum dolor sit amet consectetur, adipisicing elit. Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.

  my-modal(:show.sync="showModal_2", mod="toCenter", title="Lorem ipsum dolor sit amet")
    p Blanditiis explicabo porro, voluptatum laborum cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
    
    
  my-modal(:show.sync="showModal_3", mod="SM")
    p Заголовок не был назначен, поэтому только тело
    h3 Lorem ipsum dolor sit, amet consectetur adipisicing elit. 
    p Quod dignissimos voluptate iure eius cupiditate rem sed consequuntur itaque odio!

  my-modal(:show.sync="showModal_4", mod="SM toCenter", title="Small modal toCenter")
    p Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quod dignissimos voluptate iure eius cupiditate rem sed consequuntur itaque odio. Assumenda dignissimos veritatis placeat nesciunt maiores vel fuga est odio magnam!

  my-modal(:show.sync="showModal_5", mod="XL", title='Окно для  «Широкого» контента')
    iframe(height='480', scrolling='no', title='Flexbox Overview', src='//codepen.io/dimaZubkov/embed/BZLqGv/?height=480&theme-id=0&default-tab=result&embed-version=2', frameborder='no', allowtransparency='true', allowfullscreen='true', style='width: 100%;')

  my-modal(:show.sync="showModal_6", position="rModal", title="Lorem ipsum dolor")
    h2 Lorem ipsum dolor sit amet consectetur adipisicing elit.
    p Lorem ipsum dolor sit, amet consectetur adipisicing elit. Quod dignissimos voluptate iure eius cupiditate rem sed consequuntur itaque odio. Assumenda dignissimos veritatis placeat nesciunt maiores vel fuga est odio magnam!
    h4 Magnam atque, accusamus deleniti, inventore pariatur voluptates eos officiis quasi officia magni reprehenderit ipsa nam ducimus, temporibus autem sunt odio quae iste.


  hr.H1






</template>

<script>
import mySelect from "~/components/MySelect";
import myModal from "~/components/MyModal";

import MyAutocomplete from "../components/MyAutocomplete";

export default {
  components: {
    mySelect,
    myModal,
    MyAutocomplete
  },
  data() {
    return {
      selectedOption: {},
      options: [
        {
          name: "First Option",
          val: 1
        },
        {
          name: "Second Option",
          val: 2
        },
        {
          name: "Third Option",
          val: 3
        },
        {
          name: "Lorem ipsum",
          val: 4
        }
      ],

      showModal_1: false,
      showModal_2: false,
      showModal_3: false,
      showModal_4: false,
      showModal_5: false,
      showModal_6: false
    };
  }
};
</script>

<style lang="stylus">
@import '../assets/settings';

.Wrap {
  padding: 1em;
  margin: auto;
  max-width: 1200px;
}
</style>

