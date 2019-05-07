<template>
	<div class="wrap">
		<progress-bar :quoteCount="quoteCount"></progress-bar>
		<div class="max-warning" v-if="quoteCount == maxNumQuotes">Oops! You've reached the max number of quotes. Delete some quotes to add more.</div>
		<form class="quote__input" @submit.prevent="addQuote">
			<div class="input-wrap">
				<label for="quote">Enter a quote</label>
				<textarea rows=5 v-model="quote"></textarea>
				<button type="submit" :class="[quoteCount == maxNumQuotes ? 'deactivate' : '']">Submit</button>
			</div>
			<quotes :quoteCount="quoteCount" :quotes="quotes"></quotes>
		</form>
		<div class="info-wrap">To delete a quote, click on any existing quote.</div>
	</div>
	
</template>

<script>
	import { EventBus } from '../main';
	import Quotes from './Quotes.vue';
	import Progress from './Progress.vue';


	export default {
		components: {
			Quotes,
			ProgressBar: Progress
		},

		data(){
			return {
				quote: '',
				quotes: [],
				quoteCount: 0,
				maxNumQuotes: 10,
			}
		},

		methods: {
			addQuote: function(){
				var quote = this.quote;
				if(this.quoteCount < this.maxNumQuotes) {
					this.quotes.push(quote)
					let newCount = this.quoteCount+1;
					EventBus.$emit('countWasChanged', newCount)
				} 
				this.quote = '';
			}
		},

		mounted(){
			EventBus.$on('countWasChanged', (count) => {
				this.quoteCount = count;
			})
		}
	}
	
</script>

<style>
	label {
		display: block;
	}
	.quote__input {
		display: block;

		padding: 3rem;
		text-align: center;
	}

	textarea {
		display: block;
		margin: 0 auto;
		padding: 1rem;
		width: 50%;
	}

	button {
		display: block;
		margin: 1rem auto 0;
		background: #82c882;
		border-radius: 5px;
		padding: 8px;
		color: #fff;
		text-transform: uppercase;
		letter-spacing: 1px;
		border-color: transparent;
		transition: 0.3s ease all;
	}

	button:hover {
		background: green;
		
	}

	.info-wrap {
		background-color: gray;
		padding: 1rem;
		text-align: center;
		color: #fff;
		
	}

	.max-warning {
		text-align: center;
		color: red;
		font-size: 1.6rem;
	}

	.deactivate {
		pointer-events: none;
  		cursor: default;
  		background: gray;
	}
	
</style>