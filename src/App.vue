<template>
  <ModalView/>
  <MobileMenuV v-bind:mbmenu="mbMenuData"/>
  <TopBannerV/>

  <div class="wrap">
    <HeaderV/>
    <VisualV/>
    <CategoryV/>
    <SitemapV/>
    <FooterV/>
  </div>
</template>

<script>
  import { useStore } from 'vuex';

  import ModalView from '@/components/ModalView.vue';
  import MobileMenuV from '@/components/MobileMenuView.vue';
  import TopBannerV from '@/components/TopBannerView.vue';
  import HeaderV from '@/components/HeaderView.vue';
  import VisualV from '@/components/VisualView.vue';
  import CategoryV from '@/components/CategoryView.vue';
  import SitemapV from '@/components/SitemapView.vue';
  import FooterV from '@/components/FooterView.vue';

  export default {
    name: 'App',
    components: {
      ModalView,
      MobileMenuV,
      TopBannerV,
      HeaderV,
      VisualV,
      CategoryV,
      SitemapV,
      FooterV
    },
    setup(){
      const store = useStore();
      store.dispatch('fetchMenu');

      return {

      }
    }
  }
</script>

<style>
  @charset "UTF-8";
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap');
  @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@100;200;300;400;500;600;700;800;900&family=Noto+Sans+KR:wght@100;300;400;500;700;900&display=swap");

  * {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
  }

  a {
    color: #777;
    text-decoration: none;
  }

  ul, li {
    list-style: none;
  }

  img {
    vertical-align: middle;
    border: 0;
  }

  html {
    font-size: 10px;
    overflow-x: hidden;
  }

  body {
    font-family: "Montserrat", "Noto Sans KR", "Malgun Gothic", "Dotum", "AppleGothic", sans-serif;
    font-size: 14px;
    font-weight: 400;
    line-height: 1.5;
    letter-spacing: -0.45px;
    overflow-x: hidden;
  }

  ::-moz-selection {
    background: #1ABC9C;
    color: #fff;
  }

  ::selection {
    background: #1ABC9C;
    color: #fff;
  }

  ::-moz-selection {
    background: #1ABC9C;
    color: #fff;
  }

  ::-webkit-selection {
    background: #1ABC9C;
    color: #fff;
  }

  #app {
    
  }

  /* ==== ??????????????? ==== */
  .clearfix::after {
    content: "";
    position: relative;
    display: block;
    width: 100%;
    clear: both;
  }

  .inner {
    position: relative;
    display: block;
    width: 100%;
    max-width: 1320px;
    margin: 0 auto;
  }

  /* ==== ??????????????? ==== */
  /* LAYOUT */
  .wrap {
    position: relative;
    display: block;
  }

  .wrap-fix {
    padding-top: 80px;
  }
</style>
