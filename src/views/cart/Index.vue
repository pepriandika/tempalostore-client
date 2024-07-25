<template>
	<div>
		<div id="page-wrap">
			<h1>Shoping Cart</h1>
			<ItemCart 
				v-for="item in cartItems" 
				:key="item.id" 
				:item="item"
			/>
			<h3 id="total-price">Total: Rp{{ totalPrice }}</h3>
			<buttton id="checkout-button">Checkout</buttton>
		</div>
	</div>
</template>

<script>
import ItemCart from '@/components/ItemCart.vue';
import { cartItems } from '@/data-seed'

export default {
	components: {
		ItemCart
	},
	data() {
		return {
			cartItems
		}
	},
	computed: {
		totalPrice() {
			return this.cartItems.reduce(
				(sum, item) => sum + Number(item.price),
				0
			)
		}
	} 
}
</script>

<style scoped>
		h1 {
		border-bottom: 1px solid #41B883;
      margin: 16px 0 0;
      padding: 16px;
	}
	#total-price {
		padding: 16px;
		text-align: right;
	}
	#checkout-button {
		width: 100%;
	}
</style>