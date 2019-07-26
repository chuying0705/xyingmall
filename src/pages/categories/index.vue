<template>
  <div class="wrap">
    <div class="top-box">
      <!--<div class="categories"> <i-icon type="other" size="28" color="red"></i-icon></div>-->
      <div class="search-box">
        <i-icon class="search-icon" type="search" size="20" color="#999"></i-icon>搜索商品
      </div>
    </div>

    <div class="cate-content">
      <scroll-view class="scroll-view" scroll-y>
        <div v-for="(item, index) in categories" :key="index" :class="['cate-item', selectItem === index? 'select-item':'' ]" @click="checkCate(index)">{{item}}</div>
      </scroll-view>
      <scroll-view class="goods-box" scroll-y>
        <div class="cate">{{categories[selectItem]}}</div>
        <div class="goods">
          <div class="good-item" v-for="(good, i) in goods" :key="i">
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
  </div>
</template>

<script>
  export default {
    data () {
      return {
        categories: ['热搜推荐', '手机数码', '女装内衣', '男装内衣', '家用电器', '鞋靴箱包', '户外运动', '热搜推荐', '手机数码', '女装内衣', '男装内衣', '家用电器', '鞋靴箱包', '户外运动'],
        selectItem: 0,
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
      checkCate: function (index) {
        console.log(index)
        this.selectItem = index
      }
    }
  }
</script>

<style scoped lang="scss">
  .wrap{
    height: 100vh;
    /*display: flex;*/
    /*flex-direction:column;*/
  }
  .top-box{
    border-bottom: 1px solid #dddddd;
    padding: 19rpx 30rpx;
    width: 690rpx;
    .search-box{
      height: 60rpx;
      line-height: 60rpx;
      border-radius: 30rpx;
      background-color: #f1f1f1;
      color: #999;
      text-align: center;
      font-size: 30rpx;
    }
    position: absolute;
    top: 0;
  }

  .cate-content{
    .scroll-view{
      /*flex:1;*/
      width: 160rpx;
      background-color: #f8f8f8;
      position: absolute;
      top: 100rpx;
      bottom: 0;
      ::-webkit-scrollbar {
        display: none;
      }
      .cate-item{
        height: 100rpx;
        line-height: 100rpx;
        font-size: 28rpx;
        color: #333;
        text-align: center;
      }

      .select-item{
        background-color: #fff;
        color: #d74a45;
        font-size: 30rpx;
      }
    }

    .goods-box{
      width: 590rpx;
      position: absolute;
      top: 100rpx;
      bottom: 0;
      left: 160rpx;
      background-color: #f1f1f1;
      ::-webkit-scrollbar {
        display: none;
      }

      .cate{
        height: 60rpx;
        line-height: 60rpx;
        background-color: #fff;
        font-size: 28rpx;
        padding-left: 20rpx;
      }

      .goods{
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        padding: 20rpx 25rpx;
        .good-item{
          width: 265rpx;
          height: 350rpx;
          margin: 10rpx 0;
          overflow: hidden;
          background-color: #fff;
          border-radius: 5rpx;

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
    }


  }

</style>
