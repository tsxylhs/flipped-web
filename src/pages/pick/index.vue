<template>
  <view style="background-image: linear-gradient(to bottom, #DcDCdc,#cd128f);">
    <view
      style=" height: 43vh; padding-top: 3px; width: 82vw; margin-left: 9vw;  border-radius: 170px 170px 170px 170px">
      <cover-image style="  border-radius: 170px 170px 170px 170px" src="https://flipped.lncios.cn/xiaoyuan.jpg"
        mode="aspectFill" />
    </view>
    <view style="height: 55vh; margin-top: 10px;">
      <uni-row>
        <uni-col :xs="20" :sm="6" :md="4" :lg="3" :xl="1">
          <view style=" color: white; margin-left: 4vw;">
            <text>青菜紫罗冬瓜 ♂ ♀</text>
          </view>
        </uni-col>
        <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
          <view style="color: white;">相册</view>
        </uni-col>
      </uni-row>
      <uni-row>
        <uni-col :xs="20" :sm="6" :md="4" :lg="3" :xl="1">
          <view style=" font-size:10px; color: white; margin-left: 4vw;">
            <text>18岁*广州*本科*市场营销</text>
          </view>
        </uni-col>
      </uni-row>
      <view
        style=" margin-top: 5px;    border-radius: 30px 30px 30px 30px; height:7vh; width: 90vw; margin-left: 2.5vh; background-color: #CF83AD;">
        <uni-row>
          <uni-col :xs="1" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 4vw;">
              <uni-icons type="color" color="white" size="16" />
            </view>
          </uni-col>
          <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 5vw;">
              <text>爱好:</text>
            </view>
          </uni-col>
          <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 0vw;">
              <text>撸铁</text>
            </view>
          </uni-col>
          <uni-col :xs="1" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 4vw;">
              <uni-icons type="wallet" color="white" size="16" />
            </view>
          </uni-col>
          <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 5vw;">
              <text>工作:</text>
            </view>
          </uni-col>
          <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 0vw;">
              <text>程序员</text>
            </view>
          </uni-col>
        </uni-row>
        <uni-row>
          <uni-col :xs="1" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 4vw;">
              <uni-icons type="starhalf" color="white" size="16" />
            </view>
          </uni-col>
          <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 5vw;">
              <text>星座:</text>
            </view>
          </uni-col>
          <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 0vw;">
              <text>巨蟹座</text>
            </view>
          </uni-col>
          <uni-col :xs="1" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 4vw;">
              <uni-icons type="pyq" color="white" size="16" />
            </view>
          </uni-col>
          <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 5vw;">
              <text>五行:</text>
            </view>
          </uni-col>
          <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 0vw;">
              <text>金木水火土</text>
            </view>
          </uni-col>
        </uni-row>
        <uni-row>
          <uni-col :xs="1" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 4vw;">
              <uni-icons type="location-filled" color="white" size="16" />
            </view>
          </uni-col>
          <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 5vw;">
              <text>地址:</text>
            </view>
          </uni-col>
          <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 0vw;">
              <text>山东 菏泽</text>
            </view>
          </uni-col>
          <uni-col :xs="1" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 4vw;">
              <uni-icons type="staff" color="white" size="16" />
            </view>
          </uni-col>
          <uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 5vw;">
              <text>家庭:</text>
            </view>
          </uni-col>
          <uni-col :xs="6" :sm="6" :md="4" :lg="3" :xl="1">
            <view style=" font-size:10px; color: white; margin-left: 0vw;">
              <text>独苗</text>
            </view>
          </uni-col>
        </uni-row>
      </view>
      <view style="margin-top: 5px;">
        <text style=" color: white; margin-left: 4vw;">关于我</text>
        <view style="height:10vh; width: 90vw; margin-left: 2.5vh; background-color: #CF83AD;">
          <scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper">
            <text style="color: white; font-size: 17px;">&nbsp&nbsp&nbsp&nbsp&nbsp创业公司三年的开发经验，上市公司两年开发经验。系统的使用过 Java
              ,Golang ，Vuejs 等开发语言，涉及到微信小程序，H5，pc 端开发，nginx 部署。RabbitMQ Redis MQTT Kafka 等消息中间件，熟练使用 ElementUi Vux Gin  Xorm SpringBoot等框架。熟练使用 Linux Docker等命令。</text>
          </scroll-view>
        </view>
      </view>
      <view style="margin-top: 5px;">
        <text style=" color: white; margin-left: 4vw;">动态</text>
        <view style="     height:10vh; width: 90vw; margin-left: 2.5vh; background-color: #CF83AD;">
          <text style="color:white">搁置</text>
        </view>
      </view>

      <uni-fab ref="fab" :pattern="pattern" :content="content" :horizontal="horizontal" :vertical="vertical"
        :direction="direction" @trigger="trigger" @fabClick="fabClick" />


    </view>
  </view>

</template>

<script>
export default {
  name: "pick",
  components: {},
  props: {},
  data() {
    return {
      directionStr: '垂直',
      horizontal: 'left',
      vertical: 'bottom',
      direction: 'horizontal',
      pattern: {
        color: '#cd128f',
        backgroundColor: '#fff',
        selectedColor: '#007AFF',
        buttonColor: '#cd128f',
        iconColor: '#fff',
      },
      content: [{
        iconPath: '/static/xihuan.png',
        selectedIconPath: '/static/xihuan.png',
        text: '喜欢',
        active: false
      },
      {
        iconPath: '/static/buxihuan.png',
        selectedIconPath: '/static/buxihuan.png',
        text: '不喜欢',
        active: false
      },
      {
        iconPath: '/static/shoucangguanzhu.png',
        selectedIconPath: '/static/shoucangguanzhu.png',
        text: '倾心',
        active: false
      }
      ]
    }
  },
  computed: {},
  methods: {
    trigger(e) {
      console.log(e)
      this.content[e.index].active = !e.item.active
      uni.showModal({
        title: '提示',
        content: `您${this.content[e.index].active ? '选中了' : '取消了'}${e.item.text}`,
        success: function (res) {
          if (res.confirm) {
            console.log('用户点击确定')
          } else if (res.cancel) {
            console.log('用户点击取消')
          }
        }
      })
    },
    fabClick() {
      uni.showToast({
        title: '点击了悬浮按钮',
        icon: 'none'
      })
    }
  },
  watch: {},

  // 页面周期函数--监听页面加载
  onLoad() { },
  // 页面周期函数--监听页面初次渲染完成
  onReady() { },
  // 页面周期函数--监听页面显示(not-nvue)
  onShow() { },
  // 页面周期函数--监听页面隐藏
  onHide() { },
  // 页面周期函数--监听页面卸载
  onUnload() { },
  // 页面处理函数--监听用户下拉动作
  // onPullDownRefresh() { uni.stopPullDownRefresh(); },
  // 页面处理函数--监听用户上拉触底
  // onReachBottom() {},
  // 页面处理函数--监听页面滚动(not-nvue)
  // onPageScroll(event) {},
  // 页面处理函数--用户点击右上角分享
  // onShareAppMessage(options) {},
} 
</script>

<style scoped>
.scroll-Y {
  height: 10vh;
}
</style>