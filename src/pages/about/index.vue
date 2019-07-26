<template>
  <div class="about-box">
    <div>亲爱的顾客，您在小颖商城购物过程中，有遇到什么问题么？或是有什么意见或建议，请告诉我们哦~</div>
    <div>邮箱2430648783@qq.com</div>

  </div>


</template>

<script>

export default {
  data () {
    return {
      current: 'tab1',

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
  .about-box{
    padding: 40rpx 30rpx;
    div{

    }
  }


</style>
