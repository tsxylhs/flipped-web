<template>
   <uni-list :border="true">
        <!-- 显示圆形头像 -->
         <view v-for="(item, index) in list" :key="id">
        <uni-list-chat clickable="true" @click="toDynamic(item)" :avatar-circle="true" :title="item.name"
          :avatar="item.url" :note="item.text" time="2020-02-02 20:20"
          badge-positon="left" :badge-text="item.count">
          <view class="chat-custom-right">
            <text class="chat-custom-text">刚刚</text>
            <!-- 需要使用 uni-icons 请自行引入 -->
            <uni-icons type="star-filled" color="#999" size="18"></uni-icons>
          </view>
        </uni-list-chat>
      </view>
    </uni-list>
</template>

<script>
export default {
  name: "focus",
  components: {},
  props: {},
  data() {
    return {
      list: [{
        id:"1",
        name:"小花",
        count:"2",
        text:"这里有个姑娘叫小花",
        url: 'https://flipped.lncios.cn/queqiao.png'
      }, {
        id:"2",
        name:"萝卜",
        count:"4",
        text:"这里有个姑娘叫小花",
        url: 'https://flipped.lncios.cn/queqiao-active.png'
      }, {
        id:"3",
        name:"青菜",
        count:"1",
        text:"这里有个姑娘叫小花",
        url: 'https://flipped.lncios.cn/xiaoyuan.jpg'
      }],

    
    }
  },
  computed: {},
  methods: {
    toDynamic(item){
      uni.navigateTo({
        url: "/pages/dynamic/index?type=1",
        animationType: 'fade-in',
      	animationDuration: 200
      })
    }
  },
  watch: {},

  // 页面周期函数--监听页面加载
  onLoad() {},
  // 页面周期函数--监听页面初次渲染完成
  onReady() {},
  // 页面周期函数--监听页面显示(not-nvue)
  onShow() {},
  // 页面周期函数--监听页面隐藏
  onHide() {},
  // 页面周期函数--监听页面卸载
  onUnload() {},
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

<style scoped></style>