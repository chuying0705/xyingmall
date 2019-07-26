<template>
  <div class="order-warp">
    <i-tabs :current="current" color="#E60026"  @change="handleChangeScroll">
      <i-tab key="tab1" title="全部订单"></i-tab>
      <i-tab key="tab2" title="未付款"></i-tab>
      <i-tab key="tab3" title="待发货"></i-tab>
      <i-tab key="tab4" title="待收货"></i-tab>
      <i-tab key="tab5" title="待评价"></i-tab>
    </i-tabs>
    <div class="card-list">

      <div class="card-box" v-for="(item, index) in orderList" :key="index">
        <div class="card-top">
          <div class="order-number">订单号：{{item.orderNum}}</div>
          <div class="status" :class="statusText[item.status][0]">{{statusText[item.status][1]}}</div>
        </div>
        <div class="card-center" @click="goToDetail">
          <div class="content-box">
            <div class="img-box"></div>
            <div class="desc-box">
              <p class="title">{{item.goodsName}}</p>
              <div class="desc">规格:<span>{{item.specification}}</span></div>
              <div class="count">x<span>{{item.count}}</span></div>
            </div>
          </div>
        </div>
        <div class="card-bottom">
          <div class="price">总价: <span>￥{{item.total}}</span></div>
        </div>
      </div>

    </div>
  </div>


</template>

<script>

export default {
  data () {
    return {
      current: 'tab1',
      orderList:[
        {
          orderNum:'123456789012345',
          status:0,
          goodsName:'1侏罗纪世界主题公园侏罗纪世界主题公园2侏罗纪世界主题公园侏罗纪世界主题公园',
          specification:'500ML',
          count:2,
          total:'500.00',

        },
        {
          orderNum:'123456789012345',
          status:1,
          goodsName:'2侏罗纪世界主题公园侏罗纪世界主题公园2侏罗纪世界主题公园侏罗纪世界主题公园',
          specification:'500ML',
          count:2,
          total:'500.00',

        },
      ],
      statusText:{
        0:['wait-pay','待支付'],
        1:['wait-receive','待发货'],
        2:['wait-receive','待收货'],
        3:['wait-rate','待评价']
      },

    }
  },

  created () {
    // 调用应用实例的方法获取全局数据
    // this.getUserInfo()
  },

  methods: {
    handleChangeScroll: function({mp: { detail }}) {
      this.current = detail.key
    },
    goToDetail: function() {
      wx.navigateTo({
        url:"../orderDetail/main"
      })
    }
  }
}
</script>

<style scoped lang="scss">

  .order-warp{
    width: 100%;
    height: 100vh;
    background-color: #f5f5f5;

    .card-list{

      .card-box{
        background-color: white;
        font-size: 28rpx;
        margin: 20rpx 0;

        .card-top{
          padding: 20rpx 30rpx;
          height: 60rpx;
          .order-number{
            color: #666;
            float: left;
            line-height: 60rpx;
          }

          .status{
            width: 100rpx;
            padding: 10rpx 20rpx;
            border-radius: 10rpx;
            text-align: center;
            color: white;
            float: right;
          }

          .wait-pay{
            /*background-image: url("../assets/btn_success.png");*/
            background-color: #e60026;
          }
          .wait-receive{
            background-color: #999;
            pointer-events: none;
          }
        }

        .card-center{
          .content-box{
            /*flex: 1;*/
            height: 120rpx;
            position: relative;
            border-top: 1px solid #e5e5e5;
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
        }

        .card-bottom{
          position: relative;
          padding: 30rpx;
          height: 30rpx;

          .price{
            position: absolute;
            top: 20rpx;
            span{
              color: #e60026;

            }
          }
        }
      }
    }
  }

</style>
