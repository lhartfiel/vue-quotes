<template>
	<div>
		<ul>
			<quote v-for="quote in quotes" :quote="quote" :quoteCount="quoteCount"></quote>
		</ul>
	</div>
	
</template>

<script>
	import Quote from  './Quote.vue';

	export default {
		props: ['quotes', 'quoteCount'],

		components: { Quote },
	}
</script>

<style>
	ul {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		grid-gap: 2rem;
		margin-top: 3rem;
	}
	li {

		list-style: none;
		padding: 1rem;
		box-shadow: 0px 0px 3px gray;
	}
</style>