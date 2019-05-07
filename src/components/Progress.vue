<template>

	<div>
		<h2>Quotes Added</h2>
		<div class="progress">
			<span v-if="percentProgress > 0" class="progress-num" :style="{width: percentProgress + '%'}">{{ quoteCount }}/10</span>
		</div>
	</div>
	
</template>

<script>
	import { EventBus } from '../main';

	export default {
		props: ['quoteCount'],

		data(){
			return {
				percent: 0
			}
		},

		computed: {
			percentProgress(){
				return this.percent = this.quoteCount * 10;
			}
		},
	}

</script>

<style>

.progress {
	display: block;
	width: 100%;
	height: 2rem;
	background: transparent;
	box-shadow: 0 0 2px gray;
}

.progress-num {
	display: block;
	background: green;
	color: #fff;
	text-align: right;
	padding-right: 10px;

}
	
</style>