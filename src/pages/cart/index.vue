<template>
  <div>
    <div class="gray-box"></div>
    <div class="center-box">
        <i-swipeout :actions="actions" @change="handlerDelete" v-for="item in fruit" :key="item.id">
          <view slot="content" class="wrap">
            <div class="radio-box">
              <i-radio i-class="radio1"  :value="value" :checked="checked" :color="checked?color:''"  @change="handleChecked"></i-radio>
            </div>

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

          </view>
        </i-swipeout>

      <i-modal title="删除确认" :actions="actions1"  :visible="visible"  @iclick="handleClick">
        <view>删除后无法恢复哦</view>
      </i-modal>
      <i-message id="message" />
    </div>

    <div class="bottom-fixed">
        <div class="left">
          <div class="selectAll">
            <i-radio  i-class="radio1" :value="value" :checked="checked" :color="checked?color:''"  @change="handleChecked"></i-radio>
            <p>全选</p>
          </div>
          <div class="total-box">
            <p class="total">总计:<span>￥1000.00</span></p>
            <p class="detail">总额:￥1000.00 立减:￥20.00</p>
          </div>

        </div>
        <div class="right">
          去结算 <span>(2件)</span>
        </div>
    </div>

  </div>
</template>

<script>
  import { $Message } from '../../../static/iView/dist/base/index'
  export default {
    data () {
      return {
        actions: [
          {
            name: '删除',
            color: '#fff',
            fontsize: '20',
            width: 100,
            icon: 'delete',
            background: '#E60026'
          }
        ],
        visible: false,
        actions1: [
          {
            name: '取消'
          },
          {
            name: '删除',
            color: '#ed3f14',
            loading: false
          }
        ],

        fruit: [{
          id: 1,
          name: '香蕉',
        }, {
          id: 2,
          name: '苹果'
        }, {
          id: 3,
          name: '西瓜'
        }, {
          id: 4,
          name: '葡萄',
        }],
        current: ['苹果', '葡萄'],
        color: '#E60026',
        checked: false,
        count:1
      }
    },
    methods: {
      handleFruitChange({mp: { detail = {} }}) {
        console.log(detail)
        const index = this.current.indexOf(detail.value);
        index === -1 ? this.current.push(detail.value) : this.current.splice(index, 1);
      },
      handleChecked(){
        console.log("ok");
        this.checked = !this.checked
      },
      handleCountChange({mp: { detail}}) {
        this.count = detail.value
      },
      handlerDelete: function () {
        this.visible = true
      },
      handleClick: function ({mp: { detail }}) {
        console.log( {detail})
        if (detail.index === 0) {
          this.visible = false
        } else {
          const action = [...this.actions1]
          action[1].loading = true
          this.actions1 = action

        setTimeout(() => {
          action[1].loading = false;
          this.visible = false
          this.actions1 = action
          $Message({
            content: '删除成功！',
            type: 'success'
          });
        }, 2000);
        }
      }
    }
  }
</script>

<style  lang="scss">
  @import '../../assets/style/common';

  .gray-box{
    height: 40rpx;
    background-color: #f7f7f7;
    border-bottom: 1px solid #e5e5e5;
  }
  .center-box{
    padding-bottom: 96rpx;
    .wrap{
      display: flex;
      /*flex-flow: row nowrap ;*/
      /*justify-content: flex-start;*/
      .radio-box{
        width: 60rpx;
        padding: 60rpx 10rpx 20rpx 0;
        .radio1 {
          view{
            padding: 0 !important;
          }
        }
      }

      .content-box{
        flex: 1;
        /*width: 400rpx;*/
        height: 220rpx;
        position: relative;

        .img-box{
          width: 150rpx;
          height: 150rpx;
          background-image: url("http://img02.tooopen.com/images/20150928/tooopen_sy_143912755726.jpg");
          background-size: cover;
          /*float: left;*/
          margin-right: 20rpx;
        }
        .desc-box{
          position: absolute;
          left: 160rpx;
          top: 0;
          /*line-height: 50rpx;*/

          .title{
            width: 100%;
            overflow:hidden;
            text-overflow:ellipsis;
            display:-webkit-box;
            -webkit-box-orient:vertical;
            -webkit-line-clamp:2;
          }
          .subTitle{
            color: #999;
            font-size: 24rpx;
            margin-top: 20rpx;
          }


        }

        .price{
          color: #d24844;
          font-size: 26rpx;
          position: absolute;
          left: 160rpx;
          bottom: 0;
          span{
            font-size: 40rpx;
          }
        }
        .count-box{
          position: absolute;
          right: 0;
          bottom: 0;
        }
      }
    }
  }


  .bottom-fixed{
    width: 100%;
    height: 96rpx;
    position: fixed;
    background-color: white;
    border-top: 1px solid #ddd;
    bottom: 0;
    .left{
      width: 70%;
      height: 100%;
      float: left;
      position: relative;

      .selectAll{
        position: absolute;
        left: 20rpx;
        top: 10rpx;
        font-size: 22rpx;
        color: #999;

        .radio1 {
          view{
            padding: 0 !important;
          }
        }
      }
      .total-box{
        font-size: 28rpx;
        text-align: right;
        position: absolute;
        right: 20rpx;
        top: 0;
        .total{
          margin-top: 15rpx;
          font-weight: 800;
          span{
            color: #d74a45;
          }

        }
        .detail{
          font-size: 22rpx;
          color: #9a9a9a;
        }
      }
    }
    .right{
      width: 30%;
      height: 100%;
      float: right;
      color: white;
      font-size: 30rpx;
      line-height: 96rpx;
      text-align: center;
      background-color: #E60026;
      span{
        font-size: 20rpx;
      }
    }
  }
  .i-cell{
    padding: 0 !important;
  }

</style>
