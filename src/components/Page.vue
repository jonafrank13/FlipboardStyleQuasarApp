<template>
  <div class="page">
    <!-- <div class="card">1</div> -->
    <page-section v-for="(article, index) in articles" :key="article.id" :index="index" :article="article.data" :noOfArticles="articles.length"></page-section>
    <!-- <div class="last-card card">8</div> -->
  </div>
</template>
<script>
import PageSection from './PageSection'

export default {
  data () {
    return {
      articles: []
    }
  },
  components: {
    PageSection
  },
  beforeCreate () {
    this.$http.get('https://www.reddit.com/.json').then((response) => {
      this.articles = response.body.data.children
      this.expandArticles()
    })
  },
  methods: {
    expandArticles () {
      console.log(this.articles)
    }
  }
}

</script>
<style scoped>
.page {
  display: flex;
  flex-flow: column;
  position: absolute;
  width: 100%;
  height: 100%;
}

.card {
  width: 100%;
  height: 50%;
  position: absolute;
  background: yellow;
}

.last-card {
  top: 50%;
  visibility: hidden;
}

</style>
