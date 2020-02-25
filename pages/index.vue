<template>
  <div class="container mt-5">

    <!-- TOP ARTICLES -->
    <div class="row">
      <div class="col-md-8">
        <div class="row">
          <div class="col-md-12 mb-2">
            <h6 class="font-weight-bold">Headlines</h6> 
          </div>
          <!-- MAIN FEED -->
          <div class="col-md-12" v-for="(article, index) in articles.slice(0,1)" :key="index">
            <a :href="article.url" target="_blank" >
              <div class="card card-outline mb-3 translate-up">
                <div class="card-body">
                  <h6 class="overline text-primary">US - {{ article.source.name }}</h6>
                  <h6 class="body-1">{{ article.title }}</h6>
                  <h6 class="body-2 text-muted">{{ article.description }}</h6>
                  <img :src="article.urlToImage" class="img-fluid mt-3" :alt="article.title" :title="article.title">
                </div>
              </div>
            </a>
          </div>
          <!-- SUB MAIN FEED -->
          <div class="col-md-12" v-for="(article, index) in articles.slice(1,5)" :key="index">
            <a :href="article.url" target="_blank" >
              <div class="card card-outline mb-3 translate-up">
                <div class="card-body">
                  <div class="media">
                    <div class="media-body">
                      <h6 class="overline text-primary">US - {{ article.source.name }}</h6>
                      <h6 class="body-1">{{ article.title }}</h6>
                      <h6 class="body-2 text-muted">{{ article.description }}</h6>
                    </div>
                    <img :src="article.urlToImage" class="ml-3 align-self-center border-radius-8" style="width:128px" alt="...">
                  </div>
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
      <!-- RIGHT FEED -->
      <div class="col-md-4">
        <div class="row">
          <div class="col-md-12 mb-2">
            <h6>Latest updates</h6>
          </div>
          <div class="col-md-12" v-for="(article, index) in articles.slice(6,9)" :key="index">
            <a :href="article.url" target="_blank" >
              <div class="card card-outline mb-3 translate-up">
                <img :src="article.urlToImage" class="card-img-top" :alt="article.title" :title="article.title">
                <div class="card-body">
                  <h6 class="overline text-primary">US - {{ article.source.name }}</h6>
                  <h6 class="body-1">{{ article.title }}</h6>
                  <h6 class="body-2 text-muted">{{ article.description }}</h6>
                </div>
              </div>
            </a>
          </div>
        </div>
      </div>
      
    </div>
    
    
  </div>
</template>

<script>
export default {
  async asyncData({ app }) {
    const { articles } = await app.$axios.$get(
      `https://newsapi.org/v2/top-headlines?country=us&apiKey=64a37730f655437180f20e1a273e4eee`
    );

    return { articles }; 
  }
}
</script>

