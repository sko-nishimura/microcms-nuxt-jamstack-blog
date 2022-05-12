<template>
	<div class="wrapper">
		<Header />

		<main class="main">

			<div class="inner">
				<h2 class="is-text-align-center">このサイトについて</h2>
				
				
			</div>

		</main>

		<Footer />
	</div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/siteHeader.vue'
import Footer from '@/components/siteFooter.vue'
export default {
	
	components: {
		Header,
		Footer
	}
}
</script>

<style lang="scss">

.newsList{
	display: flex;
	flex-direction: column;
	gap: 1.5em;
}

</style>