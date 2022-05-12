<template>
	<div class="wrapper">
		<Header />

		<main class="main">
			<section class="section">
				<div class="inner">
					<h2 class="is-text-align-center">このサイトについて</h2>
					<p>このサイトはNuxt.jsのテストのためのでもサイトです。<br>内容については正規のものではありません。</p>
				</div>
			</section>
			
			<section class="section">
				<div class="inner">
					<h2 class="is-text-align-center">おしらせ</h2>
					
					<ul class="newsList">
						<li v-for="content in contents" :key="content.id">
							<nuxt-link :to="`/news/${content.id}`">
								<p class="publishedAt" v-html="dateSeparate(content.publishedAt)"></p>
								<h3 class="newsTitle">{{ content.title }}</h3>
							</nuxt-link>
						</li>
					</ul>
				</div>
			</section>

			<section class="section">
				<div class="inner">
					<h2 class="is-text-align-center">お問い合わせ</h2>
					<div class="btnWrap">
						<div class="btn"><a href="" class="btn__link">お問い合わせはこちら</a></div>						
					</div>
				</div>
			</section>

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