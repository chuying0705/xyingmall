<template>
  <swiper class="swiper" :indicator-dots="indicatorDots" :autoplay="autoplay" :interval="interval" :duration="duration" :circular="circular">
    <block v-for="(item,index) in swiperList" :key="index">
      <swiper-item>
        <div class="slide-image" :style="'background-image:url('+ item + ')'"></div>
      </swiper-item>
    </block>
  </swiper>
</template>

<script>
  export default {
    data () {
      return {
        // imgUrls: [
        //   'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
        //   'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
        //   'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
        // ],
        indicatorDots: true,
        autoplay: false,
        interval: 2000,
        duration: 1000,
        circular: true,
        // styleObject: {
        //   height: '150px'
        // }
      }
    },
    props:{
      swiperList:{},
    },
    mounted() {
        console.log(this.styleObject);

    },
    methods:{}
  }
</script>

<style scoped>
  .slide-image{
    width: 100%;
    height: 100%;
    background-size: cover;
  }

</style>
