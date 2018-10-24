<template>
	<div class="container">
		<div class="row">
			<div class="col-xs-12 col-sm-12 col-md-12 col-lg-12 col-xl-12 bg-info">
				<h5>Info: To remove a quote, click on it.</h5>
				<h4 v-if="count == 10">Delete a quote to add more</h4>
			</div>
		</div>
	</div>
</template>

<script>
import { eventBus } from '../main.js';

export default {
	data: function() {
		return {
			count: 0
		}
	},
	created() {
		eventBus.$on('arrayEdit', (data) => {
			this.count = data;
		})
	},
	computed: {
		alertColor: function() {
			return {
				backgroundColor: 'red'
			}
		}
	}
}
</script>

<style scoped>
	.bg-info {
		border-radius: 2rem;
		color: white;
		text-align: center;
	}
</style>
