<template>
	<div class="cartcontrol">
		<transition name="move">
			<div class="cart-decrease" v-show="food.count>0" @click="decreaseCart">
				<span class="inner innerout icon-remove_circle_outline"></span>
			</div>
		</transition>
		<div class="cart-count" v-show="food.count>0">{{food.count}}</div>
		<div class="cart-add icon-add_circle" @click="addCart"></div>
	</div>
</template>

<script type="text/ecmascrtipt-6">
	import Vue from 'vue';
	export default {
		props: {
			food: {
				type: Object
			}
		},
		created () {
		},
		methods: {
			addCart (event) {
				if (!event._constructed) {
					return;
				}
				if (!this.food.count) {
					Vue.set(this.food, 'count', 1);
				} else {
					this.food.count++;
				}
				this.$emit('click', event.target);
			},
			decreaseCart (event) {
				if (!event._constructed) {
					return;
				}
				if (this.food.count) {
					this.food.count--;
				}
			}
		}
	};
</script>

<style lang="stylus" type="stylesheet/stylus">
	.cartcontrol
		font-size: 0
		.cart-decrease
			display: inline-block
			padding: 6px
			opactiy: 1
			transform: translate3D(0, 0, 0)
			transition: all 0.4s linear
			&.move-enter-active, &.&move-leave-active
				transition: all 0.4s
			.inner
				display: inline-block
				font-size: 24px
				line-height: 24px
				color:rgb(0, 160, 220)
				transition: all 0.4s linear
			&.move-enter, &.move-leave-to
				opactiy: 0
				transform: translate3D(24px, 0, 0)
				.innerout
					transform: rotate(180deg)
		.cart-count
			display: inline-block
			vertical-align: top
			width: 12px
			padding-top: 6px
			line-height: 24px
			text-align: center
			font-size: 10px
			color: rgb(147, 153, 159)
		.cart-add
			display: inline-block
			font-size: 24px
			line-height: 24px
			padding: 6px
			color: rgb(0, 160, 220)
</style>
