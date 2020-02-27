<template>
	<mescroll-uni class="dfvgdftyxe5r" :class="goodspage.length<=0?'act':''" ref="mescrollRef" height="90%" top="0"  @init="mescrollInit" :down="downOption" @down="downCallback" @up="upCallback">
		 
    <view class="xkjdrert" >
		<view class="cen mt100 fz32 z9" v-if="goodspage.length<=0">
			暂无数据
		</view>
		<view class="kkhxeert" v-for="sd in goodspage">
			<view class="csdftfcxer">
				<image class="dsftreertxe" :src="sd.imageUrl"></image>
				<view class="dsfsttxeer">
					<view class="dianer fz30 dfgdfxeert">
						{{sd.name}}
					</view>
					<!-- <view class="fz26 z9 dian">
						思维转换：连杯子都要换掉
					</view> -->
					<view class="row mt10 pm20">
						<view class="col red fz28">
							￥ <text class="fz32">{{sd.price/1000}}</text>
						</view>
						<view class="col red tr">
									<image src="../../static/img/addicon.png" class="addicon cz"></image>
						</view>
					</view>
				</view>
			</view>
		</view>
		<view class="qc">
			
		</view>
    </view>
	</mescroll-uni>
</template>
<script>
	import MescrollMixin from "@/components/mescroll-uni/mescroll-mixins.js";
export default {
	props:['ijkxer'],
	mixins: [MescrollMixin], // 使用mixin (在main.js注册全局组件)
    data () {
        return {
			goodspage:""
		}
    },
    components: {
		
	},
    methods: {
		/*下拉刷新的回调 */
		downCallback() {
				this.mescroll.endSuccess();
		},
		/*上拉加载的回调: 其中page.num:当前页 从1开始, page.size:每页数据条数,默认10 */
		upCallback(page) {
		},
		async getgoodspage(){
				this.goodspage = await this.get("goods/page",{type:this.ijkxer})
				this.goodspage  = this.goodspage.data.content
		},
	},
    mounted () {
		this.getgoodspage()
	}
}
</script>
<style>
	
</style>
<style  scoped>
	.xkjdrert{
		padding: 20upx;
	}
	.kkhxeert{
		width: 50%;
		float: left;
		
	}
	.csdftfcxer{
		margin: 6upx;
		min-height: 200upx;
		box-shadow: 0 4upx 16upx rgba(93,113,127,0.08);
		border-radius: 18upx;
		overflow: hidden;
	}
	.dsftreertxe{
		height: 320upx;
		
	}
	.dfgdfxeert{
			height: 80upx;
	}
	.dsfsttxeer{
		padding: 0 20upx;
	}
	.addicon{
		width: 40upx;
		height: 40upx;
	}
	
</style>
