<template>
  <!-- HEADER -->
  <header class="header">
    <div class="inner">
      <button class="mb-bt"></button>
      <a href="#" class="logo"></a>
      <div class="gnb">
        <ul class="menu clearfix">
          <li v-for="(item, index) in menuData" :key="index">
            <a :href="item.mainlink">{{item.mainmenu}}</a>
            <ul class="submenu" v-if="item.tagtype == 'span'">
              <li v-for="(subitem, subindex) in item.submenuArr" :key="subindex">
              <a :href="subitem.link">{{subitem.title}}</a></li>
            </ul>
          </li>
        </ul>
      </div>
      <div class="member">
        <ul class="member-list clearfix">
          <li><a href="#" class="member-cart"><i class="tooltip">장바구니</i></a></li>
          <li><a href="#" class="member-mypage"><i class="tooltip">마이페이지</i></a></li>
          <li><a href="#" class="member-login"><i class="tooltip">로그인</i></a></li>
        </ul>
      </div>
    </div>
  </header>
</template>

<script>
  import { computed, onUpdated } from 'vue';
  import { useStore } from 'vuex';
  import $ from 'jquery';

  export default {
    setup(){
      const store = useStore();
      const menuData = computed(() => store.getters.getMbMenuData);

      onUpdated(() => {
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

      return{
        menuData
      }
    }
  }
</script>

<style>
  /* HEADER */
  .header {
    position: relative;
    display: block;
    height: 80px;
    background: #fff;
    border-bottom: 1px solid #dcdcdc;
    z-index: 9999;
  }
  .header .inner {
    display: flex;
    height: 100%;
  }
  .header .inner .logo {
    position: relative;
    display: block;
    width: 111px;
    height: 42px;
    background: url("@/assets/images/logo_new.png") no-repeat center;
    background-size: contain;
    margin-top: 20px;
    margin-right: 65px;
  }
  .header .inner .gnb {
    position: relative;
    display: block;
  }
  .header .inner .gnb .menu {
    position: relative;
    display: block;
  }
  .header .inner .gnb .menu > li {
    position: relative;
    display: block;
    float: left;
  }
  .header .inner .gnb .menu > li > a {
    position: relative;
    display: block;
    line-height: 80px;
    text-align: center;
    font-size: 14px;
    color: #777;
    z-index: 3;
    padding: 0 28px;
  }
  .header .inner .gnb .menu > li > a:hover {
    color: #f9d14d;
  }
  .header .inner .gnb .menu > li:hover > a {
    color: #f9d14d;
  }
  .header .inner .gnb .menu > li:hover .submenu {
    visibility: visible;
  }
  .header .inner .gnb .menu > li .submenu {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 0;
    display: block;
    visibility: hidden;
    padding: 80px 20px 40px 20px;
    text-align: center;
    background: #fff;
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.05);
  }
  .header .inner .gnb .menu > li .submenu li {
    padding: 17px 0;
  }
  .header .inner .gnb .menu > li .submenu li a {
    font-size: 13px;
    white-space: nowrap;
  }
  .header .inner .gnb .menu > li .submenu li a:hover {
    color: #f9d14d;
  }
  .header .inner .member {
    position: relative;
    display: block;
    margin-left: auto;
    margin-top: 25px;
  }
  .header .inner .member .member-list {
    position: relative;
    display: block;
  }
  .header .inner .member .member-list li {
    position: relative;
    display: block;
    float: left;
    margin-left: 42px;
  }
  .header .inner .member .member-list li:first-child {
    margin-left: 0;
  }
  .header .inner .member .member-list li a {
    position: relative;
    display: block;
    width: 23px;
    height: 23px;
  }
  .header .inner .member .member-list li a:hover .tooltip {
    visibility: visible;
  }
  .header .inner .member .member-list li a .tooltip {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 28px;
    display: inline-block;
    visibility: hidden;
    color: #fff;
    background: #000;
    white-space: nowrap;
    padding: 4px 8px;
    border-radius: 3px;
    font-size: 11px;
  }
  .header .inner .member .member-list li a .tooltip::before {
    content: "";
    position: absolute;
    left: 50%;
    transform: translateX(-50%) rotate(45deg);
    top: -3px;
    display: block;
    background: #000;
    width: 6px;
    height: 6px;
  }
  .header .inner .member .member-list li .member-cart {
    background: url("@/assets/images/ico-cart.png") no-repeat center;
  }
  .header .inner .member .member-list li .member-mypage {
    background: url("@/assets/images/ico-user.png") no-repeat center;
  }
  .header .inner .member .member-list li .member-login {
    background: url("@/assets/images/ico-login.png") no-repeat center;
  }

  .header-fix {
    position: fixed;
    left: 0;
    top: 0;
    width: 100%;
  }

  .mb-bt {
    position: absolute;
    left: 28px;
    top: 50%;
    transform: translateY(-50%);
    display: none;
    width: 30px;
    height: 23px;
    background: url("@/assets/images/btn-menu-line.png") no-repeat center;
    border: 0;
    cursor: pointer;
  }

  /* 상단 반응형 */
  @media all and (max-width: 1080px) {
    .menu > li > a {
      padding: 0 18px !important;
    }

    .member-list > li {
      margin-left: 22px !important;
    }
  }
  @media all and (max-width: 880px) {
    .menu > li > a {
      padding: 0 10px !important;
    }
  }
  @media all and (max-width: 800px) {
    .logo {
      position: absolute;
      left: 50%;
      top: 50%;
      transform: translate(-50%, -50%);
      margin-top: 0 !important;
      margin-right: 0 !important;
    }

    .gnb {
      display: none !important;
    }

    .member-list li:last-child a {
      display: none !important;
    }

    .mb-bt {
      display: block;
    }
  }
</style>