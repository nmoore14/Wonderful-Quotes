<template>
	<div class="container">
		<div class="row">
			<div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
				<div class="input-group">
					<div class="input-group-prepend">
						<span class="input-group-text">Quote:</span>
					</div>
					<input type="text" class="form-control" aria-label="With textarea" v-model="newQuote" v-on:keyup.enter="addQuote" v-if="quoteCount < 10">
				</div>
			</div>
			<div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
				<button type="button" class="btn btn-secondary btn-lg btn-block" @click="addQuote"  v-if="quoteCount < 10">Add Quote</button>
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
			if(this.newQuote != '') {
				eventBus.$emit('quoteAdded', this.newQuote);
				this.newQuote = '';
			}
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
	.input-group-text {
		font-size: 1.75rem;
		font-weight: lighter;
		border-radius: 2rem 0 0 2rem;
	}

	input {
		font-size: 1.75rem;
		font-weight: lighter;
		height: 4rem;
		border-radius: 0 2rem 2rem 0;
	}

	input:focus {
		box-shadow: none;
		border: .13rem solid #00B0FF;
	}

	.btn-block {
		margin-top: .25rem;
		background-color: #03A9F4;
		border: none;
	}
</style>