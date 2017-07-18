<template>
  <div>
    <v-header></v-header>
    <ul class="tab">
      <li class="tab-item">
        <router-link to="/goods">商品</router-link>
      </li>
      <li class="tab-item">
        <router-link to="/ratings">评价</router-link>
      </li>
      <li class="tab-item">
        <router-link to="/seller">商家</router-link>
      </li>
    </ul>
    <router-view></router-view>
  </div>
</template>

<script>
import header from './components/header/header'

export default {
  name: 'app',
  components: {
    'v-header': header
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
    .tab
      width: 100%
      display: flex
      height: 40px
      line-height: 40px
      .tab-item
        flex: 1
        text-align: center
        & > a
          display: block
          font-size: 14px
          color: rgb(77,85,93)
          &.active
            color: rgb(240,20,20)
</style>
