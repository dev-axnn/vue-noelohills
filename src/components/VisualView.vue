<template>
  <!-- VISUAL -->
  <section class="visual">
    <Swiper 
      :modules="modules" 
      :autoplay="{
        delay: 5000,
        disableOnInteraction: false,
      }"
      :loop="true"
      @swiper="onSwiper"
      @slideChange="onSlideChange"
      class="sw-visual"
    >
      <swiper-slide class="swiper-slide" v-for="(item, index) in slideData" :key="index">
        <VisualSwV 
          :vLink="item.vLink"
          :vImg="item.vImg"
          :vTitle="item.vTitle"
          :vTxt="item.vTxt"
          :vBt="item.vBt"
        />
      </swiper-slide>
    </Swiper>

    <!-- 슬라이드 컨트롤 -->
    <div class="sw-visual-control">
      <div class="sw-visual-pg"></div>
    </div>
  </section>
</template>

<script>
  import { ref } from 'vue';

  import { Autoplay } from 'swiper';
  import { Swiper, SwiperSlide } from 'swiper/vue';
  import 'swiper/css';

  import VisualSwV from '@/components/VisualSwiper.vue';
  
  export default {
    components: {
      VisualSwV,
      Swiper,
      SwiperSlide
    },

    setup(){
      const slideData = ref([]);
      slideData.value = [
        {
          vLink: "#",
          vImg: "PC_minimal_new.png",
          vTitle: "SPECIAL OFFER",
          vTxt: "노엘로힐스가 제안하는<br>아기 스킨케어 출산준비물",
          vBt: "SHOP"
        },
        {
          vLink: "#",
          vImg: "PC1_newborn.png",
          vTitle: "SPECIAL OFFER",
          vTxt: "노엘로힐스가 제안하는<br>아기 스킨케어 출산준비물",
          vBt: "SHOP"
        },
        {
          vLink: "#",
          vImg: "PC2_BabyEssence.png",
          vTitle: "밀크 에센스 로션",
          vTxt: "국내 최초 100%<br>식품 그레이드 성분",
          vBt: "SHOP"
        },
        {
          vLink: "#",
          vImg: "PC3_Branding.png",
          vTitle: "8:23",
          vTxt: "가족에게 행복을 선사하는<br>스킨케어 라이프스타일 브랜드"
        }
      ];
      const onSwiper = (swiper) => {
        console.log(swiper)
      };
      const onSlideChange = () => {

      };

      return{
        onSwiper,
        onSlideChange,
        modules: [Autoplay],
        slideData
      }
    }
  }
</script>

<style>
  /* VISUAL */
  .visual {
    position: relative;
    display: block;
  }
  .visual .sw-visual {
    width: 100%;
    height: 100%;
  }
  .visual .sw-visual .swiper-slide a {
    position: relative;
    display: block;
    width: 100%;
    height: 100%;
  }
  .visual .sw-visual .swiper-slide a .visual-img {
    position: relative;
    display: block;
    height: 600px;
  }
  .visual .sw-visual .swiper-slide a .visual-1 {
    background: url("@/assets/images/PC_minimal_new.png") no-repeat center;
    background-size: cover;
  }
  .visual .sw-visual .swiper-slide a .visual-2 {
    background: url("@/assets/images/PC1_newborn.png") no-repeat center;
    background-size: cover;
  }
  .visual .sw-visual .swiper-slide a .visual-3 {
    background: url("@/assets/images/PC2_BabyEssence.png") no-repeat center;
    background-size: cover;
  }
  .visual .sw-visual .swiper-slide a .visual-4 {
    background: url("@/assets/images/PC3_Branding.png") no-repeat center;
    background-size: cover;
  }
  .visual .sw-visual .swiper-slide a .visual-txt {
    position: relative;
    display: block;
    text-align: center;
    padding: 50px 0;
  }
  .visual .sw-visual .swiper-slide a .visual-txt .visual-title {
    position: relative;
    display: block;
    font-size: 30px;
    font-weight: 700;
    color: #777;
    margin-bottom: 20px;
  }
  .visual .sw-visual .swiper-slide a .visual-txt .visual-desc {
    position: relative;
    display: block;
    font-size: 20px;
    font-weight: 500;
    color: #777;
    margin-bottom: 35px;
  }
  .visual .sw-visual .swiper-slide a .visual-txt .visual-bt {
    position: relative;
    display: inline-block;
    font-size: 20px;
    color: #fff;
    background: #ffcc00;
    padding: 10px 20px;
  }
  .visual .sw-visual .sw-visual-control {
    position: absolute;
    left: 50%;
    transform: translateX(-50%);
    top: 550px;
    display: block;
    z-index: 9;
  }
  .visual .sw-visual .sw-visual-control .sw-visual-pg .swiper-pagination-bullet {
    width: 10px;
    height: 10px;
    background: #fff;
    opacity: 1;
    margin: 0 4px;
  }
  .visual .sw-visual .sw-visual-control .sw-visual-pg .swiper-pagination-bullet-active {
    background: #ffcf42;
  }

  /* Visual 반응형 */
  @media all and (max-width: 1320px) {
    .visual-img {
      height: 45vw !important;
    }

    .visual-txt {
      padding: 3.78vw 0 !important;
    }

    .sw-visual-control {
      top: 41.66vw !important;
    }
  }
  @media all and (max-width: 800px) {
    .visual-img {
      height: 125vw !important;
    }

    .visual-1 {
      background: url("@/assets/images/M_minimal_new.png") no-repeat center !important;
    }

    .visual-2 {
      background: url("@/assets/images/M1_newborn.png") no-repeat center !important;
    }

    .visual-3 {
      background: url("@/assets/images/M2_BabyEssence.png") no-repeat center !important;
    }

    .visual-4 {
      background: url("@/assets/images/M3_Branding.png") no-repeat center !important;
    }

    .visual-txt {
      margin-bottom: 10px !important;
    }

    .visual-title {
      font-size: 28px !important;
    }

    .visual-desc {
      font-size: 18px !important;
      margin-bottom: 25px !important;
    }

    .sw-visual-control {
      top: 120vw !important;
    }
  }
  @media all and (max-width: 480px) {
    .visual-img {
      height: 124.4vw !important;
    }

    .visual-1 {
      background: url("@/assets/images/v_480_1.png") no-repeat center !important;
    }

    .visual-2 {
      background: url("@/assets/images/v_480_2.png") no-repeat center !important;
    }

    .visual-3 {
      background: url("@/assets/images/v_480_3.png") no-repeat center !important;
    }

    .visual-4 {
      background: url("@/assets/images/v_480_4.png") no-repeat center !important;
    }

    .visual-txt {
      margin-bottom: 10px !important;
    }

    .visual-title {
      font-size: 24px !important;
      margin-bottom: 15px !important;
    }

    .visual-desc {
      font-size: 16px !important;
      margin-bottom: 20px !important;
    }

    .visual-bt {
      font-size: 18px !important;
      padding: 8px 16px !important;
    }

    .sw-visual-control {
      top: 115vw !important;
    }
  }
</style>