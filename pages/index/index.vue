<template>
	<view>
		<view class="cu-bar bg-white">
      <view class="action">
      </view>
			<view class="content text-bold">
				<text>首页</text>
        <text class="cuIcon-unfold" style="color: #007AFF;"></text>
			</view>
      <view class="action" style="flex-direction: column;">
        <text class="cuIcon-scan" style="font-size: 25px;"></text>
        <text class="text-xs" style="font-size: 0.1em;">邀请码</text>
      </view>
		</view>
    <scroll-view :scroll-top="scrollTop" scroll-y="true" class="scroll-Y" @scrolltoupper="upper" @scrolltolower="lower"
     @scroll="scroll">
         <view class="cu-bar search bg-white">
         	<view class="search-form round">
         		<text class="cuIcon-search"></text>
         		<input @focus="InputFocus" @blur="InputBlur" :adjust-position="false" type="text" placeholder="找资料" confirm-type="search"></input>
         	</view>
         </view>
        <view class="cu-list grid" :class="['col-' + gridCol,gridBorder?'':'no-border']">
        	<view class="cu-item" v-for="(item,index) in cuIconList" :key="index" v-if="index<gridCol*2">
        		<view :class="['cuIcon-' + item.cuIcon,'text-' + item.color]">
        		</view>
        		<text>{{item.name}}</text>
        	</view>
        </view>
        <view></view>
     </scroll-view>
	</view>
</template>

<script>
  import uniNavBar from "@/components/uni-nav-bar/uni-nav-bar.vue"
	export default {
    components: {uniNavBar},
		data() {
			return {
				title: 'Hello',
        cuIconList: [{
        		cuIcon: 'read',
        		color: 'green',
        		name: '课程'
        	}, {
        		cuIcon: 'file',
        		color: 'yellow',
        		name: '资源'
        	}, {
        		cuIcon: 'circlefill',
        		color: 'orange',
        		name: '微应用'
        	}],
        	gridCol: 3,
        	gridBorder: false,
			}
		},
		onLoad() {

		},
		methods: {
     upper: function(e) {
         console.log(e)
     },
     lower: function(e) {
         console.log(e)
     },
     scroll: function(e) {
         console.log(e)
         this.old.scrollTop = e.detail.scrollTop
     },
     goTop: function(e) {
         this.scrollTop = this.old.scrollTop
         this.$nextTick(function() {
             this.scrollTop = 0
         });
         uni.showToast({
             icon:"none",
             title:"纵向滚动 scrollTop 值已被修改为 0"
         })
     }
		}
	}
</script>

<style>
</style>
