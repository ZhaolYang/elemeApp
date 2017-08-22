<template>
  <div>
    <v-header :seller="seller"></v-header>
    <ul class="tab border-1px">
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
    <keep-alive><router-view :seller="seller"></router-view></keep-alive>
    
  </div>
</template>

<script>
import {urlParse} from 'common/js/util'
import header from './components/header/header'

const ERR_OK = 0;

export default {
  name: 'app',
  data() {
    return {
      seller: {
        id: (()=>{
          let queryParam = urlParse()
          console.log(queryParam)
          return queryParam.id
        })()
      }
    }
  },
  components: {
    'v-header': header
  },
  created(){
    this.$http.get('/api/seller?id='+this.seller.id).then((response) => {
      response = response.body;
      if(response.errno === ERR_OK){
        this.seller = Object.assign({}, this.seller, response.data)
      }
    });
  }
}
</script>

<style lang="stylus" rel="stylesheet/stylus">
    @import "./common/stylus/mixin.styl"

    .tab
      width: 100%
      display: flex
      height: 40px
      line-height: 40px
      border-1px(rgba(7,17,27,0.1))
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
