<template>
  <main class="main">
    <h1 class="title">{{ title }}</h1>
    <p class="publishedAt" v-html="dateSeparate(publishedAt)"></p>
    <div class="post" v-html="contents"></div>
  </main>
</template>

<script>
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
	}

}
</script>