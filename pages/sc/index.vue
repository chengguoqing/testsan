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
				{{sd}}
			</view>
		</scroll-view>
		<view class="xrrtxeertx" :style="{height:xrrtxeertx+'px'}">
			<swiper class="h100" @change="jhxerert" :current="xseerr">
				<swiper-item v-for="sd in 8">
						<quanbu></quanbu>
				</swiper-item>
			</swiper>
		</view>
		<!-- <quanbu></quanbu> -->
	</view>
</template>
<script>
	import quanbu from "./components/quanbu.vue"
	export default {
		data() {
			return {
				dhxewer: ['全部', '本周活动', '会员特价', '活动课程', '家居', '美食', '服饰', '健康'],
				xseerr: 0,
				xrrtxeertx: ''
			}
		},
		components: {
			quanbu
		},
		methods: {
			jhxerert(e) {
				this.xseerr = e.detail.current
			},
			sddrert(e){
				this.xseerr=e
			}
		},
		mounted() {

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
