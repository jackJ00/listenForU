<template>
	<view>
		<scroll-view :scroll-y="modalName==null" class="page" :class="modalName!=null?'show':''">
			<view class="cu-bar bg-white solid-bottom" >
				<view class="action">
					<text class="cuIcon-title text-orange "></text> 消息列表
				</view>
			</view>
			<view class="cu-list menu-avatar">
				<view class="cu-item" :class="modalName=='move-box-'+ index?'move-cur':''" v-for="(item,index) in fridensList" :key="index"
				 @touchstart="ListTouchStart" @touchmove="ListTouchMove" @touchend="ListTouchEnd" :data-target="'move-box-' + index"
				 @click="goChat">
					<view class="cu-avatar round lg"  >
						<image :src=item.icon style="width: 100%;height: 100%;border-radius: 50%;"></image>
						<view class="cu-tag badge" v-if="item.messageScreen">{{item.messageCount}}</view>
					</view>
					<view class="content">
						<view class="text-grey">{{item.name}}</view>
						<view class="text-gray text-sm flex">
							<view class="text-cut">
								<text class="cuIcon-infofill text-red  margin-right-xs"></text>
								{{item.message}}
							</view> 
						</view>
					</view>
					<view class="action">
						<view class="text-grey text-xs">{{item.messageTime}}</view>
						<view class="cu-tag round  sm" :class="[item.messageScreen?'bg-grey':'bg-red']" v-if="!item.messageScreen">{{item.messageCount}}</view>
						<view class="cuIcon-notice_forbid_fill text-gray" v-else></view>
					</view>
					<view class="move">
						<view class="bg-grey">置顶</view>
						<view class="bg-red">删除</view>
					</view>
				</view>
				
				
			</view>
			
		
		</scroll-view>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				modalName: null,
				skin: false,
				listTouchStart: 0,
				listTouchDirection: null,
				fridensList:[
					{
						name:'凯尔',
						icon:"https://ossweb-img.qq.com/images/lol/web201310/skin/big10001.jpg",
						message:'我已天理为凭，踏入这片荒芜，不再受凡人的枷锁遏制。我已天理为凭，踏入这片荒芜，不再受凡人的枷锁遏制。',
						messageTime:'22:20',
						messageCount:'5',
						messageScreen:1, //1屏蔽消息 0不屏蔽
					},
					{
						name:'伊泽瑞尔',
						icon:'',
						message:'等我回来一个打十个',
						messageTime:'22:20',
						messageCount:'1',
						messageScreen:0
					}
				]
			};
		},
		methods: {
			// ListTouch触摸开始
			ListTouchStart(e) {
				this.listTouchStart = e.touches[0].pageX
			},

			// ListTouch计算方向
			ListTouchMove(e) {
				this.listTouchDirection = e.touches[0].pageX - this.listTouchStart > 0 ? 'right' : 'left'
			},

			// ListTouch计算滚动
			ListTouchEnd(e) {
				if (this.listTouchDirection == 'left') {
					this.modalName = e.currentTarget.dataset.target
				} else {
					this.modalName = null
				}
				this.listTouchDirection = null
			},
			goChat(){
				uni.navigateTo({
					url:'/pages/chat/chatDetail'
				})
			}
		}
	}
</script>

<style>
	.page {
		height: 100Vh;
		width: 100vw;
	}

	.page.show {
		overflow: hidden;
	}

	.switch-sex::after {
		content: "\e716";
	}

	.switch-sex::before {
		content: "\e7a9";
	}

	.switch-music::after {
		content: "\e66a";
	}

	.switch-music::before {
		content: "\e6db";
	}
</style>
