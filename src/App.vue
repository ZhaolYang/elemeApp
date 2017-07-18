<template>
  <div id="app">
    <v-header></v-header>
    <ul class="tab">
      <li class="tab-item">商品</li>
      <li class="tab-item">评论</li>
      <li class="tab-item">商家</li>
    </ul>
    <div class="content">content</div>
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
  #app
    .tab
      width: 100%
      display: flex
      height: 40px
      line-height: 40px
      .tab-item
        flex: 1
        text-align: center
</style>
