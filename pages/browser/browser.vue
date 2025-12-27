<template>
	<view>
		<web-view :src="url"></web-view>
	</view>
</template>

<script>
	export default {
		data() {
			return { url: '' }
		},
		onLoad(options) {
			// 接收首页传过来的网址和标题
			if (options.url) {
				this.url = decodeURIComponent(options.url);
			}
			if (options.title) {
				// 修改顶部标题，把“加载中...”换成“DeepSeek”
				uni.setNavigationBarTitle({
					title: options.title
				});
			}
		}
	}
</script>