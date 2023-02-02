<template>
	<view class="view_container">
		<view class="header">
			<u-avatar :src="src" shape="square" size="60"></u-avatar>
			<view class="userName">
				<view class="name">jackJ</view>
				<text>笑一个吧，功成名就不是目的</text>
			</view>
			<view class="arrow">
				<u-icon name="arrow-right" size="28"></u-icon>
			</view>
		</view>
		<view class="fit-content">
			<u-cell-group>
				<u-cell  title="夕阳无限好" arrow-direction="down">
					<u-icon slot="icon" size="32" name="search"></u-icon>
					<!-- <u-badge count="99" :absolute="false" slot="right-icon"></u-badge> -->
				</u-cell>
				<u-cell icon="setting-fill" title="设置"></u-cell>
				<u-cell icon="setting-fill" title="关于我们"></u-cell>
			</u-cell-group>
		</view>
		
	</view>
</template>

<script>
	export default {
		data() {
			return {
				src: 'http://pic2.sc.chinaz.com/Files/pic/pic9/202002/hpic2119_s.jpg'
			};
		}
	}
</script>

<style lang="scss">
.view_container{
	padding:0 30rpx;
	.header{
		display: flex;
		margin-top: 30rpx;
		position: relative;
		.userName{
			margin-left: 50rpx;
			.name{
				font-weight: bold;
				font-size: 32rpx;
				padding: 8rpx 0;
			}
		}
		.arrow{
			position: absolute;
			right: 0rpx;
			top:30rpx;
		}
	}
	.fit-content{
		margin-top: 100rpx;
	}
}
</style>
