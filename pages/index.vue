<template lang="pug">
.Wrap

  fieldset
    legend Button
    .form-line
      button base button
      button(disabled) button disabled
      input(type="reset", value="reset")
      input(type="submit", value="submit")
    .Tag states/mod
    .form-line
      each styl in ['btn lite','btn red','btn green','btn orange','btn']
        div(class=""+styl) .btn Example
    .Tag disabled
    .form-line
      each styl in ['btn lite','btn red','btn green','btn orange','btn']
        div(class=""+styl, disabled) .btn disabled


  fieldset
    legend Checkbox, Radio
    .Tag checkbox
    each _,i in Array(3)
      label
        input(type='checkbox', name='checkbox', value=''+(i+1) )
        | Option #{i+1}

    label
      input(type='checkbox', name='checkbox', value='4', checked)
      | Checked

    .Tag radio
    each _,i in Array(3)
      label
        input(type='radio', name='radio', value=''+(i+1) )
        | Option #{i+1}
    label
      input(type='radio', name='radio', value='4', checked)
      | Checked



  fieldset
    legend Input EL
    .form-line
      select
        each option in ['red','green','orange','lite','circle']
          option #{option}     
      input(value='Read-only value', readonly)
      input(placeholder='*Required')
      input(disabled, placeholder='*disabled')

    .Tag 'color','date','datetime','datetime-local','email','number','range','search','tel','time','url','month','week'
    .form-line
      input(type='color' pattern="#[a-f0-9]{6}" title="hexadecimal color" placeholder="#000000")
      each type in ['color','date','datetime','datetime-local','email','number','range','search','tel','time','url','month','week', 'file','password']
        label=type
          input(type=""+type)

    .Tag c-select
    my-select(:options="options", @option="selectedOption = $event")
    p selectedOption: 
      b {{selectedOption.name}}
    pre {{selectedOption}}


  fieldset
    legend form-group
    .flex-row
      .form-group
        input.Serch(type='text')
        select(multiple)
          each option in ['red','green','orange','lite','circle']
            option #{option}
        select
          each option in ['red','green','orange','lite','circle']
            option #{option}
        textarea
        input(placeholder='*Required')
        input(disabled, placeholder='*disabled')
        .checked-group
          each _,i in Array(3)
            label
              input(type='radio', name='radio', value=''+(i+1) )
              | Option #{i+1}
          label
            input(type='radio', name='radio', value='4', checked)
            | Checked
        input(disabled, placeholder='*disabled')
        button button
        
      .DIV_XZ.col   
        .flex-row.form-line
          input.col(placeholder='Input width 1/2')
          input.col(placeholder='Input width 1/2') 
        .flex-row.form-line
          .col(style="flex-basis: 210px;align-self:center")
            each _,i in Array(3)
              label
                input(type='radio', name='radio', value=''+(i+1) )
                | Option #{i+1}
            label
              input(type='radio', name='radio', value='4', checked)
              | Checked

          input.col(placeholder='Input') 
        .flex-row.form-line
          input.col.w_1-4(placeholder='Input width 1/4')
          input.col.w_1-2(placeholder='Input width 1/2') 
          input.col.w_1-4(placeholder='Input width 1/4') 
        .flex-row.form-line
          input.col.w_3-4(placeholder='Input width 3/4')
          div
            button base button







  
  
  
  
  
  
  
  
  
  fieldset
    legend Autocomplete
    my-autocomplete


  hr.H1
  //Text
  .Tag h1
  h1 Lorem ipsum dolor sit amet quos dolorem recusandae deleniti quasi
  .Tag h2
  h2 Lorem ipsum dolor sit amet quos dolorem recusandae deleniti quasi
  .Tag h3 
  h3 Lorem ipsum dolor sit amet quos dolorem recusandae deleniti quasi
  .Tag h4 
  h4 Lorem ipsum dolor sit amet quos dolorem recusandae deleniti quasi
  .Tag h5
  h5 Lorem ipsum dolor sit amet quos dolorem recusandae deleniti quasi
  .Tag p
  p Lorem ipsum dolor <b>sit amet consectetur</b>, adipisicing elit. Blanditiis explicabo porro, <s>voluptatum laborum</s> cumque molestiae quibusdam accusamus sed, quam sint ducimus libero distinctio? Dolore laborum, quos dolorem recusandae deleniti quasi.
  p Lorem ipsum dolor sit, amet consectetur 
    a(href = '#') adipisicing
    |  elit. Voluptate non ab dicta iure quibusdam deserunt assumenda nulla 
    a(href = '#') pariatur recusandae fugiat possimus 
    | commodi accusamus numquam, aliquam veniam saepe accusantium nostrum? Pariatur?

  .Tag ul.textList
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

  .Tag ol.textList
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
  .form-line
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




</style>

