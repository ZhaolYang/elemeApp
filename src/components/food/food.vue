<template>
  <transition name="move">
    <div v-show="showFlag" id="food">
    </div>
  </transition>
</template>

<script>
export default {
  name: 'food',
  data() {
    return {
      showFlag: false
    }
  },
  props: {
    food: {
      type: Object
    }
  },
  methods: {
    show() {
      this.showFlag = true
    }
  }

}
</script>

<style lang="stylus">
  #food
    position: fixed
    left: 0
    top: 0
    bottom: 48px
    z-index: 30
    width: 100%
    background: #fff
    &.move-enter-active, &.move-leave-active
      transition: all .2s linear
		  transform: translate3d(0, 0, 0)
    &.move-enter, &.move-leave-to
      transform: translate3d(100%, 0, 0)
</style>
