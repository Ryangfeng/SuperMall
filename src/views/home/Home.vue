<template>
  <div id="home">
    <NavBar class="home-navbar">
      <div slot="center">购物街</div>
    </NavBar>
  </div>
</template>


<script>
  import NavBar from 'components/common/navbar/NabBar'
  import {getHomeMultidata} from "network/home";

  export default {
    name: "Home",
    data() {
      return {
       banners:[],
        recommends:[]
      }
    },
    components: {
      NavBar
    },
    create() {
      //1.请求多个数据e
      getHomeMultidata().then(res => {
        this.banners=res.data.banner.list;
        this.recommends=res.data.recommend.list;
      },err=>{
        console.log(err);
      })
    }
  }
</script>


<style scoped>
  .home-navbar {
    background-color: var(--color-tint);
    color: white;
  }
</style>
