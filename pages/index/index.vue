<template>
  <div class="content">

    <div style="position: relative;width: 160px;height: 160px;margin-top: 20px">
      <img :src="imgUrl" v-if="imgUrl" alt="" style="margin: 4px">
      <img :src="list[selectIndex]" alt="" style="width: 100%;height: 100%">
    </div>

    <slider :value="slider" @change="sliderChange" activeColor="#007aff" backgroundColor="#000000" block-color="#eee" show-value  style="width: 90%;margin-top: 18px"/>

    <uni-file-picker  ref="files" :auto-upload="false"/>
    <uni-file-picker
        v-model="imageValue"
        fileMediatype="image"
        @select="select"
        :limit="1"
        style="width: 100px;height: 50px"
        :auto-upload="false"
        @progress="progress"
        @success="success"
        @fail="fail">
      <div>选择文件</div>
    </uni-file-picker>

    <div @click="selectImage"
         style="margin-top: 10px;background: #007aff;border-radius: 4px;color: white;padding: 1px 4px">选择图片
    </div>

    <div
        style="display: flex;flex-wrap: wrap;justify-content: space-around;width: 100%;margin-top: 30px;overflow-y: auto">
      <img v-for="(item , index) in list" :key="index" :src="item" alt=""
           style="width: 70px;height:70px;margin: 7px 7px" @click="selectIndex=index">
    </div>

  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [],
      imageValue: [],
      imgUrl: '',
      slider:50,
      selectIndex: 0
    }
  },
  onLoad() {
    this.list = []
    for (let i = 0; i < 32; i++) {
      let img = require(`../img/${i}.png`)
      this.list.push(img)
    }

  },
  methods: {
    selectImage() {
    },
    // 获取上传状态
    select(e){
      console.log('选择文件：',e)
    },
    // 获取上传进度
    progress(e){
      console.log('上传进度：',e)
    },

    // 上传成功
    success(e){
      console.log('上传成功')
    },

    // 上传失败
    fail(e){
      console.log('上传失败：',e)
    },
    sliderChange(e) {
      console.log('value 发生变化：' + e.detail.value)
    }
  }
}
</script>

<style>
.content {
  display: flex;
  background-color: #f8f8f8;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}

</style>
