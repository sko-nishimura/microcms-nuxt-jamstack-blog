<template>
	<div class="wrapper">
	<Header />
  <main class="main">
		<div class="inner newsContents">

			<h1 class="title">{{ title }}</h1>
			<p class="publishedAt" v-html="dateSeparate(publishedAt)"></p>
			<div class="postContent" v-html="contents"></div>

			<div class="fieldBlock">
				<div class="fieldBlock__image" v-html="field.fieldtext"></div>
				<div class="fieldBlock__image"><img v-bind:src="field.fieldimg.url" alt=""></div>
			</div>

		</div>

  </main>
	<Footer />
	</div>
</template>

<script>
import Header from '@/components/siteHeader.vue'
import Footer from '@/components/siteFooter.vue'
import axios from 'axios'

export default {
  async asyncData({ params }) {
    const { data } = await axios.get(
      `https://umusample.microcms.io/api/v1/news/${params.slug}`,
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
.newsContents{
	h1{
		margin-bottom: 1em;
		font-size: 2em;
	}

	.postContent{
		margin-top: 2em;
	}
}

.fieldBlock{
	display: flex;
	gap: 5%;
	margin-top: 3em;
}

</style>