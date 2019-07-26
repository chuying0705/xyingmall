<template>
    <div class="goods-box">
      <div class="goods">
        <div class="good-item" v-for="(good, i) in goods" :key="i">
          <img :src="good.imgs[0]" alt="">
          <div class="bottom-box">
            <div class="good-title">{{good.title}}</div>
            <div class="good-price">
              ￥<span class="price">{{good.price / good.originPrice}}</span>
              <span class="oriPrice">{{good.originPrice}}</span>
              <i-icon class="icon" type="publishgoods_fill" size="24" color="#E60026"></i-icon>
            </div>
          </div>

        </div>
      </div>
    </div>
</template>

<script>
  export default {
    data () {
      return {
        goods: [
          {
            title: 'JavaScript 从入门到放弃 手绘金装版 包邮不满意包退换 从入门到放弃',
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
    }
  }
</script>

<style scoped lang="scss">
  .goods-box{
    background-color: #f1f1f1;
    .goods{
      display: flex;
      flex-wrap: wrap;
      justify-content: space-between;
      padding: 20rpx;
      .good-item{
        width: 47%;
        height: 380rpx;
        margin: 1.5%;
        overflow: hidden;
        background-color: #fff;
        border-radius: 5rpx;
        img{
          height: 240rpx;
        }

        .bottom-box{
          padding: 10rpx;

          .good-title{
            font-size: 24rpx;
            color: #333;
            overflow:hidden;
            text-overflow:ellipsis;
            display:-webkit-box;
            -webkit-box-orient:vertical;
            -webkit-line-clamp:2;

          }

          .good-price{
            font-size: 26rpx;
            color: #E60026;

            .price{
              font-size: 36rpx !important;
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
  }
</style>
