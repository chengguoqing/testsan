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
			<swiper-item v-for="sd in banners">
				<view class="kjhhxeeett">
					<view class="yuyyhjxert">
						<image :src="sd.photo"></image>
						<view class="lokjxeertt">
							<view class="cf fz30">
								{{sd.name}} | {{sd.position}}
							</view>
							<view class="fz40 cf">
								{{sd.companyName}}
							</view>
						</view>
					</view>
				</view>
				<!-- <image src="https://duxinggj-2018-1251133427.cos.ap-guangzhou.myqcloud.com/d8a1b44d-5526-45e4-af04-dd47f9c0e495.png"></image> -->
			</swiper-item>
			
		</swiper>
		<view class="pd mt20">
			<view class="dtitle">
				联盟空间
			</view>
			<scroll-view class="jinhxeeert" :scroll-x="true">
				<view class="jjbxwer dian " v-for="sd in company">
					<image :src="sd.logo" class="kkjjeer yj cz "></image>
					<view class="mt20 fz20 z3">
						{{sd.address}}
					</view>
					<view class=" fz28 z3">
							{{sd.name}}
					</view>
					<view class="mt20 fz20 z3">
						{{sd.linkName}}
					</view>
					<!-- <view class="pr cf">
						{{sd.name}}
					</view>
					<image :src="sd.logo"></image> -->
				</view>
			</scroll-view>

		</view>

		<view class="mt40">
			<view class="mt20  cen">
				<view class="fdgdfttdd" v-for="sd in catalogue">
					<image :src="sd.resourceIcon" class="xseeerte"></image>
					<view class="fz24 z3">
						{{sd.name}}
					</view>
				</view>
				<view class="qc">
					
				</view>
			</view>

			
		</view>
		
		<swiper class="jhgxeeerert ab" :indicator-dots="true" :autoplay="true" :circular="true" indicator-color="#F0BDC9"
		 indicator-active-color="#FF547B">
			<swiper-item v-for="sd in advertInfo">
				<view class="kjhhxeeett">
					<view class="dsfsdrceder">
						<image :src="sd.imageUrl"></image>
					</view>
				</view>
			</swiper-item>
		</swiper>
		
		
		

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
			<view class="dsfsdtrdert" v-for="sd in linepage">
				<image  :src="sd.cover" class="w100" mode="widthFix" ></image>
			</view>
		</view>
	<!-- 	<uni-load-more :status="status" /> -->
	</view>
</template>
<script>
	import uniLoadMore from '@/components/uni-load-more/uni-load-more.vue'
	export default {
		data() {
			return {
				dsfdsr: 0,
				jhgdse: 10,
				banners:'',
				company:'',
				catalogue:'',
				linepage:'',
				advertInfo:'',
				status: 'more' // loading
			}
		},
		components: {
			uniLoadMore
		},
		methods: {
			async getbanner(){ // 获取顶部推荐⽤户列表
				this.banners = await this.get("user/page",{})
				this.banners  = this.banners.data.content
			},
			async getcompany(){ // 联盟空间
				this.company = await this.get("company/page",{})
				this.company  = this.company.data.content
			},
			async getcatalogue(){ // 分类 icon和名称
				this.catalogue = await this.get("catalogue/page",{})
				this.catalogue  = this.catalogue.data.content
				
				uni.stopPullDownRefresh();
			},
			async getlinepage(){ // 当前⽅程式列表内容
				this.linepage = await this.get("line/page",{})
				this.linepage  = this.linepage.data.content
			},
			async getadvertInfo(){ //
				this.advertInfo = await this.get("advertInfo/list",{code:'LINE'})
				this.advertInfo  = this.advertInfo.data
			},
			jjhhse () {
					this.getbanner()
					this.getcompany()
					this.getcatalogue()
					this.getlinepage()
					this.getadvertInfo()
			}
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
			this.jjhhse()
		},
		mounted() {
			this.jjhhse()
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
		width: 200upx;
		height: 260upx;
		background: #EDEDED;
		border-radius: 10upx;
		font-size: 26upx;
		display: inline-block;
		margin-right: 30upx;
		overflow: hidden;
		position: relative;
		padding: 20upx 30upx;
	}
	/* .jjbxwer image{
		width: 100%;
		height: 100%;
		position: absolute;
		left: 0;
		top: 0;
	} */



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
	.kjhhxeeett{
		padding: 20upx 40upx;
	}
	.yuyyhjxert{
		border-radius: 40upx;
		height: 620upx;
		overflow: hidden;
		position: relative;
	}
	.lokjxeertt{
		position: absolute;
		left: 0;
		bottom: 0;
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
		border-radius: 20upx;
	}
	.kkjjeer{
		width: 80upx;
		height: 80upx;
	}
	.dsfsdrceder{
		height: 200upx;
		
		overflow: hidden;
		border-radius: 20upx;
	}
	.jhgxeeerert.ab {
		height: 220upx;
	}
	.dsfsdrceder image{
		width: 100%;
		height: 100%;
	}
</style>
