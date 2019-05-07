<template>
	<li @click="removeQuote()" key="quote--{{ count }}">{{ quote }}</li>
</template>

<script>
	import { EventBus } from '../main';

	export default{

		props: ['quote', 'quoteCount'],

		data(){
			return {
				count: this.quoteCount
			}
		},

		methods: {
			removeQuote(){
				let currentQuote = this.$el;
				currentQuote.remove();
				this.count = this.quoteCount - 1;
				EventBus.$emit('countWasChanged', this.count)
			}
		},
	}
</script>

<style>
	li:hover {
		cursor: pointer;
	}
</style>