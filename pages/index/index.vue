<template>
	<view class="content">
		<img :src="url" alt="" style="object-fit: cover"/>
  </view>
</template>

<script>
	export default {
		data() {
			return {
				title: 'Hello',
        url:'https://7a68-zhuzhu-release-8gntzk0r8745383d-1253927436.tcb.qcloud.la/%E5%BE%AE%E4%BF%A1%E5%9B%BE%E7%89%87_20211117142858.jpg?sign=87d42c48505856200d00b72327a9ca3d&t=1637156550'
			}
		},
		onLoad() {

		},
		methods: {

		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

</style>
