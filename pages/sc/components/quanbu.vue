<template>
	<mescroll-uni class="dfvgdftyxe5r" ref="mescrollRef" height="90%" top="0"  @init="mescrollInit" :down="downOption" @down="downCallback" @up="upCallback">
		 
			<swiper class="jhgxeeerert" :indicator-dots="true" :autoplay="true" :circular="true" indicator-color="#F0BDC9"
			 indicator-active-color="#FF547B">
				<swiper-item v-for="sd in 5">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/6c23e47b-585c-4d88-adbe-8bc4528527d0.png"></image>
				</swiper-item>
			</swiper>
			<view class="fz36 pd mt20">
				热门推荐
			</view>
			<scroll-view class="jinhxeeert dfrxeeert " :scroll-x="true">
				<view class="ccvrrtxeer pm20" v-for="sd in 20">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/ca225934-71dd-4bef-afc4-36d409b80ba9.jpg"
					 class="jhhnxeert"></image>
					<view class="dsfdsrrxewrer">
						<view class="xdrrrtxw dianer fz26 z3">
							六年老白茶 | 陈皮白茶，七年新会天马大红皮 - 沐心
						</view>
						<view class="dddrrt red fz28 mt10 ">
							<text class="fz24">￥</text>78
						</view>
					</view>
				</view>
			</scroll-view>

			<view class="fz36 pd mt20">
				会员专区
			</view>
			<view class="btm mt20">
				<view class="mt10" v-for="sd in 10">
					<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/27fdef9f-947f-45ce-8d76-2870247366e1.png"
					 class="w100" mode="widthFix"></image>
					<view class="row">
						<view class="col">
							<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/793e1907-d788-4a42-aa19-f383e83bbef7.png"
							 mode="widthFix" class="w100"></image>
						</view>
						<view class="col">
							<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/54413eb6-15e5-4150-abd0-e27d9109b885.png"
							 mode="widthFix" class="w100"></image>
						</view>
						<view class="col">
							<image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/0540308c-61a5-422e-be19-5bd505312bff.png"
							 mode="widthFix" class="w100"></image>
						</view>
					</view>
				</view>
			</view>
			</mescroll-uni>
</template>
<script>
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js";
	export default {
			mixins: [MescrollMixin], // 使用mixin (在main.js注册全局组件)
		data() {
			return {
				downOption: {
					auto: false //是否在初始化后,自动执行downCallback; 默认true
				},
				dataList: []
			}
		},
		components: {

		},
		methods: {
			/*下拉刷新的回调 */
			downCallback() {
				setTimeout(a=>{
					this.mescroll.resetUpScroll()
				},2000)
			},
			/*上拉加载的回调: 其中page.num:当前页 从1开始, page.size:每页数据条数,默认10 */
			upCallback(page) {
				setTimeout(a=>{
					this.mescroll.endSuccess();
				},2000)
			}
		},
		onLoad() {
			
		},
		mounted() {

		}
	}
</script>
<style scoped>
	.jhgxeeerert {
		height: 400upx;
	}

	.jhgxeeerert image {
		width: 100%;
		height: 100%;
	}

	.sdfrferet {
		width: 500upx;
		height: 500upx;
	}

	.ccvrrtxeer {
		width: 200upx;
		min-height: 200upx;
		display: inline-block;
		margin-left: 30upx;
		opacity: inherit;
		overflow: hidden;

		border-radius: 20upx;
		box-shadow: 0 2px 8px rgba(93, 113, 127, 0.08);
	}

	.dfrxeeert {
		border-top: 1px solid #F9F9FA;
		padding-top: 20upx;
	}

	.jhhnxeert {
		width: 100%;
		height: 200upx;
	}

	.dsfdsrrxewrer {
		padding-left: 20upx;
		padding-right: 20upx;
		padding-top: 10upx;
	}

	.xdrrrtxw {
		white-space: normal;
	}
	
	.dfvgdftyxe5r {
		height: 100%;
	}
</style>
