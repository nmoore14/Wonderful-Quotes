<template>
	<div class="container">
		<div class="row">
			<div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
				<div class="input-group">
					<div class="input-group-prepend">
						<span class="input-group-text">Quote:</span>
					</div>
					<textarea class="form-control" rows="1" aria-label="With textarea" v-model="newQuote" v-on:keyup.enter="addQuote" v-if="quoteCount < 10"></textarea>
				</div>
			</div>
			<div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
				<button type="button" class="btn btn-primary btn-lg" @click="addQuote"  v-if="quoteCount < 10">Add Quote</button>
			</div>
		</div>
	</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
	data: function() {
		return {
			newQuote: '',
			quoteCount: 0,
		}
	},
	methods: {
		addQuote: function() {
			eventBus.$emit('quoteAdded', this.newQuote);
			this.newQuote = '';
		}
	},
	created() {
		eventBus.$on('arrayEdit', (data) => {
			this.quoteCount = data;
		})
	}
}
</script>

<style scoped>
	.btn-lg {
		margin: 2rem;
	}
</style>