<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot='center'>购物街</div></nav-bar>
    <swiper>
      <swiper-item v-for="(item,index)  in banners" :key="index">
        <a :href="item.link">
          <img :src="item.imges" alt=""> 
        </a>
      </swiper-item>
    </swiper> 
  </div>
</template>

<script> 
  import NavBar from '../../components/common/navbar/NavBar.vue'
  import {getHomeMultidata} from '../../network/home'
  import {Swiper,SwiperItem} from '../../components/common/swiper'

  export default {
    name: "Home",
    components:{ 
        NavBar,
        Swiper,
        SwiperItem,
        
    },
    data() {
      return {
        banners:[],
        recommends:[]
      }
    },
    created() {
      getHomeMultidata().then(res=>{
        this.banners=res.data.banner.list;
        this.recommends=res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
  .home-nav{
    background-color: var(--color-tint);
    color:#fff;
  }
</style>
