<template>
  <div id="app" class="container">
		<div class="row">
			<app-header></app-header>
			<app-new></app-new>
			<app-quotes></app-quotes>
			<app-footer></app-footer>
		</div>
	</div>
</template>

<script>
import Header from './components/Header.vue';
import New from './components/New.vue';
import Quotes from './components/Quotes.vue';
import Footer from './components/Footer.vue';

export default {
  components: {
		appHeader: Header,
		appNew: New,
		appQuotes: Quotes,
		appFooter: Footer
	}
}
</script>

<style>
	html {
		font-size: 12pt;
	}

</style>
