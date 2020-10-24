<template>
  <Layout>
    <div class="snippets">
      <div class="container snippets-container">

        <div class="snippets-header">
          <h1 v-html="$page.post.title" class="snippets-title" />
          <div class="snippets-meta">
            <div class="snippets-author">
              <span class="label">Author</span>
              <span class="author-name" v-text="$page.post.author" />
            </div>
            <div class="snippets-date">
              <span class="label">Date</span>
              <div v-text="$page.post.date"/>
            </div>
            <div class="snippets-time">
              <span class="label">Time</span>
              <span>{{ $page.post.timeToRead }} min read</span>
            </div>
          </div>          
        </div>

        <SnippetsContent :content="$page.post.content" />

      </div>
    </div>
  </Layout>
</template>

<page-query>
query SnippetsPost ($path: String!) {
  post: snippetsPost (path: $path) {
    title
    author
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>
import SnippetsContent from "@/components/SnippetsContent"

export default {
  components: {
    SnippetsContent
  },
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>

<style scoped>
.snippets-container {
  max-width: 1200px;
}

.snippets-header {
  padding: 8rem 0 4rem 0;
}
.snippets-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.snippets-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.snippets-meta > div {
  margin-right: 4rem;
}
.snippets-meta > div:last-of-type {
  margin: 0;
}
</style>
