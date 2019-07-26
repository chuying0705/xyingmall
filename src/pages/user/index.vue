<template>
  <div class="user-box">
    <div class="userinfo" >
      <div class="top-box">
        <img class="userinfo-avatar" v-if="userInfo.avatarUrl" :src="userInfo.avatarUrl" background-size="cover" />
      </div>
      <div class="userinfo-nickname">
        <div>{{userInfo.nickName}}</div>
      </div>
    </div>
    <div class="list-box">
      <i-cell-group>
        <i-cell title="订单管理" is-link url="/pages/orders/orderList/main"></i-cell>
        <i-cell title="地址管理" is-link url="/pages/address/addressList/main"></i-cell>
        <i-cell title="我的优惠券" is-link url="/pages/coupons/myCoupons/main"></i-cell>
        <i-cell title="关于" is-link url="/pages/about/main" ></i-cell>
      </i-cell-group>
    </div>

  </div>
</template>

<script>
  export default {
    data () {
      return {
        motto: 'Hello World',
        userInfo: {}
      }
    },

    methods: {
      getUserInfo () {
        // 调用登录接口
        wx.login({
          success: () => {
            wx.getUserInfo({
              success: (res) => {
                this.userInfo = res.userInfo
              }
            })
          }
        })
      },

    },

    created () {
      // 调用应用实例的方法获取全局数据
      this.getUserInfo()
    }
  }
</script>

<style scoped lang="scss">
  .user-box{
    width: 100vw;
    height: 100vh;
    background-color: #f5f5f5;

    .userinfo {
      display: flex;
      flex-direction: column;
      align-items: center;
      background-color: #fff;
      padding-bottom: 80rpx;


      .top-box{
        width: 100%;
        height: 120rpx;
        background-color: #E60026;
        position: relative;

        .userinfo-avatar {
          width: 128rpx;
          height: 128rpx;
          /*margin: 20rpx;*/
          border-radius: 50%;
          position: absolute;
          bottom: -64rpx;
          left: 50%;
          transform: translateX(-50%);
        }
      }
      .userinfo-nickname {
        color: #333;
        margin-top: 70rpx;
      }

    }
    .list-box{
      border-top: 1px solid #e5e5e5;
    }

  }







  .list-box{

  }
</style>
