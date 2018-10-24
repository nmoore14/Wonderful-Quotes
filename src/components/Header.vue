<template>
	<div class="container">
		<div class="row">
			<div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12">
				<h2 class="dispay-2">Quotes Added</h2>
				<div class="progress">
  				<div class="progress-bar" role="progressbar" :style="barLength" aria-valuenow="25" aria-valuemin="0" aria-valuemax="100">{{ quoteCount }}/10</div>
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
			quoteCount: 0
		}
	},
	created() {
		eventBus.$on('arrayEdit', (data) => {
			this.quoteCount = data;
		})
	},
	computed: {
		barLength: function() {
			return {
				width: this.quoteCount / 10 * 100 + '%'
			}
		}
	}
}
</script>

<style scoped>
	.container {
		margin-bottom: 2rem;
	}

	h2 {
		font-weight: lighter;
	}

	.progress {
		height: 3rem;
	}
</style>