<template>
    <div class="container">
    	<quote-input></quote-input>
    </div>
</template>

<script>
	import { EventBus } from './main.js';
	import Input from './components/QuoteInput.vue';

    export default {
        components: {
        	'quote-input': Input
        }
    }
</script>

<style>
</style>
