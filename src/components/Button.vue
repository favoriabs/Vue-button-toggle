<template>
  <div>
    <!-- <button  v-on:click="changeText()">{{text}}</button> -->
    <button v-bind:style="{'background-color': inactiveColor}" v-on:click="toggleOn()">On</button>
    <button v-bind:style="{'background-color': activeColor}" v-on:click="toggleOff()">Off</button>
    <hr/>
    <transition name="slide-fade">
      <img v-show="onShowImage" src="../assets/bulb.png" width="150px" height="200px">
    </transition>
    <transition name="slide-fade">
      <img v-show="offShowImage" src="../assets/offbulb.png" width="200px" height="200px">
    </transition>

  </div>
</template>


<script>
export default {
  name: 'button',
  data () {
    return {
      text: 'On',
      activeColor: 'teal',
      inactiveColor: '',
      offShowImage: true,
      onShowImage: false
    }
  },
  methods: {
    changeText () {
      if (this.text === 'on') {
        this.text = 'off'
      } else {
        this.text = 'on'
      }
    },
    toggleOn () {
      if (this.inactiveColor === '') {
        this.inactiveColor = 'teal'
        this.activeColor = ''
      } else {
        this.inactiveColor = 'teal'
        this.activeColor = ''
      }
      this.onShowImage = true
      this.offShowImage = false
    },
    toggleOff () {
      if (this.activeColor === 'teal') {
        this.inactiveColor = ''
        this.activeColor = 'teal'
      } else {
        this.inactiveColor = ''
        this.activeColor = 'teal'
      }
      this.offShowImage = true
      this.onShowImage = false
    }
  }
}
</script>

<style scoped>
.offButton{
  background-color: teal;
}
.fade-enter-active, .fade-leave-active {
   transition: all .3s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0
}
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for <2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
/*.onButton{
  background-color: green;
}*/
</style>
