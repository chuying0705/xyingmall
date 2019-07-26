<template>
  <div class="wrap">
    <div class="address-box">
      <i-cell-group>
        <i-cell title="吴彦祖 13212341234" label="标题下方的描述信息" is-link url="/pages/address/addressList/main"></i-cell>
      </i-cell-group>
    </div>
    <div class="line"></div>
    <div class="good-box">
      <i-cell title="小颖商城" i-class="shop-box">
        <i-icon type="shop_fill" slot="icon" />
      </i-cell>
      <div class="content-box">
        <div class="img-box"></div>
        <div class="desc-box">
          <div class="title">2侏罗纪世界主题公园侏罗纪世界主题公园2侏罗纪世界主题公园侏罗纪世界主题公园</div>
          <p class="subTitle">3侏罗纪世界主题公园</p>
        </div>
        <div class="price">￥<span>10000</span>.00</div>
        <view class="count-box">
          <i-input-number :value="count" min="1" max="100" @change="handleCountChange" />
        </view>
      </div>
      <div class="ticket-box">
        <i-cell title="优惠券"  is-link url="/pages/coupons/myCoupons/main"></i-cell>
      </div>
      <div class="price-box">
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

        <!--<i-cell title="商品金额"  :value="'￥' + total"></i-cell>-->
        <!--<i-cell title="运费"  :value="'+￥' + fare" ></i-cell>-->
        <!--<i-cell title="优惠券"  :value="'-￥' + coupons" ></i-cell>-->
        <!--<i-cell title="实付金额"  :value="'￥' + final" i-class="final-box"></i-cell>-->
      </div>

      <i-button @click="handleClick" type="success">微信支付</i-button>
    </div>

    <div></div>
  </div>


</template>

<script>
  export default {
    data () {
      return {
        total: 1000,
        fare:10,
        coupons:20,
        final:990

      }
    },
    components:{
    },
    methods: {
      handleClick: function() {

      }

    }
  }
</script>

<style scoped lang="scss">
  .wrap{
    background-color: #f7f7f7;
    .address-box{
      width: 100%;
      padding: 10rpx 0;
      background-color: white;
    }
    .line{
      width: 100%;
      height: 10rpx;
      background-image: url("../../../static/imgs/line.png");
      background-size: 100% 100%;
      margin-bottom: 20rpx;
    }

    .good-box{
      /deep/ .shop-box{
        border-bottom: 1px solid #e5e5e5;

      }

      .content-box{
        flex: 1;
        /*width: 400rpx;*/
        height: 210rpx;
        position: relative;
        background-color: white;
        padding: 30rpx;
        /*border-bottom: 1px solid #eee;*/
        margin-bottom: 20rpx;

        .img-box{
          width: 140rpx;
          height: 140rpx;
          background-image: url("http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg");
          background-size: cover;
          /*float: left;*/
          margin-right: 20rpx;
        }
        .desc-box{
          position: absolute;
          left: 190rpx;
          top: 30rpx;
          /*line-height: 50rpx;*/

          .title{
            width: 95%;
            overflow:hidden;
            text-overflow:ellipsis;
            display:-webkit-box;
            -webkit-box-orient:vertical;
            -webkit-line-clamp:2;
            font-size: 28rpx;
          }
          .subTitle{
            color: #999;
            font-size: 26rpx;
            margin-top: 20rpx;
          }


        }

        .price{
          color: #d24844;
          font-size: 26rpx;
          position: absolute;
          left: 190rpx;
          bottom: 30rpx;
          span{
            font-size: 32rpx;
          }
        }
        .count-box{
          position: absolute;
          right: 30rpx;
          bottom: 30rpx;
        }
      }

    }

    .ticket-box{
      /*border-bottom: 1px solid #e5e5e5;*/
      margin-bottom: 20rpx;
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
        font-weight: 800;
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
