<template>
  <div id="home">
    <nav-bar class="home-nav"><div slot="center">购物街</div></nav-bar>
    <home-swiper :banners="banners"></home-swiper>
    <recommend-view :recommends="recommends"/>
    <feature-view/>
    <tab-control :titles="['流行', '新款', '精选']" class="tab-control"/>

    <ul>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
      <li>....</li>
    </ul>
  </div>
</template>

<script>
  //子组件
  import HomeSwiper from "./childrenComps/HomeSwiper";
  import RecommendView from "./childrenComps/RecommendView";
  import FeatureView from "./childrenComps/FeatureView";

  //公共组件
  import NavBar from "components/common/navbar/NavBar";
  import TabControl from "components/content/tabControl/TabControl";

  import {getHomeMultiDate} from "network/home";

  export default {
    name: "Home",
    components: {
      HomeSwiper,
      RecommendView,
      FeatureView,

      NavBar,
      TabControl
    },
    data() {
      return {
        banners: [],
        recommends: []
      }
    },
    created() {
      //1.请求多个数据
      getHomeMultiDate().then( res => {
          this.banners = res.data.banner.list;
          this.recommends = res.data.recommend.list;
      })
    }
  }
</script>

<style scoped>
  #home {
    padding-top: 44px;
  }

  .home-nav {
    background-color: var(--color-tint);
    color: #fff;

    position: fixed;
    left: 0;
    right: 0;
    top: 0;
    z-index: 9;
  }

  .tab-control {
    position: sticky;
    top: 44px;
  }
</style>
