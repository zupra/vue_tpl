<template lang="pug">

.Modal-rootOverlay(v-show="show", @click.self='close')
  .Modal-Card(:class='[mod, position]')
    .title(v-if="title") {{ title }}
    .body
      //slot(name="body")
      //Заполните <div slot="body">Контент</div>
      slot
      
    .actions
      slot(name="actions")
        .btn.red(@click='close') close

</template>

<script>

export default {
  name: 'modal',
  props: {
    show: Boolean,
    mod: String,
    title: String,
    position: {
      type: String,
      default: 'Y_center'
    }
  },
  watch: {
    show(isShow) {
      document.body.style.cssText = (isShow) ? "height:100vh;overflow:hidden;" : "";
    }
  },
  methods: {
    close() {
      this.$emit('update:show', false);
      document.body.style = '';
    },
  }
}

</script>

<style lang="stylus">


@import '../assets/settings'

$bg = #f1f1f1;

.Modal
  &-rootOverlay
    z-index 100
    position fixed
    left 0
    top 0
    width 100% //100vw
    height 100vh
    display flex
    cursor pointer
    background rgba(#444 0.7)
    //background rgba(#444 0.7) url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20'><g stroke='white' stroke-width='4' stroke-linecap='round'><line x1='3' y1='3' x2='17' y2='17'/><line x1='3' y1='17' x2='17' y2='3'/></g></svg>") top right no-repeat
    
    overflow hidden
    overflow-y overlay //auto

  &-Card
    //reset rootOverlay
    cursor auto
    background #FFF

.Modal-Card
  .title
    font-size 1.4rem
    line-height 1.3
    padding: .75rem 1.5rem;
    //border-radius .2em 0 0
  .body
    background #f1f1f1
    padding 1rem 1.5rem;
    //fix
    p
      margin-bottom 0
  .actions
    text-align right
    padding: .75rem 1.5rem 1.2rem

  &.XL
    max-width 1080px
    margin auto
  &.SM
    max-width 460px

  &.toCenter
    margin auto
//position
.Y_center
  margin 10% auto auto
  
  border-radius .2em
  width 90%
  max-width 780px
  
  transform scale(.5)
  opacity 0
  animation Y_center .2s .3s cubic-bezier(0.250, 0.460, 0.450, 0.940) forwards	//ease-in
@keyframes Y_center
  to
    transform scale(1)
    opacity 1

.lModal
.rModal
  //overflow overlay
  padding 1em
  max-width 400px
  //FIX
  align-self start
  min-height 100%
  
  animation translateX .2s .3s cubic-bezier(0.250, 0.460, 0.450, 0.940) forwards	//ease-in
  
.rModal
  margin-left auto
  transform translateX(100%)
.lModal
  margin-right auto
  transform: translateX(-100%)
@keyframes translateX
  to
    transform translateX(0)  


</style>
