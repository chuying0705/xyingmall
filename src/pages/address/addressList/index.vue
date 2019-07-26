<template>
  <div class="address-box">
    <div class="address-item" v-for="i in 3" :key="i">
      <i-row i-class="price-row">
        <i-col span="4" i-class="col-left">
          <i-radio i-class="radio1"  :value="value" :checked="checked" :color="checked?'#d74a45':''"  @change="handleChecked"></i-radio>
        </i-col>
        <i-col span="15" i-class="col-center">
          <div class="desc-box">
            <div class="name">吴彦祖 13212341234</div>
            <div class="add">上海市虹口区北外滩溧阳路111号307</div>
          </div>
        </i-col>
        <i-col offset="1" span="4" i-class="col-right" @click="editAddress">编辑</i-col>
      </i-row>
    </div>
    <div class="btn"  @click="addAddress">
      新增收货地址
    </div>

  </div>
</template>

<script>
  export default {
    data () {
      return {
        checked: false

      }
    },

    methods: {
      handleChecked(){
        console.log("ok");
        this.checked = !this.checked
      },
      editAddress(){
        wx.navigateTo({
          url: '../editAddress/main'
        })
      },
      addAddress(){
        wx.navigateTo({
          url: '../addAddress/main'
        })
      }
    },

    created () {

    }
  }
</script>

<style scoped lang="scss">
  .address-box{
    width: 100%;
    height: 100vh;
    background-color: #f7f7f7;
    font-size: 30rpx;

    /deep/ .price-row{
      width: 100%;
      /*height: 100rpx;*/
      padding: 20rpx 30rpx;
      border-bottom: 1px solid #eee;
      background-color: white;

      .desc-box{

        .name{
          width: 100%;
          font-weight: 800;
        }
        .add{
          color: #666666;
          width: 100%;
          overflow:hidden;
          text-overflow:ellipsis;
          display:-webkit-box;
          -webkit-box-orient:vertical;
          -webkit-line-clamp:2;
        }
      }

      .col-right{
        color: #d74a45;
        font-size: 30rpx;
        margin-top: 40rpx;
      }

    }

    .btn{
      width: 100%;
      height: 96rpx;
      line-height: 96rpx;
      background-color: white;
      text-align: center;
      position: fixed;
      bottom: 0;
      left: 0;
      color: #d74a45;
      border-top: 1px solid #eee;
    }


  }




</style>
