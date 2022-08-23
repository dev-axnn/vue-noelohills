<template>
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
  import { onMounted } from 'vue';
  import $ from 'jquery';

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
      MobileMenuV,
      TopBannerV,
      HeaderV,
      VisualV,
      CategoryV,
      SitemapV,
      FooterV
    },
    setup(){
      onMounted(() => {
        // 스크롤시 header 고정
        let header = $('.header');
        let wrap = $('.wrap');
        let fixY = $('.banner').height();

        $(window).scroll(function () {
          // 스크롤바의 세로상단 px 값
          let temp = $(window).scrollTop();
          // 50 은 banner 의 높이값 px
          if (temp > fixY) {
            header.addClass('header-fix');
            wrap.addClass('wrap-fix');
          } else {
            header.removeClass('header-fix');
            wrap.removeClass('wrap-fix');
          }
        });
      });
      
      const mbMenuData = [
        {
          tagtype: 'span',
          mainmenu: 'SHOP',
          mainlink: '',
          submenuArr: [
            {link: '#', title: 'ALL PRODUCT'},
            {link: '#', title: 'NEWBORN'},
            {link: '#', title: 'BABY'},
            {link: '#', title: 'FAMILY'},
            {link: '#', title: 'BATH GOODS'},
            {link: '#', title: 'PRESENTS'}
          ]
        },
        {
          tagtype: 'span',
          mainmenu: 'ABOUT',
          mainlink: '',
          submenuArr: [
            {link: '#', title: 'BRAND STORY'},
            {link: '#', title: 'WHO WE ARE'},
            {link: '#', title: 'MAKE A WISH'},
            {link: '#', title: 'PRESS'}
          ]
        },
        {
          tagtype: 'span',
          mainmenu: 'TRUST',
          mainlink: '',
          submenuArr: [
            {link: '#', title: 'FOOD GRADE'},
            {link: '#', title: 'PENTACERA™'},
            {link: '#', title: 'BABY SKINCARE'},
            {link: '#', title: 'CERTIFICATION'},
            {link: '#', title: 'INGREDIENT'}
          ]
        },
        {
          tagtype: 'a',
          mainmenu: 'STOKISTS',
          mainlink: 'a.html',
          submenu: []
        },
        {
          tagtype: 'a',
          mainmenu: 'REVIEW',
          mainlink: 'b.html',
          submenu: []
        },
        {
          tagtype: 'span',
          mainmenu: 'BENEFITS',
          mainlink: '',
          submenuArr: [
            {link: '#', title: 'EVENTS'},
            {link: '#', title: 'MEMBERS'}
          ]
        }
        

      ];

      return {
        mbMenuData
      }
    }
  }
</script>

<style>
  @charset "UTF-8";
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

  /* ==== 공통클래스 ==== */
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

  /* ==== 개별클래스 ==== */
  /* LAYOUT */
  .wrap {
    position: relative;
    display: block;
  }

  .wrap-fix {
    padding-top: 80px;
  }
</style>
