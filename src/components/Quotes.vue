<template>
	<div class="container-fluid">
		<div class="row">
			<div class="card" v-for="(quote, index) in myQuotes" :key="index" @click="removeQuote(index)">
				<div class="card-body">
					<p class="card-text">{{ quote }}</p>
				</div>
			</div>
		</div>
	</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
	data: function() {
		return {
			myQuotes: []
		}
	},
	methods: {
		removeQuote: function(index) {
			this.myQuotes.splice(index, 1);
			var quotesCount = this.myQuotes.length;
			console.log("Array length after remove: " + quotesCount);
			eventBus.$emit('arrayEdit', quotesCount);
		},
		myQuotesCount: function() {
			var quotesCount = this.myQuotes.length;
			console.log("Array length: " + quotesCount);
			eventBus.$emit('arrayEdit', quotesCount);
		}
	},
	created() {
		eventBus.$on('quoteAdded', (data) => {
			this.myQuotes.push(data);
			this.myQuotesCount();
		})
	}
}
</script>

<style scoped>
	.container-fluid {
		margin-top: .5rem;
	}
	.card {
		width: 23.75rem;
		border-color: #2196F3;
	}

	.card:hover {
		background-color: #FF8A80;
		cursor: pointer;
		border: .13rem solid #D50000;
	}
</style>
