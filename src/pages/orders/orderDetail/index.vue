<template>
  <div class="order-box">
    <div class="module">
      <i-steps :current="current" i-class="step">
        <i-step>
          <view slot="title">
            提交订单
          </view>
        </i-step>
        <i-step>
          <view slot="title">
            配送中
          </view>
        </i-step>
        <i-step>
          <view slot="title">
            交易完成
          </view>
        </i-step>
      </i-steps>

      <div class="logistics-box">
        <div class="desc">您的订单已提交，请在30分钟内支付哦！欢迎下次光临欢迎下次光临</div>
        <p>2018-9-28 12:00:00</p>
      </div>
      <div class="order-detail">
        <p>订单状态：<span>已签收</span></p>
        <p>订单编号：<span>12345678901</span></p>
        <p>下单时间：<span>2018-9-28 12:00:00</span></p>
        <div class="btn" @click="goToPay">去支付/再次购买</div>
      </div>
    </div>

    <div class="module">
      <div class="order-detail">
        <p class="price">商品金额：<span>￥100.00</span></p>
        <p>订单优惠：<span>10.00</span></p>
        <p>收货地址：<span class="add">您的订单已提交，请在30分钟内支付哦！欢迎下次光临欢迎下次光临</span></p>
        <p>收货人：&nbsp&nbsp&nbsp<span>吴彦祖 13212341234</span></p>
        <p>配送方式：<span>普通快递</span></p>
      </div>
    </div>

    <div class="module">
      <div class="content-box">
        <div class="img-box"></div>
        <div class="desc-box">
          <p class="title">欢迎下次光临欢迎下次光临</p>
          <div class="desc">规格:<span>100</span></div>
          <div class="count">x<span>1</span></div>
        </div>
      </div>
    </div>

    <div class="module price-box">
      <i-row i-class="price-row">
        <i-col span="8" i-class="col-left">商品金额</i-col>
        <i-col span="16" i-class="col-right">￥{{total}}</i-col>
      </i-row>
      <i-row i-class="price-row">
        <i-col span="8" i-class="col-left">运费</i-col>
        <i-col span="16" i-class="col-right">+￥{{fare}}</i-col>
      </i-row>
      <i-row i-class="price-row">
        <i-col span="8" i-class="col-left">优惠券</i-col>
        <i-col span="16" i-class="col-right">-￥{{coupons}}</i-col>
      </i-row>
      <i-row i-class="price-row final-box">
        <i-col span="8" i-class="col-left">实付金额</i-col>
        <i-col span="16" i-class="col-right ">￥{{final}}</i-col>
      </i-row>
    </div>

  </div>


</template>

<script>

export default {
  data () {
    return {
      current : 1,
      total: 1000,
      fare:10,
      coupons:20,
      final:990

    }
  },

  components: {

  },

  created () {
    // 调用应用实例的方法获取全局数据
    // this.getUserInfo()
  },

  methods: {
    goToPay: function() {
      wx.navigateTo({
        url:'../../purchase/main'
      })
    }
  }
}
</script>

<style scoped lang="scss">
  .grayBox {
    width: 100%;
    height: 10rpx;
    background-color: #ddd;
  }

  .order-box{
    width: 100%;
    height: 100vh;
    background-color: #f5f5f5;

    .module{
      background-color: white;
      margin-bottom: 20rpx;
      font-size: 28rpx;
    }

    /deep/ .step{
      padding: 30rpx 0;
      ._view{
        /*color: #e60026;*/
      }
    }

    .logistics-box{
      padding: 20rpx 30rpx;
      /*border-top: 1px solid #e5e5e5;*/
      border-bottom: 1px solid #e5e5e5;

      .desc{

      }
      > p {
        font-size: 24rpx;
        color: #999;
        margin-top: 20rpx;
      }

    }

    .order-detail{
      padding: 20rpx 30rpx;

      >p{
        margin: 20rpx 0;
        color: #999;
        span{
          color: #333;
        }
      }

      .btn{
        border: 1px solid #e60026;
        border-radius: 10rpx;
        color: #e60026;
        padding: 20rpx;
        text-align: center;
        margin-top: 20rpx;
      }

      .price{
        span{
          color: red;

        }
      }

      .add{
        width:540rpx;
        display:inline-table;

      }
    }

    .content-box{
      /*flex: 1;*/
      height: 120rpx;
      position: relative;
      /*border-top: 1px solid #e5e5e5;*/
      border-bottom: 1px solid #e5e5e5;
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
        width: 550rpx;
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

      .desc{
        position: absolute;
        top: 80rpx;
        color: #999;
      }
      .count{
        position: absolute;
        top: 80rpx;
        left: 280rpx;
        color: #999;
      }


    }

    /deep/ .price-box{
      padding: 20rpx 30rpx;
      font-size: 28rpx;
      background-color: white;

      .price-row{
        padding: 10rpx 0;
      }

      .final-box{
        border-top: 1px solid #eee;
        font-size: 32rpx;
        padding: 20rpx 0;
      }

      .col-right{
        text-align: right;
        color: red;
      }
    }



  }


</style>
