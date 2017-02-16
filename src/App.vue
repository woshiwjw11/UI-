<template>
  <div>
  <v-header :seller="seller"></v-header>
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
    <router-view :seller="seller"></router-view>
  </div>
</template>
<script type="text/ecmascript-6">
import header from './components/header/header.vue';
export default{
   data() {
      return {
        seller: {

        }
      };
    },
    created() {
      this.$http.get('/api/seller').then((response) => {
        console.log(response.body);
        response=response.body;
        if (response.errno === 0) {
          this.seller=response.data;
          console.log(this.seller);
        }
      });
      // 通过resource 来进行http请求，首先因为这是自己mock的数据，所以不会请求失败，所以在.then中只写了一个方法，就是当成功的时候，将data赋值给seller
      // 这里只用get方法 剩下的还有post方法等，需要在另外的实践中使用到
    },
  components: {
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
