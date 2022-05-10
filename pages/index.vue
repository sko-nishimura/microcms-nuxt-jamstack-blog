<template>
	<div class="wrapper">
		<Header />

		<main class="main">
		<ul>
			<li v-for="content in contents" :key="content.id">
				<nuxt-link :to="`/${content.id}`">
					{{ content.title }}
				</nuxt-link>
			</li>
		</ul>
		</main>

		<Footer />
	</div>
</template>

<script>
import axios from 'axios'
import Header from '@/components/siteHeader.vue'
import Footer from '@/components/siteFooter.vue'
export default {
  async asyncData() {
    const { data } = await axios.get(
      'https://umusample.microcms.io/api/v1/news',
      {
        headers: { 'X-MICROCMS-API-KEY': '4ae495e5286644a798116bf75130dae3f780' }
      }
    )
    return data
  },
	components: {
		Header,
		Footer
	}
}
</script>