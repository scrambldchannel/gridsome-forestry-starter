<template>
  <Layout>
    <div class="news">
      <div class="container news-container">

        <div class="news-header">
          <h1 v-html="$page.post.title" class="news-title" />
          <div class="news-meta">
            <div class="news-author">
              <span class="label">Author</span>
              <span class="author-name" v-text="$page.post.author" />
            </div>
            <div class="news-date">
              <span class="label">Date</span>
              <div v-text="$page.post.date"/>
            </div>
            <div class="news-time">
              <span class="label">Time</span>
              <span>{{ $page.post.timeToRead }} min read</span>
            </div>
          </div>          
        </div>

        <NewsContent :content="$page.post.content" />

      </div>
    </div>
  </Layout>
</template>

<page-query>
query NewsPost ($path: String!) {
  post: newsPost (path: $path) {
    title
    author
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>
import NewsContent from "@/components/NewsContent"

export default {
  components: {
    NewsContent
  },
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>

<style scoped>
.news-container {
  max-width: 1200px;
}

.news-header {
  padding: 8rem 0 4rem 0;
}
.news-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.news-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.news-meta > div {
  margin-right: 4rem;
}
.news-meta > div:last-of-type {
  margin: 0;
}
</style>
