<template>
<div>
  <img :src="url" alt="" style="object-fit: cover;width: 50px;height: 50px"/>
  <button open-type="getUserInfo" lang="zh_CN" @click="wxLogin">{{ title }}</button>
  <button @click="aaa">{{ // title }}</button>

</div>
</template>

<script>
export default {
  name: "UserInfo",
  data() {
    return{
      title: 'Hello',
      url: 'cloud://zhuzhu-release-2g12anrx02601be9.7a68-zhuzhu-release-2g12anrx02601be9-1253927436/login_img2.png'

    }
  },
  methods: {

    aaa(data) {
      uni.authorize({
        scope: 'scope.userInfo',
        success() {
          console.log('-----------1231312')
        }
      })
    },
    wxLogin(data) {
      // console.log('-------q-----',data)
      //
      // this.url=data.detail.userInfo.avatarUrl
      // this.title=data.detail.userInfo.nickName
      let _this = this
      uni.getUserProfile({
        desc: '123123123123',
        success: function (infoRes) {
          console.log('----：' + infoRes.userInfo.nickName);
          console.log('----：' + infoRes.userInfo.avatarUrl);
          _this.url = infoRes.userInfo.avatarUrl
        },
        fail(err) {
          console.info('------', err)
        }
      });
    },

  }

}
</script>

<style scoped>

</style>
