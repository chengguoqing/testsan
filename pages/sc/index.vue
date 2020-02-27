<template>
	<view>
		<view class="pd pt20">
			<view class="shurukser">
				<icon type="search" size="16" class="shuhhxeert"></icon>
				<input placeholder="输入你感兴趣的人或内容" class="shurunhxeert" />
			</view>
		</view>
		<scroll-view scroll-x="true" class=" mt10 jhggxseert dx_jz">
			<view v-for="(sd,idx) in dhxewer" @tap="sddrert(idx)" :class="idx==xseerr?'act':''" class="xwerrtxe fz30 z6 pr cen  ml30 f_b cz">
				{{sd.name}}
			</view>
		</scroll-view>
		<view class="xrrtxeertx" :style="{height:xrrtxeertx+'px'}">
			<swiper class="h100" @change="jhxerert" :current="xseerr">
				<swiper-item v-for="(sd,idx) in dhxewer">
					
					 <quanbu v-if="idx == 0"></quanbu> 
					<spym :ijkxer="sd.id" v-if="idx != 0"></spym>
				</swiper-item>
			</swiper>
		</view>
		<!-- <quanbu></quanbu> -->
	</view>
</template>
<script>
	import quanbu from "./components/quanbu.vue"
	import spym from "./components/spym.vue"
	
	export default {
		data() {
			return {
				dhxewer: [{
					name:"全部",
					id:''
				}],
				xseerr: 0,
				xrrtxeertx: '',
				goodsCategory:""
			}
		},
		components: {
			quanbu,
			spym
		},
		methods: {
			jhxerert(e) {
				this.xseerr = e.detail.current
			},
			sddrert(e) {
				this.xseerr = e
			},
			// 商品分类
			async getgoodsCategory() {
				this.goodsCategory = await this.get("goodsCategory/page ", {})
				this.goodsCategory = this.goodsCategory.data.content
				this.goodsCategory.map(a=>{
					let eert = {}
					eert.name = a.name
					eert.id =a.id
					this.dhxewer.push(eert)
				})
			},


		},
		mounted() {
			this.getgoodsCategory()
		},
		onLoad() {
			this.xrrtxeertx = uni.getSystemInfoSync().windowHeight - 105
		}
	}
</script>
<style scoped>
	.jhggxseert {
		height: 88upx;
		line-height: 80upx;
		border-top: 1px solid #F9F9FA;
		border-bottom: 1px solid #F9F9FA;
		position: sticky;
		top: 0;
		/* #ifdef H5 */
		top: 88upx;
		/* #endif */
		left: 0;
		background: #fff;
		z-index: 100;

	}

	.xwerrtxe.act {
		color: #ff547b;
	}

	.xwerrtxe.act::after {
		content: ' ';
		position: absolute;
		left: 0;
		bottom: 0;
		border-radius: 40upx;
		background: #ff547b;
		height: 6upx;
		width: 100%;
	}

	.dfvgdftyxe5r {
		height: 100%;
	}
</style>
