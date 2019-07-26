<template>
  <div >
    <Swiper :swiperList="imgUrls"></Swiper>

    <div>
      <div class="grayBox"></div>
      <div class="mudule">
        <div class="title">好物推荐</div>
      </div>
      <Scroll></Scroll>
    </div>

    <div>
      <!--<div class="grayBox"></div>-->
      <div class="mudule">
        <div class="title">热门商品</div>
      </div>
      <Hot-list></Hot-list>
    </div>
  </div>


</template>

<script>
import swiper from '@/components/swiper'
import scroll from '@/components/scroll'
import hotList from '@/components/hotList'

export default {
  data () {
    return {
      imgUrls: [
        'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
        'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
        'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
      ],
      recommends: ['a', 'b', 'c']
    }
  },

  components: {
    'Swiper': swiper,
    'Scroll': scroll,
    'HotList': hotList
  },

  created () {
    // 调用应用实例的方法获取全局数据
    // this.getUserInfo()
  },

  methods: {}
}
</script>

<style scoped lang="scss">
  .grayBox {
    width: 100%;
    height: 10rpx;
    background-color: #ddd;
  }
  .mudule{
    padding: 20rpx 20rpx;
    text-align: center;
    border-bottom:1px solid #ddd;
    .title{
      font-size: 28rpx;
      display: inline-block;
      &:before,&:after{
        content: "";
        border-top: 2rpx solid #000;
        display: block;
        width: 50rpx;
        margin: 20rpx 30rpx 0;
      }

      &:before{
        float: left;
      }
      &:after{
        float: right;
      }

    }
  }


</style>
