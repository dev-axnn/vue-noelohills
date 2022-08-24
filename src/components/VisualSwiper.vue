<template>
  <a :href="vLink">
    <!-- require(`@/assets/images/${vImg}`) 이미지를 불러오는 단어 -->
    <div class="visual-img bg" :style="{backgroundImage: 'url(' + require(`@/assets/images/${vImg}`) + ')'}"></div>
    <div class="visual-txt">
      <h3 class="visual-title">{{vTitle}}</h3>
      <span class="visual-desc" v-html="vTxt"></span>
      <span class="visual-bt">{{vBt}}</span>
    </div>
  </a>
</template> 

<script>
export default {
  props: ['vLink', 'vImg', 'vTitle', 'vTxt', 'vBt'],
  setup (){
    return{

    }
  }
}
</script>

<style>
  .bg {
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
  }
</style>