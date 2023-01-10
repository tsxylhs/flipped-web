<template>
  <view class="content">
    <scroll-view class="chat" scroll-y="true" scroll-with-animation="true" :scroll-into-view="scrollToView">
      <view class="chat-main" :style="{ paddingBottom: inputh + 'px' }">
        <view class="chat-ls" v-for="(item, index) in unshiftmsg" :key="index" :id="'msg' + index">
          <view class="chat-time" v-if="item.createTime != ''">{{ changeTime(item.createTime) }}</view>
          <view class="msg-m msg-left" v-if="item.sendName == friendName">
            <image @click="getMessage(item.sendName,'showLeft')" class="user-img" src="../../static/queqiao-active.png"></image>
            <view>
              <uni-row>
                <view>{{ item.sendName }}</view>
              </uni-row>
              <uni-row>
                <view class="message" v-if="item.TextType == 0">
                  <!-- 文字 -->
                  <view class="msg-text">{{ item.sendText }}</view>
                </view>
                <view class="message" v-if="item.TextType == 1" @tap="previewImg(item.sendText)">
                  <!-- 图像 -->
                  <image :src="item.sendText" class="msg-img" mode="widthFix"></image>
                </view>
                <view class="message" v-if="item.TextType == 2" @tap="playVoice(item.sendText.voice)">
                  <!-- 音频 -->
                  <view class="msg-text voice" :style="{ width: item.sendText.time * 4 + 'rpx' }">
                    <image src="../../static/yuyin1.png" class="voice-img"></image>
                    {{ item.sendText.time }}″
                  </view>
                </view>
                <view class="message" v-if="item.TextType == 3" @tap="openLocation(item.sendText)">
                  <!-- 位置 -->
                  <view class="msg-map">
                    <view class="map-name">{{ item.sendText.name }}</view>
                    <view class="map-address">{{ item.sendText.address }}</view>
                    <!-- 如果map不起作用，就可以直接用一张图片去替代 -->
                    <map class="map" :longitude="item.sendText.longitude" :latitude="item.sendText.latitude"
                      :markers="covers(item.sendText)"></map>
                  </view>
                </view>
              </uni-row>
            </view>

          </view>
          <view class="msg-m msg-right" v-if="item.sendName != friendName">
            <image class="user-img" src="../../static/queqiao-active.png"></image>
            <view class="message" v-if="item.TextType == 0">
              <view class="msg-text">{{ item.sendText }}</view>
            </view>
            <view class="message" v-if="item.TextType == 1" @tap="previewImg(item.sendText)">
              <image :src="item.sendText" class="msg-img" mode="widthFix"></image>
            </view>
            <view class="message" v-if="item.TextType == 2" @tap="playVoice(item.sendText.voice)">
              <!-- 音频 -->
              <view class="msg-text voice" :style="{ width: item.sendText.time * 4 + 'rpx' }">
                {{ item.sendText.time }}″
                <image src="../../static/yuyin1.png" class="voice-img"></image>
              </view>
            </view>
            <view class="message" v-if="item.TextType == 3" @tap="openLocation(item.sendText)">
              <!-- 位置 -->
              <view class="msg-map">
                <view class="map-name">{{ item.sendText.name }}</view>
                <view class="map-address">{{ item.sendText.address }}</view>
                <map class="map" :longitude="item.sendText.longitude" :latitude="item.sendText.latitude"
                  :markers="covers(item.sendText)"></map>
              </view>
            </view>
          </view>
        </view>
      </view>
    </scroll-view>
    <uni-drawer  class="drawer" ref="showLeft" mode="left" :width="280" @change="change($event,'showLeft')">
					<view class="close">
						<button @click="closeDrawer('showLeft')"><text class="word-btn-white">关闭Drawer</text></button>
					</view>
          <view> 消息人信息 </view>
	</uni-drawer>
  </view>
  <view>
  <submit @inputs="inputs" @heights="heights"></submit>
</view>

</template>

<script>
import dateTime from '../../common/dateTime.js';
import submit from '../chat/chat.vue';
//音频
const innerAudioContext = uni.createInnerAudioContext();
export default {

  name: "chatIndex",
  components: {submit },
  props: {},
  data() {
    return {
      showRight: false,
				showLeft: false,
      friendName: "青菜",
      msg: [
      ],
      // 反转数据接收
      unshiftmsg: [{
        "sendName": "青菜",
        "receviceName": "゛时光い",
        "sendText": {
          "address": "上海市闵行区莲花路425弄",
          "latitude": 31.146769,
          "longitude": 121.40569,
          "name": "莲花公寓",
        },
        "createTime": "2022-01-06 12:40:12",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 3
      }, {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": {
          "voice": "时光匆匆流过",
          "time": 2 //秒
        },
        "createTime": "2022-01-06 12:22:12",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 2
      }, {
        "sendName": "青菜",
        "receviceName": "゛时光い",
        "sendText": {
          "voice": "时光匆匆流过",
          "time": 60 //秒
        },
        "createTime": "2022-01-06 12:00:12",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 2
      }, {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "江湖笑",
        "createTime": "2022-01-03 12:22:12",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 0
      },
      {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "情愿了",
        "createTime": "2022-01-02 12:22:07",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 0
      },
      {
        "sendName": "青菜",
        "receviceName": "青菜",
        "sendText": "道不尽红尘恋",
        "createTime": "2021-12-19 12:22:03",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 0
      },
      {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "喝着相同的水",
        "createTime": "2021-12-19 12:21:58",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 0
      },
      {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "https://flipped.lncios.cn/xiaoyuan.jpg",
        "createTime": "2021-12-19 12:21:54",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 1
      },
      {
        "sendName": "青菜",
        "receviceName": "゛时光い",
        "sendText": "https://flipped.lncios.cn/xiangcun.jpg",
        "createTime": "2021-12-19 12:21:48",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 1
      },
      {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "不醉不罢休",
        "createTime": "2021-12-19 12:21:42",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 0
      },
      {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "https://flipped.lncios.cn/shechu.jpg",
        "createTime": "2021-12-19 11:02:18",
        "updateTime": null,
        "chatmState": 1,
        "TextType": 1
      }, {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": "诉不完人间愿",
        "createTime": "2021-12-18 20:37:03",
        "updateTime": null,
        "chatmState": 0,
        "TextType": 0
      }],
      imgMsg: [],
      scrollToView: '',
      oldTime: new Date(),
      inputh: '60',

    }
  },
  computed: {},
  methods: {

    confirm() {},
			// 打开窗口

			// 关闭窗口
			closeDrawer(e) {
				this.$refs[e].close()
			},
			// 抽屉状态发生变化触发
			change(e, type) {
				console.log((type === 'showLeft' ? '左窗口' : '右窗口') + (e ? '打开' : '关闭'));
				this[type] = e
			},
		// app端拦截返回事件 ，仅app端生效
		onBackPress() {
			if (this.showRight || this.showLeft) {
				this.$refs.showLeft.close()
				this.$refs.showRight.close()
				return true
			}
		},
    getMessage(id,e){
      this.$refs[e].open();
      uni.showToast({
            title: '点击了弹层按钮'+id,
            icon: 'none'
          })
    },
    changeTime(date) {
      return dateTime.dateTime1(date);
    },
    // 进行图片的预览
    previewImg(e) {
      let index = 0;
      for (let i = 0; i < this.imgMsg.length; i++) {
        if (this.imgMsg[i] == e) {
          index = i;
        }
      }
      console.log("index", index)
      // 预览图片
      uni.previewImage({
        current: index,
        urls: this.imgMsg,
        longPressActions: {
          itemList: ['发送给朋友', '保存图片', '收藏'],
          success: function (data) {
            console.log('选中了第' + (data.tapIndex + 1) + '个按钮,第' + (data.index + 1) + '张图片');
          },
          fail: function (err) {
            console.log(err.errMsg);
          }
        }
      });
    },
    //音频播放
    playVoice(e) {
      innerAudioContext.src = e;
      innerAudioContext.onPlay(() => {
        console.log('开始播放');
      });
    },
    //地图定位
    covers(e) {
      let map = [{
        latitude: e.latitude,
        longitude: e.longitude,
        iconPath: '../../../static/logo.png'
      }]
      return (map);
    },
    //跳转地图信息
    openLocation(e) {
      uni.openLocation({
        latitude: e.latitude,
        longitude: e.longitude,
        name: e.name,
        address: e.address,
        success: function () {
          console.log('success');
        }
      });
    },
    //接受输入内容
    inputs(e) {
      //时间间隔处理
      let data = {
        "sendName": "゛时光い",
        "receviceName": "青菜",
        "sendText": e.message,
        "createTime": new Date(),
        "updateTime": new Date(),
        "chatmState": 1,
        "TextType": e.type
      };
      // 发送给服务器消息
      // onSendWS(JSON.stringify(data));

      this.unshiftmsg.push(data);
      // 跳转到最后一条数据 与前面的:id进行对照
      this.$nextTick(function () {
        this.scrollToView = 'msg' + (this.unshiftmsg.length - 1)
      })
      if (e.type == 1) {
        this.imgMsg.push(e.message);
      }
      console.log(e)
    },
    //输入框高度
    heights(e) {
      console.log("高度:", e)
      this.inputh = e;
      this.goBottom();
    },
    // 滚动到底部
    goBottom() {
      this.scrollToView = '';
      this.$nextTick(function () {
        this.scrollToView = 'msg' + (this.unshiftmsg.length - 1)
      })
    }
  },
  watch: {},

  // 页面周期函数--监听页面加载
  onLoad() { },
  // 页面周期函数--监听页面初次渲染完成
  onReady() { },
  // 页面周期函数--监听页面显示(not-nvue)
  onShow() {
    for (var i = 0; i < this.msg.length; i++) {
      //时间间隔处理
      if (i < this.msg.length - 1) { //这里表示头部时间还是显示一下
        let t = dateTime.spaceTime(this.oldTime, this.msg[i].createTime);
        if (t) {
          this.oldTime = t;
        }
        this.msg[i].createTime = t;
      }
      // 获取图片，为下面的预览做准备
      if (this.msg[i].TextType == 1) {
        this.imgMsg.unshift(this.msg[i].sendText)
      }
      this.unshiftmsg.unshift(this.msg[i]);
    }
    // 跳转到最后一条数据 与前面的:id进行对照
    this.$nextTick(function () {
      this.scrollToView = 'msg' + (this.unshiftmsg.length - 1)
    })
  },
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

<style lang="scss">

.example-body {
	padding: 10px;
}
.scroll-view {
	/* #ifndef APP-NVUE */
	width: 100%;
	height: 100%;
	/* #endif */
	flex:1
}
// 处理抽屉内容滚动
.scroll-view-box {
	flex: 1;
	position: absolute;
	top: 0;
	right: 0;
	bottom: 0;
	left: 0;
}
.drawer{

}
.info {
	padding: 15px;
	color: #666;
}

.info-text {
	font-size: 14px;
	color: #666;
}
.info-content {
	padding: 5px 15px;
}
.close {
	padding: 10px;
  margin-top: 12vh;
}

.chat {
  height: 90vh;

  .chat-main {
    padding-left: 32rpx;
    padding-right: 32rpx;
    padding-top: 20rpx;
    // padding-bottom: 120rpx;  //获取动态高度
    display: flex;
    flex-direction: column;
  }

  .chat-ls {
    .chat-time {
      font-size: 24rpx;
      color: rgba(39, 40, 50, 0.3);
      line-height: 34rpx;
      padding: 10rpx 0rpx;
      text-align: center;
    }

    .msg-m {
      display: flex;
      padding: 20rpx 0;

      .user-img {
        flex: none;
        width: 80rpx;
        height: 80rpx;
        border-radius: 20rpx;
      }

      .message {
        flex: none;
        max-width: 480rpx;
      }

      .msg-text {
        font-size: 32rpx;
        color: rgba(39, 40, 50, 1);
        line-height: 44rpx;
        padding: 18rpx 24rpx;
      }

      .msg-img {
        max-width: 400rpx;
        border-radius: 20rpx;
      }

      .msg-map {
        background: #fff;
        width: 464rpx;
        height: 284rpx;
        overflow: hidden;

        .map-name {
          font-size: 32rpx;
          color: rgba(39, 40, 50, 1);
          line-height: 44rpx;
          padding: 18rpx 24rpx 0 24rpx;
          //下面四行是单行文字的样式
          display: -webkit-box;
          -webkit-box-orient: vertical;
          -webkit-line-clamp: 1;
          overflow: hidden;
        }

        .map-address {
          font-size: 24rpx;
          color: rgba(39, 40, 50, 0.4);
          padding: 0 24rpx;
          //下面四行是单行文字的样式
          display: -webkit-box;
          -webkit-box-orient: vertical;
          -webkit-line-clamp: 1;
          overflow: hidden;
        }

        .map {
          padding-top: 8rpx;
          width: 464rpx;
          height: 190rpx;
        }
      }

      .voice {
        // width: 200rpx;
        min-width: 100rpx;
        max-width: 400rpx;
      }

      .voice-img {
        width: 28rpx;
        height: 36rpx;
      }
    }

    .msg-left {
      flex-direction: row;

      .msg-text {
        margin-left: 16rpx;
        background-color: #fff;
        border-radius: 0rpx 20rpx 20rpx 20rpx;
      }

      .ms-img {
        margin-left: 16rpx;
      }

      .msh-map {
        margin-left: 16rpx;
        border-radius: 0rpx 20rpx 20rpx 20rpx;
      }

      .voice {
        text-align: right;

      }

      .voice-img {
        float: left;
        transform: rotate(180deg);
        width: 28rpx;
        height: 36rpx;
        padding-bottom: 4rpx;
      }
    }

    .msg-right {
      flex-direction: row-reverse;

      .msg-text {
        margin-right: 16rpx;
        background-color: rgba(255, 228, 49, 0.8);
        border-radius: 20rpx 0rpx 20rpx 20rpx;
      }

      .ms-img {
        margin-right: 16rpx;
      }

      .msh-map {
        margin-left: 16rpx;
        border-radius: 20rpx 0rpx 20rpx 20rpx;
      }

      .voice {
        text-align: left;

      }

      .voice-img {
        float: right;
        padding: 4rpx;
        width: 28rpx;
        height: 36rpx;
      }
    }
  }
}
</style>