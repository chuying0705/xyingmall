<template>
  <div class="wrap">
    <Swiper :swiperList="goodsItem.imgUrls"></Swiper>
    <div class="desc-box">
      <i-row i-class="title-box box-row">
        <i-col span="21" i-class="col-class">
          <div class="good-title">{{goodsItem.title}}</div>
          <div class="good-price">
            ￥<span class="price">{{goodsItem.price}}</span>
            <span class="oriPrice">{{goodsItem.originPrice}}</span>
          </div>
        </i-col>
        <i-col offset="1" span="2" i-class="col-class-left" >
          <button class="icon share_icon" @click="" open-type="share"></button>
          <i-icon class="icon" type="share" size="24" color="#E60026"></i-icon>
          <p>分享</p>
        </i-col>
      </i-row>
      <i-row i-class="box-row count-box">
        <p> <span>库存:100件</span> <span>销量:100</span> <span>运费:包邮</span> </p>
        <p>
          <div class="desc-tags">
            <i-icon class="icon" type="success_fill" size="16" color="#E60026"></i-icon> <span>正品100%</span>
          </div>
        <div class="desc-tags">
          <i-icon class="icon" type="success_fill" size="16" color="#E60026"></i-icon> <span>如实描述</span>
        </div>
        </p>
      </i-row>
    </div>

    <div class="box-row ticket">
      领券
      <div class="ticket-tags">新人福利</div>
      <div class="ticket-tags">新人福利</div>
      <div class="ticket-tags">新人福利</div>

    </div>

    <div class="box-row " @click="openSpecification">
      选择 商品属性
    </div>
    <div class="detail-box">
      <div class="box-row good-detail-title">
        商品详情
      </div>
      <img v-for="item in goodsItem.imgUrls" :src="item" alt="">
    </div>


    <i-row i-class="bottom-fixed">
      <i-col span="12" i-class="left">
        加入购物车
      </i-col>
      <i-col span="12" i-class="right" @click="buyNow">
        立即购买
      </i-col>
    </i-row>

    <div class="product-box"  :class="showSpecification? 'slideup' : ''">
      <i-row i-class="good-detail">
        <div class="content-box">
          <div class="img-box"></div>
          <div class="desc-box">
            <p class="title">2侏罗纪世界主题公园侏罗纪世界主题公园2侏罗纪世界主题公园侏罗纪世界主题公园</p>
            <div class="price">￥<span>10000</span>.00</div>
          </div>
        </div>
      </i-row>
      <i-row i-class="good-detail">
        <div class="content-box-center">
          <p>商品规格</p>
          <div class="tags-box">
            <div class="tags">红</div>
            <div class="tags">侏罗纪世界</div>
            <div class="tags">侏罗纪世界</div>
            <div class="tags">侏罗纪</div>
            <div class="tags">世界</div>
            <div class="tags">世界</div>
          </div>
        </div>
      </i-row>
      <i-row i-class="good-detail">
        <div class="content-box content-box-bottom">
          <p>购买数量</p>
          <view class="count-box">
            <i-input-number :value="count" min="1" max="100" @change="handleCountChange" />
          </view>
        </div>
      </i-row>

      <div class="delete-box" @click="closeSpecification">
        <i-icon class="icon" type="delete_fill" size="24" color="#999"></i-icon>
      </div>


    </div>

  </div>


</template>

<script>
  import swiper from '@/components/swiper'

  export default {
    data () {
      return {
        goodsItem:{
          title: 'JavaScript 从入门到放弃 手绘金装版 包邮不满意包退换',
          price: 100.00,
          originPrice: 999,
          imgUrls: [
            'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg',
            'http://img06.tooopen.com/images/20160818/tooopen_sy_175866434296.jpg',
            'http://img06.tooopen.com/images/20160818/tooopen_sy_175833047715.jpg',
            'http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg'

          ]
        },
        count:1,
        showSpecification: false,

      }
    },
    components:{
      'Swiper': swiper
    },
    methods: {
      checkCate: function (index) {
        console.log(index)
        this.selectItem = index
      },
      handleCountChange({mp: { detail}}) {
        this.count = detail.value
      },
      openSpecification: function() {
        this.showSpecification = true;
      },
      closeSpecification: function() {
        this.showSpecification = false;
      },
      buyNow:function() {
        if(false){
          this.openSpecification();
        }else{
          wx.navigateTo({
            url:'../purchase/main'
          })
        }
      },
      shareApp: function() {
        console.log("share");
        Page.onShareAppMessage()
      }
    },
    onShareAppMessage: function (res) {
      if (res.from === 'button') {
        // 来自页面内转发按钮
        console.log(res.target)
      }
      return {
        title: '哈哈哈',
        path: '/page/user?id=123'
      }
    }
  }
</script>

<style scoped lang="scss">
  .wrap{
    width: 100%;
    /*height: 100vh;*/
    background-color: #f5f5f5;
    padding-bottom: 96rpx;
    /*display: flex;*/
    /*flex-direction:column;*/
    // >>> 深度作用选择器，能够作用到子组件，sass等无法正确解析 用/deep/代替
    /deep/ .swiper{
      height: 500rpx;
    }

    .desc-box{

      /deep/ .title-box{
        margin-bottom: 0 !important;

         .col-class-left{
          text-align: center;
          font-size: 24rpx;
          margin-top: 30rpx;
        }
      }

      .good-title{
        color: #333;
        font-size: 30rpx;
        font-weight: 600;
      }

      .good-price{
        color: #E60026;
        margin-top: 10rpx;
        font-size: 24rpx;
        font-weight: 600;
        .price{
          font-size: 34rpx;
        }
        .oriPrice{
          text-decoration: line-through;
          color: #ccc;
          margin-left: 20rpx;
          font-size: 30rpx;
        }
        .icon{
          float: right;
        }

        .share_icon{
          background-color: green;
          width: 80rpx;
          height: 80rpx;
        }
      }

      /deep/ .count-box{
        span{
          margin-right: 30rpx;
        }

        .desc-tags{
          float: left;
          font-size: 24rpx;
          margin: 10rpx 30rpx 0 0;
        }

      }
    }

    .ticket-tags{
      display: inline-block;
      /*background-color: #e60026;*/
      color: white;
      padding: 5rpx 20rpx;
      margin-right: 20rpx;
      font-size: 24rpx;
      background-image: url("../../../static/imgs/tag_bg.png");
      background-size: 100% 100%;
    }
    .ticket-tags:nth-child(1){
      margin-left: 10rpx;
    }




    /deep/ .box-row{
      padding: 20rpx 30rpx;
      background-color: white;
      border-bottom: 1px solid #e5e5e5;
      font-size: 28rpx;
      color: #999;
      margin-bottom: 20rpx;
    }

    .detail-box{
      .good-detail-title{
        text-align: center;
        color: #333;
        margin-bottom: 0;
      }
      img{
        display: block;
        width: 100%;
      }
    }





    /deep/ .bottom-fixed{
      width: 100%;
      height: 96rpx;
      border-top: 1px solid #ddd;
      position: fixed;
      bottom: 0;
      left: 0;
      color: white;
      text-align: center;
      z-index: 5;
      view{
        height:100%;
        line-height:96rpx;
      }

      .left{
        background-color: #ee904d;

      }
      .right{
        background-color: #E60026;
      }


    }

    .product-box{
      width: 100%;
      /*height: 0;*/
      position: fixed;
      bottom: 98rpx;
      background-color: white;
      font-size: 30rpx;

      .content-box{
        /*flex: 1;*/
        height: 120rpx;
        position: relative;
        border-top: 1px solid #e5e5e5;
        padding: 30rpx 30rpx;


        .img-box{
          width: 120rpx;
          height: 120rpx;
          background-image: url("http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg");
          background-size: cover;
          position: absolute;
          top: 30rpx;
          left: 30rpx;
        }
        .desc-box{
          width: 450rpx;
          position: absolute;
          left: 170rpx;
          top: 30rpx;

          .title{
            width: 100%;
            overflow:hidden;
            text-overflow:ellipsis;
            display:-webkit-box;
            -webkit-box-orient:vertical;
            -webkit-line-clamp:1;
          }

        }

        .price{
          color: #d24844;
          position: absolute;
          top: 80rpx;
        }

      }

      .content-box-center{
        padding: 20rpx 30rpx;
        border-top: 1px solid #e5e5e5;

        .tags-box{
          width: 100%;
          margin-top: 10rpx;
          display: inline-block;
          font-size: 26rpx;

          .tags{
            float: left;
            border: 1px solid #e5e5e5;
            /*border: 1px solid #E60026;*/
            border-radius: 5rpx;
            padding: 10rpx 20rpx;
            margin:10rpx 20rpx 0 0;
          }
        }

      }

      .content-box-bottom{
        height: 60rpx;
        position: relative;
        p{
          margin-top: 10rpx;
        }
        .count-box{
          position: absolute;
          right: 30rpx;
          top: 30rpx;
        }
      }

      .delete-box{
        width: 60rpx;
        height: 60rpx;
        position: absolute;
        top: 0;
        right: 0;
        .icon{
          position: absolute;
          top: 20rpx;
          right: 20rpx;
        }
      }


      /*height: inherit;*/
      -webkit-transition: all 0.5s cubic-bezier(0, 1, 0.5, 1);
      transition: all 0.5s cubic-bezier(0, 1, 0.5, 1);
      -webkit-transform: translateY(100%);
      transform: translateY(100%);

    }

    .slideup{
      -webkit-transform: translateY(0);
      transform: translateY(0);
    }


  }

</style>
