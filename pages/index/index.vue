<template>
	<view class="evan-icons-show">
		<view class="evan-icons-show__block">
			<text class="evan-icons-show__block__label">基本用法：</text>
			<evan-icons type="glass"></evan-icons>
			<evan-icons type="music"></evan-icons>
			<evan-icons type="search"></evan-icons>
			<evan-icons type="envelope-o"></evan-icons>
		</view>
		<view class="evan-icons-show__block">
			<text class="evan-icons-show__block__label">自定义颜色：</text>
			<evan-icons type="glass" color="#00ff00"></evan-icons>
			<evan-icons type="music" color="#0000ff"></evan-icons>
			<evan-icons type="search" color="#ff00ff"></evan-icons>
			<evan-icons type="envelope-o" color="#ffff00"></evan-icons>
		</view>
		<view class="evan-icons-show__block">
			<text class="evan-icons-show__block__label">自定义大小：</text>
			<evan-icons type="glass" size="20"></evan-icons>
			<evan-icons type="music" size="30"></evan-icons>
			<evan-icons type="search" size="40"></evan-icons>
			<evan-icons type="envelope-o" size="50"></evan-icons>
		</view>
		<view class="evan-icons-show__block">
			<text class="evan-icons-show__block__label">点击事件：</text>
			<evan-icons @click="onIconClick(1)" type="glass"></evan-icons>
			<evan-icons @click="onIconClick(2)" type="music"></evan-icons>
			<evan-icons @click="onIconClick(3)" type="search"></evan-icons>
			<evan-icons @click="onIconClick(4)" type="envelope-o"></evan-icons>
		</view>
		<view class="evan-icons-show__block vertical">
			<text class="evan-icons-show__block__label">全部图标：</text>
			<view class="evan-icons-show__block__list">
				<view class="evan-icons-show__block__list__item" v-for="(item,index) in iconArray" :key="index">
					<evan-icons :type="item"></evan-icons>
					<text class="evan-icons-show__block__list__item__text">{{item}}</text>
				</view>
			</view>
		</view>
		<!-- #ifdef APP-VUE -->
		<button class="evan-icons-show__button" @click="goNvue">nvue页面</button>
		<!-- #endif -->
	</view>
</template>

<script>
	import EvanIcons from '@/components/evan-icons/evan-icons.vue'
	import icons from '@/components/evan-icons/icons.js'
	export default {
		components: {
			EvanIcons
		},
		computed: {
			iconArray() {
				return Object.keys(icons)
			}
		},
		data() {
			return {
				title: 'Hello'
			}
		},
		onLoad() {

		},
		methods: {
			onIconClick(index) {
				uni.showToast({
					title: `点击了第${index}个icon`,
					icon: 'none'
				})
			},
			goNvue() {
				uni.navigateTo({
					url: '../app/app'
				})
			}
		}
	}
</script>

<style lang="scss">
	.evan-icons-show {
		&__button {
			position: absolute;
			right: 10px;
			top: 10px;
		}

		&__block {
			margin-bottom: 10px;

			&.vertical {
				display: flex;
				flex-direction: column;
			}

			&__label {
				font-size: 12px;
				color: #333;
			}

			&__list {
				display: flex;
				flex-wrap: wrap;

				&__item {
					display: flex;
					flex-direction: column;
					align-items: center;
					justify-content: center;
					margin-top: 6px;
					width: 25%;

					&__text {
						font-size: 12px;
						color: #333;
						margin-top: 6px;
					}
				}
			}
		}
	}
</style>
