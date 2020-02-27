<template>
	<mescroll-uni class="dfvgdftyxe5r" ref="mescrollRef" height="90%" top="0"  @init="mescrollInit" :down="downOption" @down="downCallback" @up="upCallback">
		 
			<swiper class="jhgxeeerert" :indicator-dots="true" :autoplay="true" :circular="true" indicator-color="#F0BDC9"
			 indicator-active-color="#FF547B">
				<swiper-item v-for="sd in advertInfo">
					<view class="kjhhxeeett">
						<view class="yuyyhjxertaser">
							
							<image :src="sd.imageUrl" ></image>
						</view>
					</view>
				</swiper-item>
			</swiper>
			<view class="fz36 pd mt20">
				热门推荐
			</view>
			<scroll-view class="jinhxeeert dfrxeeert " :scroll-x="true">
				<view class="ccvrrtxeer pm20" v-for="sd in goodspage">
					<image :src="sd.imageUrl"
					 class="jhhnxeert"></image>
					<view class="dsfdsrrxewrer">
						<view class="xdrrrtxw dianer fz26 z3">
							{{sd.name}}
						</view>
						<view class="dddrrt red fz28 mt10 ">
							<text class="fz24">￥</text>{{sd.price/1000}}
						</view>
					</view>
				</view>
			</scroll-view>

			<view class="fz36 pd mt20">
				会员专区
			</view>
			<view class="btm mt20">
				<view class="mt10 fdgfdtxeertt">
					<view class="yuyyhjxert">
						<image :src="userinfo.photo" mode="widthFix"></image>
						<view class="lokjxeertt">
							<view class="cf fz30">
								{{userinfo.name}} | {{userinfo.position}}
							</view>
							<view class="fz40 cf">
								{{userinfo.companyName}}
							</view>
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
				advertInfo:'',
				dataList: [],
				userinfo:"",
				goodspage:""
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
			},
			// 上部滚动图⽚及链接
			async getadvertInfo(){
					this.advertInfo = await this.get("advertInfo/list",{code:"LINE"})
					this.advertInfo  = this.advertInfo.data
			},
			// 分类及商品列表 1是热⻔
			async getgoodspage(){
					this.goodspage = await this.get("goods/page",{type:1})
					this.goodspage  = this.goodspage.data.content
			},
			// 商城中的会员专区获取某个⽤户信息
			async getuserinfo(){
					this.userinfo = await this.get("user/170")
					this.userinfo  = this.userinfo.data
			}
			
			
		},
		onLoad() {
			
		},
		mounted() {
			this.getadvertInfo()
			this.getgoodspage()
			this.getuserinfo()
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
	.kjhhxeeett{
		padding: 20upx 40upx;
	}
	.yuyyhjxertaser{
		border-radius: 40upx;
		height: 380upx;
		overflow: hidden;
		position: relative;
	}
	.fdgfdtxeertt{
		height: 340upx;
		padding: 10upx 40upx;
	}
	.yuyyhjxert image{
		width: 100%;
		height: 100%;
	}
	
	.yuyyhjxert{
		border-radius: 40upx;
		height: 340upx;
		overflow: hidden;
		position: relative;
	}
	.lokjxeertt{
		position: absolute;
		left: 0;
		top: 0;
		width: 100%;
		padding: 40upx 30upx;
	}
	.fdgdfttdd{
		width: 25%;
		float: left;
	}
	.dsfsdtrdert{
		padding: 10upx 40upx;
	}
	.dsfsdtrdert image{
		border-radius:8upx;
	}
</style>
