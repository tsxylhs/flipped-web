<template>
    <view style="background-image: linear-gradient(to bottom, #DcDCdc,#cd128f);">
    <view style=" height: 43vh; padding-top: 3px; width: 82vw; margin-left: 9vw;  border-radius: 170px 170px 170px 170px">
      <cover-image style="  border-radius: 170px 170px 170px 170px" src="https://flipped.lncios.cn/xiaoyuan.jpg"  mode="aspectFill" />
    </view>
    <view style="height: 55vh; margin-top: 10px;">
      <uni-row>
					<uni-col :xs="20" :sm="6" :md="4" :lg="3" :xl="1">
						<view style=" color: white; margin-left: 4vw;">
             <text>青菜紫罗冬瓜 ♂ ♀</text></view>
					</uni-col>
					<uni-col :xs="4" :sm="6" :md="4" :lg="3" :xl="1">
						<view  style="color: white;">相册</view>
					</uni-col>
				</uni-row>
        <uni-row>
          <uni-col :xs="20" :sm="6" :md="4" :lg="3" :xl="1">
						<view style=" font-size:12px; color: white; margin-left: 4vw;">
             <text >18岁*广州*本科*市场营销</text></view>
					</uni-col>
        </uni-row>
        <view style="    border-radius: 30px 30px 30px 30px; height:10vh; width: 90vw; margin-left: 2.5vh; background-color: #CF83AD;">
            
        </view>
         <view style="margin-top: 5px;">
          <text style=" color: white; margin-left: 4vw;" >关于我</text>
          <view style="     height:10vh; width: 90vw; margin-left: 2.5vh; background-color: #CF83AD;">
            
          </view>
        </view>
        <view style="margin-top: 5px;">
          <text style=" color: white; margin-left: 4vw;" >他/她的动态</text>
          <view style="     height:10vh; width: 90vw; margin-left: 2.5vh; background-color: #CF83AD;">
            
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
						iconPath:'/static/shoucangguanzhu.png',
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
					success: function(res) {
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