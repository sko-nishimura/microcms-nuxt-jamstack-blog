<template>
	<div class="wrapper">
		<Header />

		<main class="main">
			<div class="inner">
				<h2 class="is-text-align-center">おしらせ</h2>
				
				<ul class="newsList">
					<li v-for="content in contents" :key="content.id">
						<nuxt-link :to="`/news/${content.id}`">
							<div class="newsList__image" v-if="content.thumbnail"><img v-bind:src="content.thumbnail" alt=""></div>
							<div class="newsList__content">
								<p class="publishedAt" v-html="dateSeparate(content.publishedAt)"></p>
								<h3 class="newsTitle">{{ content.title }}</h3>
							</div>
						</nuxt-link>
					</li>
				</ul>
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
  async asyncData() {
    const { data } = await axios.get(
      'https://umusample.microcms.io/api/v1/news',
      {
        headers: { 'X-MICROCMS-API-KEY': '4ae495e5286644a798116bf75130dae3f780' }
      }
    )
    return data
  },
	methods:{
		dateSeparate: function(t){
			const year = t.slice( 0, 4 );
			const month = t.slice( 5, 7 );
			const day = t.slice( 8, 10 );
			const time = year+'年'+month+'月'+day+'日';
			return time;
		}
	},
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