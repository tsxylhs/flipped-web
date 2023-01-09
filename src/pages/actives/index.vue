<template>
<view class="content">
  <view class="card card-vh">
      <view class="plr20 fun-title ">
        <van-divider
          hairline
          contentPosition="center"
          customStyle="margin-top:0;color: #cd128f; border-color: #cd128f; font-size: 16px;"
          >实时签到人员(滚动)</van-divider
        >
      </view>
      <scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper">
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view style="color: coral;">青菜  2023年1月8号 12:00</view>
      <view>青菜  2023年1月8号 12:00</view>
      <view>青菜  2023年1月8号 12:00</view>
      <view>青菜  2023年1月8号 12:00</view>
    </scroll-view>
        

      </view>
  <view class="card">
      <view class="plr20 fun-title">
        <van-divider
          hairline
          contentPosition="center"
          customStyle="margin-top:0;color: #cd128f; border-color: #cd128f; font-size: 16px;"
          >活动相关
        </van-divider>
      </view>
      <view class="plr20 funs">
        <van-row gutter="20">
          <van-col span="8" v-for="(fun, idx) in funsConfig" :key="idx">
            <navigator class="fun-item" :url="fun.url">
              <view class="icon-container" :class="[`icon-${fun.bg}`]">
                <van-icon
                  :color="fun.color"
                  size="40px"
                  :name="fun.icon"
                ></van-icon>
              </view>
              <text class="text">{{ fun.text }}</text>
            </navigator>
          </van-col>
        </van-row>
      </view>
    </view>
  <view class="card">

      <view class="plr20 fun-title">
        <van-divider
          hairline
          contentPosition="center"
          customStyle="margin-top:0; color: #cd128f; border-color: #cd128f; font-size: 16px;"
          >参与签到
        </van-divider>
      </view>
      <view class="funs plr20">
        <van-row>
          <van-col span="12">
            <view class="fun-item" @click="handleScan">
              <view class="icon-bg-green icon-container">
                <van-icon color="#07c160" size="50px" name="scan"></van-icon>
              </view>
              <text class="text">扫码签到</text>
            </view>
          </van-col>
          <van-col span="12">
            <navigator class="fun-item" url="../locSign/locSign">
              <view class="icon-bg-blue icon-container">
                <van-icon
                  color="#1989fa"
                  size="50px"
                  name="location-o"
                ></van-icon>
              </view>
              <text class="text">定位签到</text>
            </navigator>
          </van-col>
        </van-row>
      </view>
    </view>

    <view class="card card-vh">
      <view class="plr20 fun-title ">
        <van-divider
          hairline
          contentPosition="center"
          customStyle="margin-top:0;color: #cd128f; border-color: #cd128f; font-size: 16px;"
          >活动地址</van-divider
        >
      </view>
      <view class="msg-map">
                <view class="map-name">{{ active.addr.name }}</view>
                <view class="map-address">{{ active.addr.address }}</view>
                <map class="map" :longitude="active.addr.longitude" :latitude="active.addr.latitude"
                  :markers="covers(active.addr)"></map>
              </view>
    </view>
    <van-toast id="van-toast" />   
</view>

</template>

<script>
export default {
  name: "actives",
  components: {},
  props: {},
  data() {
    return {
      active:{
        addr:{
          name:"上海市闵行区莲花路",
          address:"莲花公寓",
          latitude: 31.146769,
          longitude: 121.40569
        }
      },
     funsConfig : [
  {
    text: '报名参加',
    icon: 'friends-o',
    color: '#07c160',
    bg: 'green',
    url: '../activity/join/join'
  },
  {
    text: '报名人数(80)',
    icon: 'award-o',
    color: '#1989fa',
    bg: 'blue',
    url: '../activity/create/index'
  },
  {
    text: '活动详情',
    icon: 'setting-o',
    color: '#ee0a24',
    bg: 'red',
    url: '../activity/manage/manage'
  }
]
    }
  },
  computed: {},
  methods: {
    covers(e) {
      let map = [{
        latitude: e.latitude,
        longitude: e.longitude
      }]
      return (map);
    },
    handleScan () {
      uni.scanCode({
        onlyFromCamera: true,
        success: res => {
          Toast.loading({
            message: '签到中...',
            duration: 0, // 持续展示 toast
            forbidClick: true
          })
          if (res.scanType !== 'QR_CODE') {
            Toast.fail('不是二维码')
            return
          }
          try {
            const data = JSON.parse(res.result)
            const { type, qrcode } = data
            switch (type) {
              case 'sign':
                this.qrCodeSign(qrcode)
                break
            }
          } catch (e) {
            Toast.fail('不支持的二维码')
          }
        }
      })
    },
    qrCodeSign (qrcode) {
      this.$api.record
        .startRecord(SignMethod.qrCode, {
          qrcode
        })
        .then(() => {
          Toast.success('签到成功')
        })
        .catch(err => {
          const { code, data } = err
          if (code === StatusCode.record.notJoin) {
            Toast.success({
              message: ' 还未加入活动\n\n准备跳转加入',
              onClose: () => {
                this.changeAutoSign({
                  method: SignMethod.qrCode,
                  pwd: qrcode
                })
                uni.navigateTo({
                  url: `../activity/join/join?pwd=${data.pwd}`
                })
              }
            })
            return
          }
          let errMsg = ''
          switch (code) {
            case StatusCode.record.signOver:
              errMsg = '签到已结束'
              break
            case StatusCode.record.alreadySign:
              errMsg = '已经签过到了'
              break
            case StatusCode.record.invalidQRCode:
              errMsg = ' 二维码过期 \n\n请重新扫一扫'
              break
            default:
              errMsg = '签到失败'
          }
          Toast.fail(errMsg)
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

<style lang="scss">
.scroll-Y{
  height: 240rpx;
}
 .msg-map {
        background: #fff;
        width: 100%;
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
          width: 100%;
          height: 190rpx;
        }
      }
.content {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: primary;
  padding: 20rpx 30rpx;
  height: 100vh;
}
.card-vh{
  height: 44vh;
}
.plr20 {

  padding: 0 10rpx;
}
.card {
  background-color: #fff;
  width: 95%;
  border-radius: 16rpx;
  padding: 20rpx;
  box-shadow: 0 0 5rpx #ddd;
  margin-bottom: 20rpx;
}
.avatar-container {
  display: flex;
  align-items: center;
  position: relative;
  .avatar {
    border-radius: 50%;
    width: 130rpx;
    height: 130rpx;
    overflow: hidden;
  }
  .login {
    background-color: #fff;
    padding: 0;
    border: none;
    text-align: left;
    margin-left: 40rpx;
    flex-grow: 1;
    font-size: 1rem;
  }
  .login::after {
    border: none;
  }
  .info {
    text-align: center;
    font-size: 1.2rem;
    margin-left: 40rpx;
    .sex {
      margin-left: 10rpx;
    }
    .re-login {
      position: absolute;
      right: 20rpx;
      top: 0;
      bottom: 0;
      align-items: center;
      justify-content: center;
      display: flex;
    }
  }
}
.fun-item {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding-bottom: 10rpx;
  .icon-container {
    border-radius: 50%;
    padding: 30rpx;
  }
  .icon-bg-green {
    background-color: rgb(242, 245, 246);
  }
  .icon-bg-blue {
    background-color:  rgb(242, 245, 246);
  }
  .icon-bg-red {
    background-color: rgb(244, 100, 100);
  }
  .text {
    padding-top: 16rpx;
    font-size: 0.8rem;
    text-align: center;
  }
}

</style>