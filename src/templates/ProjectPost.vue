<template>
  <Layout>
    <div class="project">
      <div class="container project-container">

        <div class="project-header">
          <h1 v-html="$page.post.title" class="project-title" />
          <div class="project-meta">
            <div class="project-author">
              <span class="label">Author</span>
              <span class="author-name" v-text="$page.post.author" />
            </div>
            <div class="project-date">
              <span class="label">Date</span>
              <div v-text="$page.post.date"/>
            </div>
            <div class="project-time">
              <span class="label">Time</span>
              <span>{{ $page.post.timeToRead }} min read</span>
            </div>
          </div>          
        </div>

        <ProjectContent :content="$page.post.content" />

      </div>
    </div>
  </Layout>
</template>

<page-query>
query ProjectPost ($path: String!) {
  post: projectPost (path: $path) {
    title
    author
    date (format: "D. MMMM YYYY")
    timeToRead
    content
  }
}
</page-query>

<script>
import ProjectContent from "@/components/ProjectContent"

export default {
  components: {
    ProjectContent
  },
  metaInfo () {
    return {
      title: this.$page.post.title
    }
  }
}
</script>

<style scoped>
.project-container {
  max-width: 1200px;
}

.project-header {
  padding: 8rem 0 4rem 0;
}
.project-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.project-meta {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.project-meta > div {
  margin-right: 4rem;
}
.project-meta > div:last-of-type {
  margin: 0;
}
</style>
