<template>
	<span>
		<div v-if="label" class="title is-6 mb-05">{{label}}</div>
		<span v-bind:class="amountClass">{{amount/100000000 >=1 ? ((amount/100000000).toPrecision(6)/1).toLocaleString() : (amount/100000000).toPrecision(6)/1}} BTC </span>
	</span>
</template>

<script>
export default {
	props: {
		amount: {
			type: Number,
			required: false,
			default: 0
		},
		label: {
			type: String,
			required: false
		},
		isNegative: {
			type: Boolean,
			required: false,
			default: false
		},
		isPositive: {
			type: Boolean,
			required: false,
			default: false
		}
	},
	computed:{
		amountClass:function(){
			return {
				negative: this.isNegative,
				positive: this.isPositive,
				default: !this.isNegative && !this.isPositive
			};
		}
	}
}
</script>

<style scoped>
	.negative{
		color: red;
		font-size: 14px;
		font-weight: 600;
	}

	.positive{
		color: green;
		font-size: 14px;
		font-weight: 600;
	}

	.default{
		font-size: 12px;
		font-weight: 500;
	}
</style>
