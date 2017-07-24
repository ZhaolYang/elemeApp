<template>
    <div class="v-header">
        <div class="content-wrapper">
        	<div class="avatar">
        		<img width="64" height="64" :src="seller.avatar">
        	</div>
        	<div class="content">
        		<p class="title">
        			<span class="brand"></span>
        			<span class="name">{{seller.name}}</span>
        		</p>
        		<div class="description">
        			{{seller.description}}/{{seller.deliveryTime}}分钟送达
        		</div>
        		<div v-if="seller.supports" class="support">
        			<span class="icon" :class="classMap[seller.supports[0].type]"></span>
        			<span class="text">{{seller.supports[0].description}}</span>
        		</div>
        	</div>
        	<div v-if="seller.supports" class="support-count">
        		<span class="count" @click="showDetail">{{seller.supports.length}}个</span>
        		<i class="icon-keyboard_arrow_right"></i>
        	</div>
        </div>
        <div class="notice-wrapper" @click="showDetail">
        	<span class="notice-title"></span>
        	<span class="notice-text">{{seller.bulletin}}</span>
        	<i class="icon-keyboard_arrow_right"></i>	
        </div>
        <div class="background">
        	<img :src="seller.avatar" width="100%" height="100%">
        </div>
				<transition name="fade">
					<div v-show="detailShow" class="detail">
						<div class="detail-wrapper clearfix">
							<div class="detail-main">
								<h1 class="name">{{seller.name}}</h1>
								<div class="star-wrapper">
									<star :size="48" :score="seller.score"></star>
								</div>
								<!-- 优惠信息 -->
								<div class="title">
									<div class="line"></div>
									<p class="text">优惠信息</p>
									<div class="line"></div>
								</div>
								<ul v-if="seller.supports" class="supports">
									<li class="support-item" v-for="(item, index) in seller.supports">
											<span class="icon" :class="classMap[item.type]"></span>
											<span class="text">{{item.description}}</span>
									</li>
								</ul>
								<div class="title">
									<div class="line"></div>
									<p class="text">商家公告</p>
									<div class="line"></div>
								</div>
								<!-- 公告 -->
								<div class="bulletin">
									<p class="content">{{seller.bulletin}}</p>
								</div>
							</div>
						</div>
						<div class="detail-close">
							<i class="icon-close" @click="hideDetail"></i>
						</div>
					</div>
				</transition>
        
    </div>
</template>

<script>
import star from '../star/star'

export default {
    name: 'v-header',
    data(){
        return {
        	detailShow: false
        }
    },
    props: {
    	seller: {
    		type: Object
    	}
    },
    created() {
    	this.classMap = ['decrease','discount','special','invoice','guarantee']
    },
    methods: {
    	showDetail(){
    		this.detailShow = true
    	},
			hideDetail(){
				this.detailShow = false
			}
    },
    components: {
    	star
    }
}
</script>

<style lang="stylus">
	@import "../../common/stylus/mixin.styl"

	.v-header
	  position: relative
	  color: #fff
	  background: rgba(7,17,27,.5)
	  overflow: hidden
	  .content-wrapper
	  	position: relative
	  	padding: 24px 12px 18px 24px
	  	font-size: 0
	  	.avatar
	  	  display: inline-block
	  	  font-size: 14px
	  	  vertical-align: top
	  	  img
	  	  	border-radius: 2px
	  	.content
	  	  display: inline-block
	  	  margin-left: 16px
	  	  font-size: 14px
	  	  .title
	  	    margin: 2px 0 8px 0
	  	    .brand
	  	      display: inline-block
	  	      vertical-align: top
	  	      width: 30px
	  	      height: 18px
	  	      bg-image('brand')
	  	      background-size: 30px 18px
	  	      background-repeat: no-repeat
	  	    .name
	  	      margin-left: 6px
	  	      font-size: 16px
	  	      line-height: 18px
	  	      font-weight: bold
	  	  .description
	  	  	margin-bottom: 10px
	  	  	line-height: 12px
	  	  	font-size: 12px
	  	  .support
	  	  	.icon
	  	  	  display: inline-block
	  	  	  width: 12px
	  	  	  height: 12px
	  	  	  margin-right: 4px
	  	  	  background-size: 12px 12px
	  	  	  background-repeat: no-repeat
	  	  	  vertical-align: top
	  	  	  &.decrease
	  	  	  	bg-image('decrease_1')
	  	  	  &.discount
	  	  	  	bg-image('discount_1')
	  	  	  &.guarantee
	  	  	  	bg-image('guarantee_1')
	  	  	  &.invoice
	  	  	  	bg-image('invoice_1')
	  	  	  &.special
	  	  	  	bg-image('special_1')
	  	  	.text
	  	      font-size: 10px
	  	      line-height: 12px
	  	      vertical-align: top
	  	.support-count
	      position: absolute
	      right: 12px
	      bottom: 14px
	      padding: 0 8px
	      height: 24px
	      line-height: 24px
	      border-radius: 14px
	      background: rgba(0,0,0,0.2)
	      text-align: center
	      .count
	      	vertical-align: top
	      	font-size: 10px
	      .icon-keyboard_arrow_right
	      	margin-left: 2px
	      	line-height: 24px
	      	font-size: 10px
	  .notice-wrapper 
	  	position: relative
	  	height: 28px
	  	line-height: 28px
	  	padding: 0 22px 0 12px
	  	white-space: nowrap
	  	overflow: hidden
	  	text-overflow: ellipsis
	  	font-size: 0
	  	background: rgba(7,17,27,.2)
	  	.notice-title
	  	  display: inline-block
	  	  vertical-align: top
	  	  margin-top: 8px
	  	  width: 22px
	  	  height: 12px
	  	  bg-image('bulletin')
	  	  background-size: 22px 12px
	  	  background-repeat: no-repeat
	  	.notice-text
	      margin-left: 0 4px
	  	  font-size: 10px
	  	.icon-keyboard_arrow_right
	  	  position: absolute
	  	  font-size: 10px
	  	  right: 12px
	  	  top: 8px
	  .background
	  	position: absolute
	  	top: 0
	  	left: 0
	  	width: 100%
	  	height: 100%
	  	z-index: -1
	  	filter: blur(10px)
	  .detail
	  	position: fixed
	  	top: 0
	  	left: 0
	  	z-index: 100
	  	width: 100vw
	  	height: 100%
	  	overflow: auto
	  	background: rgba(7,17,27,.8)
			backdrop-filter: blur(10px)
			.detail-wrapper
				min-height: 100vh
				width: 100vw
				.detail-main
					padding-top: 64px
					padding-bottom: 64px
					.name
						line-height: 16px
						text-align: center
						font-size: 16px
						font-weight: 700
					.star-wrapper
						margin-top: 18px
						padding: 2px 0
						text-align: center
					.title
						display: flex
						width: 80vw
						margin: 30px auto 24px
						.line
							flex: 1
							position: relative
							top: -6px
							border-bottom: 1px solid rgba(255,255,255,.2)
						.text
							padding: 0 12px
							font-size: 14px
					.supports
						width: 80vw
						margin: 0 auto
						.support-item
							padding: 0 12px
							margin-bottom: 12px
							font-size: 0
							&:last-child
								margin-bottom: 0
							.icon
								display: inline-block
								width: 16px
								height: 16px
								vertical-align: top
								margin-right: 6px
								background-size: 16px 16px
								background-repeat: no-repeat
								&.decrease
									bg-image('decrease_2')
								&.discount
									bg-image('discount_2')
								&.guarantee
									bg-image('guarantee_2')
								&.invoice
									bg-image('invoice_2')
								&.special
									bg-image('special_2')
							.text
								line-height: 16px
								font-size: 12px
					.bulletin
						width: 80vw
						margin: 0 auto
						.content
							padding: 0 12px
							line-height 24px
							font-size: 12px
			.detail-close
				position: relative
				width: 32px
				height: 32px
				margin: -64px auto 0
				clear: both
				font-size: 32px
		.fade-enter-active, .fade-leave-active
			transition: all .3s
		.fade-enter, .fade-leave-to
			opacity: 0
</style>