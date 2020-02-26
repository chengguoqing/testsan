<template>
	<view>
		<view class="pd pt20">
			<view class="shurukser">
				<icon type="search" size="16" class="shuhhxeert"></icon>
				<input placeholder="输入你感兴趣的人或内容" class="shurunhxeert" />
			</view>
		</view>
		<swiper class="jhgxeeerert" :indicator-dots="true" :autoplay="true" :circular="true" indicator-color="#F0BDC9"
		 indicator-active-color="#FF547B">
			<swiper-item>
				<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/d8a1b44d-5526-45e4-af04-dd47f9c0e495.png"></image>
			</swiper-item>
			<swiper-item>
				<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/c4882181-7383-4f58-aa10-10eb677b4cb3.png"></image>
			</swiper-item>
		</swiper>
		<view class="pd mt20">
			<view class="dtitle">
				联盟空间
			</view>
			<scroll-view class="jinhxeeert" :scroll-x="true">
				<view class="jjbxwer" v-for="sd in 20">
					深圳总部
				</view>
			</scroll-view>

		</view>

		<view class="mt40">
			<view class="mt20 row cen">
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						最新活动
					</view>
				</view>
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						冬夏令营
					</view>
				</view>
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						海上运动
					</view>
				</view>
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						有氧营地
					</view>
				</view>
			</view>

			<view class="mt20 row cen">
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						轰趴BBQ
					</view>
				</view>
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						婚纱婚礼殿堂
					</view>
				</view>
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						笔记
					</view>
				</view>
				<view class="col">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/afbf8bbb-b84a-489f-acb5-360e41bff34c.png"
					 class="xseeerte"></image>
					<view class="fz24 z3">
						加入航海方程式
					</view>
				</view>
			</view>
		</view>

		<view class="mt40 pd">
			<view class="csdfrtxcwer">
				<view class="kjhjhbbjhgde aa " :class="dsfdsr==0?'act':''" @tap="dsfdsr=0">
					当前方程式
				</view>
				<view class="kjhjhbbjhgde" :class="dsfdsr==1?'act':''" @tap="dsfdsr=1">
					精彩回眸
				</view>
			</view>
		</view>

		<view class="mt20">
			<image v-for="sd in jhgdse" src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/4446e8a7-11d9-4b8b-ae4f-73421423ffe8.png"
			 class="w100" mode="widthFix"></image>
		</view>
		<uni-load-more :status="status" />
	</view>
</template>
<script>
	import uniLoadMore from '@/components/uni-load-more/uni-load-more.vue'
	export default {
		data() {
			return {
				dsfdsr: 0,
				jhgdse: 10,
				status: 'more' // loading
			}
		},
		components: {
			uniLoadMore
		},
		methods: {

		},
		onShareAppMessage: function(res) {
			// 来自页面内分享按钮
			return {
				title: "獨行工匠",
				path: "/pages/index/index"
			}
		},
		onReachBottom() {
			this.status = 'loading'
			setTimeout(a => {
				this.jhgdse += 10
				this.status = 'more'
			}, 2000)
		},
		onPullDownRefresh() {
			setTimeout(function() {
				uni.stopPullDownRefresh();
			}, 1000);
		},
		mounted() {

		},
	}
</script>
<style scoped>
	.jhgxeeerert {
		height: 680upx;
	}

	.jhgxeeerert image {
		width: 100%;
		height: 100%;
	}

	.jjbxwer {
		width: 160upx;
		height: 160upx;
		background: #EDEDED;
		border-radius: 10upx;
		line-height: 160upx;
		font-size: 30upx;
		text-align: center;
		display: inline-block;
		margin-right: 30upx;
	}



	.xseeerte {
		width: 110upx;
		height: 110upx;
	}

	.kjhjhbbjhgde {
		width: 240upx;
		display: inline-block;
		font-size: 28upx;
		color: #999;
		position: relative;
		margin-right: 30upx;
	}

	.kjhjhbbjhgde.act {
		color: #333;
		font-size: 40upx;
	}

	.csdfrtxcwer {
		position: relative;
	}

	.csdfrtxcwer::after {
		content: ' ';
		position: absolute;
		left: 240upx;
		top: 0;
		height: 40upx;
		top: 10upx;
		width: 2upx;
		background: #333;
	}
</style>
