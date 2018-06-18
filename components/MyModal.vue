<template lang="pug">

.Modal_Overlay(v-show="show", @click.self='close')
  .Modal_Card(:class='[mod, position]')
    .close(v-if='position', @click='close')

    .title(v-if="title") {{ title }}
    .body
      //slot(name="body")
      //Заполните <div slot="body">Контент</div>
      slot
      
      .actions
        .btn.-red(@click='close') Ок
        //.btn.-lite.-circle Cancel
        //span Cancel
</template>

<script>

export default {
  //name: 'modal',
  props: {
    show: Boolean,
    mod: String,
    title: String,
    position: {
      type: String,
      default: 'Y_center'
    }
  },
  // watch: {
  //   show(isShow) {
  //     document.documentElement.style.cssText = (isShow) ? "height:100vh;overflow:hidden;" : "";
  //   }
  // },
  methods: {
    close() {
      this.$emit('update:show', false)
    },
    // Hide() {
    //   this.vis = false
    // }
  }
  // methods: {
  //   close() {
  //     this.$emit('close');
  //     document
  //       .body
  //       .classList
  //       .remove('no-scroll');
  //   }
  // },
  // destroyed () {
  //   document
  //     .body.classList.remove('no-scroll')
  // }
}

</script>

<style lang="stylus">


@import '../assets/settings'


.Modal_Overlay
  z-index 100
  position fixed
  left 0
  top 0
  width 100% //100vw
  height 100%
  display flex
  cursor pointer
  background rgba(#444 0.7)
  
  overflow hidden
  overflow-y overlay //auto

.Modal_Card
  //reset
  cursor auto
  background #FFF
  
  &.toCenter
    margin auto
  &.XL
    max-width 1080px
    margin auto
  &.SM
    max-width 460px

.Modal_Card
  .title
    font-size 1.4rem
    line-height 1.3
    
    background #FFF
    border-radius 5px 0 0
  .title
  .body
    padding: .75rem 1.5rem;
     
     
//position    
.Y_center
  margin 18% auto auto
  width 90%
  max-width 780px
   
  //border-top .5em solid $blue //#03a9f4
  border-radius 5px
  background #f1f1f1
  
  animation Y_center .2s .3s cubic-bezier(0.250, 0.460, 0.450, 0.940) forwards	//ease-in
  transform scale(.5)
  opacity 0
  .title
    border-radius 5px 0 0
@keyframes Y_center
  to
    transform scale(1)
    opacity 1  
.rModal
  margin-left auto
  //overflow overlay
  padding 1em
  max-width 400px
  //FIX
  align-self start
  min-height 100%
  
  animation rModal .2s .3s cubic-bezier(0.250, 0.460, 0.450, 0.940) forwards	//ease-in
  transform translateX(100%)
  .body
    background #f1f1f1 
@keyframes rModal
  to
    transform translateX(0)  
    
    

//Close
$finger = 44px 
.Y_center
  position relative //for close
  .close
    cursor pointer
    position absolute
    top -($finger/2)
    right -($finger/2)
    width $finger
    height $finger
    border-radius 50%
    background $blue url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='20' height='20' viewBox='0 0 20 20'><g stroke='white' stroke-width='4' stroke-linecap='round'><line x1='3' y1='3' x2='17' y2='17'/><line x1='3' y1='17' x2='17' y2='3'/></g></svg>") center no-repeat
    &:hover
      background-color $blue + 20




</style>
