<template>
  <div class="scroll-wrap">
    <scroll-view  scroll-x class="scroll-wrap" >
      <div class="recommends-wrap">
        <div class="good-item" v-for="(good, i) in goods" :key="i" @click="goToDetail">
          <img :src="good.imgs[0]" alt="">
          <div class="bottom-box">
            <div class="good-title">{{good.title}}</div>
            <div class="good-price">
              ￥<span class="price">{{good.price}}</span>
              <span class="oriPrice">{{good.originPrice}}</span>
              <i-icon class="icon" type="publishgoods_fill" size="24" color="#E60026"></i-icon>
            </div>
          </div>

        </div>
      </div>
    </scroll-view>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        goods: [
          {
            title: 'JavaScript 从入门到放弃 手绘金装版 包邮不满意包退换',
            price: 100,
            originPrice: 999,
            imgs: [
              'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
            ]
          },
          {
            title: '颈椎病康复指南 手绘金装版 包邮不满意包退换',
            price: 100,
            originPrice: 999,
            imgs: [
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
              'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
            ]
          },
          {
            title: 'JavaScript 从入门到放弃 手绘金装版 包邮不满意包退换',
            price: 100,
            originPrice: 999,
            imgs: [
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg',
              'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg'
            ]
          },
          {
            title: 'JavaScript 从入门到放弃 手绘金装版 包邮不满意包退换',
            price: 100,
            originPrice: 999,
            imgs: [
              'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
            ]
          },
          {
            title: '颈椎病康复指南 手绘金装版 包邮不满意包退换',
            price: 100,
            originPrice: 999,
            imgs: [
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
              'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg'
            ]
          },
          {
            title: 'JavaScript 从入门到放弃 手绘金装版 包邮不满意包退换',
            price: 100,
            originPrice: 999,
            imgs: [
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg',
              'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
              'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg'
            ]
          }
        ]
      }
    },
    methods: {
      goToDetail: function() {
        wx.navigateTo({
          url: "/pages/goodDetail/main"
        })
      }
    }
  }
</script>

<style scoped lang="scss">
  .scroll-wrap{
    background-color: #f1f1f1;
  }
  .recommends-wrap{
    white-space: nowrap;
    display: inline-block;
    padding: 20rpx;

    .good-item{
      width: 265rpx;
      height: 350rpx;
      margin: 10rpx 0;
      overflow: hidden;
      background-color: #fff;
      border-radius: 5rpx;
      display: inline-block;
      margin: 12rpx;
      box-shadow: 5rpx 5rpx 5rpx #eee;

      img{
        height: 220rpx;
      }

      .bottom-box{
        padding: 10rpx;

        .good-title{
          font-size: 22rpx;
          color: #333;
          overflow:hidden;
          text-overflow:ellipsis;
          display:-webkit-box;
          -webkit-box-orient:vertical;
          -webkit-line-clamp:2;

        }

        .good-price{
          font-size: 24rpx;
          color: #E60026;

          .price{
            font-size: 34rpx !important;
            font-weight: 600;
          }
          .oriPrice{
            text-decoration: line-through;
            color: #ccc;
            margin-left: 10rpx;
          }
          .icon{
            float: right;
          }
        }
      }
    }
  }



</style>
