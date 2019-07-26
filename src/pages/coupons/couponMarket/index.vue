<template>
  <div >
    <div class="card-list">
      <div class="card-box" v-for="(item, index) in couponList" :key="index">

        <i-row>
          <i-col span="8" i-class="col-class">
            <div class="card-left left-active">
              <div class="count">￥ <span>{{item.discount}}</span></div>
              <div class="title">满{{item.fill}}可用</div>
            </div>
          </i-col>
          <i-col span="15" offset="1" i-class="col-class">
            <div class="card-right">
              <p class="title">{{item.title}}</p>
              <p class="desc">{{item.desc}}</p>
              <p class="date">{{item.validFrom}} - {{item.validUtil}}</p>
              <div class="btn class-active" >立即领取</div>
            </div>
          </i-col>
        </i-row>

      </div>

    </div>
  </div>


</template>

<script>

  export default {
    data () {
      return {
        current: 'tab1',
        couponList:[
          {
            couponsNo:'1234567',
            discount:20,
            fill:1000,
            title:'新人福利',
            desc:'满100可用',
            validFrom:'2018.01.01 ',
            validUtil: '2018.12.31',
            status:0

          },
          {
            couponsNo:'1234567',
            discount:20,
            fill:100,
            title:'新人福利',
            desc:'满100可用',
            validFrom:'2018.01.01 ',
            validUtil: '2018.12.31',
            status:1

          },
          {
            couponsNo:'1234567',
            discount:20,
            fill:100,
            title:'新人福利',
            desc:'满100可用',
            validFrom:'2018.01.01 ',
            validUtil: '2018.12.31',
            status:2

          },
        ],
        statusText:{
          0:['立即使用','class-active','left-active'],
          1:['已使用','class-used','left-used'],
          2:['已过期','class-expired','left-expired']
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
      }
    }
  }
</script>

<style scoped lang="scss">

  .card-list{
    padding: 20rpx 30rpx;

    .card-box{
      background-color: white;
      font-size: 28rpx;
      margin: 20rpx 0;

      font-size: 28rpx;
      box-shadow: 8rpx 10rpx 5rpx #f6f6f6;

      .card-left{
        color: white;
        /*text-align: center;*/
        padding: 30rpx;

        .count{
          font-weight: 800;

          span{
            font-size: 70rpx;

          }

        }
      }

      .left-active{
        background: linear-gradient(to bottom right, #5d9de1, #667adc);
      }
      .left-used{
        background-color: #c2c2c2;
      }
      .left-expired{
        background-color: #c2c2c2;
      }

      .card-right{
        /*border: 1px solid red;*/
        height: 160rpx;
        position: relative;
        .title{
          font-weight: 800;
          font-size: 30rpx;
          margin-top: 20rpx;
        }

        .desc{
          font-size: 24rpx;
          position: absolute;
          bottom: 0;
          top: 60rpx;
        }

        .date{
          color: #4d4c4d;
          font-size: 18rpx;
          position: absolute;
          bottom: 0;
          left: 0;
        }

        .btn{
          width: 140rpx;
          height: 50rpx;
          line-height: 50rpx;
          border-radius: 50rpx;
          text-align: center;
          position: absolute;
          bottom: 50rpx;
          right: 10rpx;

        }
        .class-active{
          border: 1px solid #5293d5;
          color: #5293d5;
        }
        .class-used{
          border: 1px solid #999;
          color: #999;
          pointer-events: none;
        }
        .class-expired{
          border: 1px solid #999;
          color: #999;
          pointer-events: none;
        }
      }


    }
  }


</style>
