<template>
  <div>
  <v-header></v-header>
    <div class="tab">
      <div class="tab-item border-1px">
        <a href="#" v-link="{path:'/goods'}">商品</a>
      </div>
      <div class="tab-item">
        <a href="#" v-link="{path:'/ratings'}">评论</a>
      </div>
      <div class="tab-item">
        <a href="#" v-link="{path:'/seller'}">商家</a>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>
<script type="text/ecmascript-6">
import header from './components/header/header.vue';
export default{
  components: {
    data () {
      return {
        seller: {}
      };
    },
    'v-header': header
  }
};
</script>
<style lang="stylus" rel="stylesheet/stylus">
  @import  "./common/stylus/mixinit.styl"
    .tab
      display: flex
      width: 100%
      height: 40px
      line-height: 40px
      border-1px(rgba(7,17,27,0.1))
      .tab-item
        flex: 1
        text-align: center
        & > a
          display:block
          font-size:14px
          color:rgb(55,100,33)
          &.active
            color:rgb(240,20,20)


</style>
