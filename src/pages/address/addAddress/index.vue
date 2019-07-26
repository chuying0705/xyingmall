<template>
  <div class="user-box">
    <div class="list-box">
      <!--<i-cell-group>-->
        <i-cell title="收货人">
          <input slot="footer" type="text" placeholder="姓名" maxlength="10"/>
        </i-cell>
        <i-cell title="联系方式">
          <input slot="footer" type="number" placeholder="手机号" maxlength="11"/>
        </i-cell>
        <i-cell title="所在地区">
          <div slot="footer">
            <picker mode="region" @change="bindRegionChange" :value="region" :custom-item="customItem">
              <view class="picker" :class="region.length === 0 ? 'color' : ''">
                {{region.length === 0? '--请选择--' : '当前选择：'+ region[0] + '，' + region[1]+'，' + region[2]}}
              </view>
            </picker>
            <div></div>
          </div>
        </i-cell>
        <i-cell title="详细地址">
          <input slot="footer" type="text" placeholder="详细地址需填写楼栋楼层或房间号信息"/>
        </i-cell>
        <i-cell title="地址标签">
          <div slot="footer">
            <i-tag
              v-for="(item, index) in tags"
              :key="i"
              @change="onChange"
              checkable="true"
              :name="index"
              :color="item.color"
              :checked="item.checked"
              type="border"
              style="margin-right:5px;">
              {{item.name}}
            </i-tag>
          </div>
        </i-cell>
      <!--</i-cell-group>-->
      <i-button @click="handleClick" i-class="btn">确认</i-button>
    </div>

    <div class="picker">

    </div>
  </div>
</template>

<script>
  export default {
    data () {
      return {
        region: [],
        customItem: '全部',
        tags : [
          {
            name : '家',
            checked : false,
            color : 'default'
          },
          {
            name : '公司',
            checked : false,
            color : 'default'
          },
          {
            name : '学校',
            checked : false,
            color : 'default'
          },
          {
            name : '其他',
            checked : false,
            color : 'default'
          }
        ]
      }
    },

    methods: {
      bindRegionChange: function ({mp:{detail}}) {
        console.log('picker发送选择改变，携带值为', detail)
        this.region = detail.value
      },

      onChange({mp:{detail}}){
        console.log(detail);
        // const detail = event.detail;
        this.tags[detail.name].checked = detail.checked

      }

    },

    created () {
    }
  }
</script>

<style scoped lang="scss">
  .user-box{
    width: 100vw;
    height: 100vh;
    background-color: #f7f7f7;

    .list-box{
      /deep/ ._i-cell{
        /*border-bottom: 1px solid #eee;*/
      }

      input, div{
        /*float: left;*/
        /*border: 1px solid red;*/
        width: 540rpx;
        text-align: left;

      }
      .color{
        color: #4e83f7;
      }
    }

  }

  .list-box{
    /deep/ .btn{
      background-color: #E60026 !important;
      color: white !important;
      border-radius: 10rpx;
    }


  }
</style>
