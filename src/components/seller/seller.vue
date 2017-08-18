<template>
	<div class="seller" ref="seller">
		<div class="seller-content">
			<div class="overview">
				<h1 class="title">{{seller.name}}</h1>
				<div class="desc">
					<star :size="36" :score="seller.score"></star>
					<span class="text">({{seller.ratingCount}})</span>
					<span class="text">({{seller.sellCount}})</span>
				</div>
				<ul class="remark">
					<li class="block">
						<h2>起送价</h2>
						<div class="content">
							<span class="stress">{{seller.minPrice}}元</span>
						</div>
					</li>
					<li class="block">
						<h2>商家配送</h2>
						<div class="content">
							<span class="stress">{{seller.deliveryPrice}}元</span>
						</div>
					</li>
					<li class="block">
						<h2>平均配送时间</h2>
						<div class="content">
							<span class="stress">{{seller.deliveryTime}}分钟</span>
						</div>
					</li>
				</ul>
			</div>
		</div>
	</div>
</template>

<script>
	import BScroll from 'better-scroll'
	import star from '../star/star'

	export default {
		props: {
			seller: {
				type: Object
			}
		},
		components: {
			star
		}
	}
</script>

<style></style>