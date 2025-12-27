<template>
	<view class="container">
		
		<view class="header">
			<text class="app-title"> AI assistant</text>
			<text class="app-desc">Designed By XZJ</text>
		</view>

		<view class="grid-container">
			<view class="card" 
				  v-for="(item, index) in aiList" 
				  :key="index"
				  @click="openWeb(item)"
			>
				<view class="card-left">
					<image :src="item.icon" class="card-logo" mode="aspectFit"></image>
					
					<view class="card-info">
						<text class="card-name" :style="{color: item.color}">{{ item.name }}</text>
						<text class="card-tag">{{ item.tag }}</text>
					</view>
				</view>

				<text class="go-icon" :style="{color: item.color}">进入 ></text>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 使用 Google S2 服务获取高清图标，格式统一为 PNG
				aiList: [
					{
						name: 'DeepSeek',
						tag: '深度求索 | 代码与推理强者',
						url: 'https://chat.deepseek.com',
						color: '#4e6ef2',
						icon: 'https://www.google.com/s2/favicons?domain=chat.deepseek.com&sz=128'
					},
					// --- 新增：豆包 (放在第二个) ---
					{
						name: '豆包',
						tag: '字节跳动 | 语音与全能助手',
						url: 'https://www.doubao.com',
						color: '#307BF6', // 豆包蓝
						icon: 'https://www.google.com/s2/favicons?domain=www.doubao.com&sz=128'
					},
					// ---------------------------
					{
						name: 'Kimi',
						tag: '月之暗面 | 长文档分析',
						url: 'https://kimi.moonshot.cn',
						color: '#333333',
						icon: 'https://www.google.com/s2/favicons?domain=kimi.moonshot.cn&sz=128'
					},
					{
						name: '腾讯元宝',
						tag: '腾讯混元 | 微信生态集成',
						url: 'https://yuanbao.tencent.com',
						color: '#0052d9',
						icon: 'https://www.google.com/s2/favicons?domain=yuanbao.tencent.com&sz=128'
					},
					{
						name: '通义千问',
						tag: '阿里巴巴 | 全能型助手',
						url: 'https://tongyi.aliyun.com',
						color: '#6e45e2',
						icon: 'https://www.google.com/s2/favicons?domain=tongyi.aliyun.com&sz=128'
					},
					{
						name: 'ChatGPT',
						tag: 'OpenAI | 需科学网络',
						url: 'https://chatgpt.com',
						color: '#10a37f',
						icon: 'https://www.google.com/s2/favicons?domain=chatgpt.com&sz=128'
					},
					{
						name: 'Gemini',
						tag: 'Google | 需科学网络',
						url: 'https://gemini.google.com',
						color: '#9B59B6',
						icon: 'https://www.google.com/s2/favicons?domain=gemini.google.com&sz=128'
					},
					{
						name: 'Copilot',
						tag: 'Microsoft | 需科学网络',
						url: 'https://copilot.microsoft.com',
						color: '#E17055',
						icon: 'https://www.google.com/s2/favicons?domain=copilot.microsoft.com&sz=128'
					}
				]
			}
		},
		methods: {
			openWeb(item) {
				const targetUrl = encodeURIComponent(item.url);
				uni.navigateTo({
					url: `/pages/browser/browser?url=${targetUrl}&title=${item.name}`
				})
			}
		}
	}
</script>

<style>
	/* 页面整体背景 */
	page { background-color: #f7f8fa; }
	.container { padding: 20px; }

	/* 头部样式 */
	.header { margin-top: 20px; margin-bottom: 25px; padding-left: 5px;}
	.app-title { font-size: 26px; font-weight: 900; color: #333; display: block; margin-bottom: 8px; }
	.app-desc { font-size: 13px; color: #999; letter-spacing: 1px;}

	/* 列表容器 */
	.grid-container { display: flex; flex-direction: column; gap: 16px; }

	/* 卡片样式 */
	.card {
		background-color: #ffffff;
		padding: 18px;
		border-radius: 16px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		box-shadow: 0 8px 20px rgba(0,0,0,0.03);
		border: 1px solid #f0f0f0;
		transition: transform 0.1s;
	}
	.card:active { transform: scale(0.98); background-color: #fcfcfc; }

	/* 左侧布局：图标+文字 */
	.card-left {
		display: flex;
		align-items: center;
	}

	/* 图标样式 */
	.card-logo {
		width: 44px;
		height: 44px;
		margin-right: 15px;
		border-radius: 10px;
		background-color: #f9f9f9; 
	}

	/* 文字信息 */
	.card-info { display: flex; flex-direction: column; }
	.card-name { font-size: 17px; font-weight: bold; margin-bottom: 4px; }
	.card-tag { font-size: 12px; color: #aaa; }
	
	/* 右侧箭头 */
	.go-icon { font-size: 13px; font-weight: bold; opacity: 0.8; }
</style>