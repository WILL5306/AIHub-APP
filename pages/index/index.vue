<template>
	<view class="container" :class="{ 'dark-theme': isDarkMode }">
		
		<view class="header-row">
			<view class="header-text">
				<text class="app-title">全能 AI 助手</text>
				<text class="app-desc">Designed By XZJ</text>
			</view>
			
			<view class="theme-btn" @click="toggleTheme">
				<text class="theme-icon">{{ isDarkMode ? '☀️' : '🌙' }}</text>
			</view>
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
						<text class="card-name" :style="{color: isDarkMode ? '#fff' : item.color}">{{ item.name }}</text>
						<text class="card-tag">{{ item.tag }}</text>
					</view>
				</view>

				<text class="go-icon" :style="{color: isDarkMode ? '#aaa' : item.color}">进入 ></text>
			</view>
		</view>

	</view>
</template>

<script>
	export default {
		data() {
			return {
				// 默认模式：false 代表浅色，true 代表深色
				isDarkMode: false,
				
				aiList: [
					{
						name: 'DeepSeek',
						tag: '深度求索 | 代码与推理强者',
						url: 'https://chat.deepseek.com',
						color: '#4e6ef2',
						icon: '/static/deepseek.png' 
					},
					{
						name: '豆包',
						tag: '字节跳动 | 语音与全能助手',
						url: 'https://www.doubao.com',
						color: '#307BF6',
						icon: '/static/doubao.png'
					},
					{
						name: 'Kimi 智能助手',
						tag: '月之暗面 | 长文档分析',
						url: 'https://kimi.moonshot.cn',
						color: '#333333',
						icon: '/static/kimi.png'
					},
					{
						name: '腾讯元宝',
						tag: '腾讯混元 | 微信生态集成',
						url: 'https://yuanbao.tencent.com',
						color: '#0052d9',
						icon: '/static/yuanbao.png'
					},
					{
						name: '通义千问',
						tag: '阿里巴巴 | 全能型助手',
						url: 'https://tongyi.aliyun.com',
						color: '#6e45e2',
						icon: '/static/tongyi.png'
					},
					{
						name: 'ChatGPT',
						tag: 'OpenAI | 需科学网络',
						url: 'https://chatgpt.com',
						color: '#10a37f',
						icon: '/static/chatgpt.png'
					},
					{
						name: 'Gemini',
						tag: 'Google | 需科学网络',
						url: 'https://gemini.google.com',
						color: '#9B59B6',
						icon: '/static/gemini.png'
					},
					{
						name: 'Copilot',
						tag: 'Microsoft | 需科学网络',
						url: 'https://copilot.microsoft.com',
						color: '#E17055',
						icon: '/static/copilot.png'
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
			},
			// 切换主题的方法
			toggleTheme() {
				this.isDarkMode = !this.isDarkMode;
				
				// (可选) 动态修改顶部导航栏颜色，让它也跟着变黑
				if (this.isDarkMode) {
					uni.setNavigationBarColor({
						frontColor: '#ffffff', // 顶部时间电量文字变白
						backgroundColor: '#121212' // 顶部背景变黑
					})
				} else {
					uni.setNavigationBarColor({
						frontColor: '#000000', // 顶部时间电量文字变黑
						backgroundColor: '#f7f8fa' // 顶部背景变灰白
					})
				}
			}
		}
	}
</script>

<style>
	/* 页面根样式 */
	page { 
		/* 移除原来的背景色，交给 container 控制 */
		background-color: transparent; 
	}
	
	/* 默认容器样式 (浅色模式) */
	.container { 
		padding: 20px; 
		min-height: 100vh; /* 铺满全屏 */
		background-color: #f7f8fa; 
		transition: background-color 0.3s; /* 颜色切换时的过渡动画 */
	}

	/* 头部左右布局 */
	.header-row {
		margin-top: 20px;
		margin-bottom: 25px;
		display: flex;
		justify-content: space-between; /* 左右分开 */
		align-items: center;
	}
	
	.app-title { font-size: 26px; font-weight: 900; color: #333; display: block; margin-bottom: 4px; transition: color 0.3s;}
	.app-desc { font-size: 13px; color: #999; letter-spacing: 1px;}

	/* 切换按钮样式 */
	.theme-btn {
		width: 40px;
		height: 40px;
		background-color: #eee;
		border-radius: 50%;
		display: flex;
		justify-content: center;
		align-items: center;
		box-shadow: 0 2px 5px rgba(0,0,0,0.1);
	}
	.theme-icon { font-size: 20px; }

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
		transition: all 0.3s; /* 所有属性都带动画 */
	}
	.card:active { transform: scale(0.98); }

	.card-left { display: flex; align-items: center; }
	
	.card-logo {
		width: 44px;
		height: 44px;
		margin-right: 15px;
		border-radius: 10px;
		background-color: #f9f9f9; 
	}

	.card-info { display: flex; flex-direction: column; }
	.card-name { font-size: 17px; font-weight: bold; margin-bottom: 4px; transition: color 0.3s; }
	.card-tag { font-size: 12px; color: #aaa; }
	.go-icon { font-size: 13px; font-weight: bold; opacity: 0.8; }

	/* ============================== */
	/* 🌑 深色模式样式 (Dark Mode)     */
	/* ============================== */
	
	/* 背景变深黑 */
	.container.dark-theme {
		background-color: #121212;
	}

	/* 标题变白 */
	.dark-theme .app-title {
		color: #ffffff;
	}

	/* 按钮变暗 */
	.dark-theme .theme-btn {
		background-color: #333;
		box-shadow: 0 2px 5px rgba(255,255,255,0.1);
	}

	/* 卡片变深灰 */
	.dark-theme .card {
		background-color: #1e1e1e;
		border-color: #333;
		box-shadow: none;
	}

	/* 图标背景变暗 */
	.dark-theme .card-logo {
		background-color: #2c2c2c;
		opacity: 0.9;
	}
</style>