<template>
  <header class="header">
    <span class="header-btn header-btn-left" v-if="hasLocation"  >
      <van-icon name="location-o" />
      <p class="name">深圳市</p>
    </span>

    <span class="header-btn header-btn-left" v-else @click="backAction" >
      <van-icon name="arrow-left" />
    </span>

    <div class="header-center search-box" v-if="hasLocation">
      <van-icon name="search" />
      <input type="text" class="search" @click.prevent="goSearch" placeholder="请输入要搜索的内容" />
    </div>

   <div class="header-title text-overflow" v-else>
      <h1 class="text-overflow">{{title}}</h1>
   </div>

    <span class="header-btn header-btn-right" @click="cartAction"  >
      <van-icon name="shopping-cart-o" />
    </span>
  </header>
</template>

<script>
export default {
  props:{
    hasLocation:{
      type:Boolean,
      default:true
    },
    title:{
      type:String,
      // required:true
    }
  },
  methods:{
    backAction(){
      this.$router.back();
    },
    goSearch(){
      this.$router.push('/market/search');
    },
    cartAction(){
      this.$router.push('/market/cart');
    }
  }
};
</script>
<style lang='scss' scoped>
.header {
  display: flex;
  height: 44px;
  align-content: center;
  justify-content: space-around;
  background: #fff;
  align-items: center;
  box-sizing: border-box;
  width: 100%;
  padding: 0 20px;

  .header-btn {
    display: flex;
    align-items: center;
    flex-direction: column;
    .van-icon-location-o{
      color: #505044;   
      font-size: 14px;      
    }
    .van-icon-shopping-cart-o{
      color: #3b3b3b;
      font-size: 20px;    
    }
    .name {
      font-size: 14px;
      color: #505044;
      padding-top: 5px;
    }
  }
  .header-btn-left{
    padding: 0 15px 0 0;
  }
  .header-btn-right{  
    padding: 0 0 0 15px;
  }
  .header-center {
    flex: 1;
    background: #f2f2f0;
    line-height: 38px;
    border-radius: 4px;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    .van-icon {
      padding: 0 8px;
      color: #94958f;
      font-weight: bold;
    }
    .search {
      border: none;
      background: none;
      flex: 1;
      width: 100%;
      font-size: 15px;
    }
  }
  .header-title{
    flex: 1;
    text-align: center;
  }
}
</style>