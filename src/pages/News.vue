<template>
  <Layout>

    <div class="container">
      <div class="news-hero">
        <h1 class="news-header">
          Recent blog posts
        </h1>
      </div>
    </div>

    <g-link 
      :to="item.node.path"
      v-for="item in $page.posts.edges" 
      :key="item.node.id"
      class="news-post"
    >
      <div class="container news">
        <h2 class="news-title">{{ item.node.title }}</h2>
        <p class="news-excerpt">{{ item.node.excerpt }}</p>
      </div>
    </g-link>
      
  </Layout>
</template>

<page-query>
query news {
	posts: allNewsPost {
    edges {
      node {
        id
        path
        title
        excerpt
      }
    }
  }
}
</page-query>

<script>
export default {
      metaInfo () {
      return {
        title: "News"
      }
    }

}
</script>

<style scoped>
.container.new {
  max-width: 720px;
}
.news-hero {
  padding: 4rem 0;
  text-align: center;
  color: var(--color-base-1);
}
.news-header {
  font-size: 3rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.news-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.news-post > * {
  transition: transform 0.5s ease;
}
.news-post:hover {
  background-color: var(--color-base-1);
}
.news-post:hover > * {
  transform: translateX(4rem);
}
.news-post h1,
.news-post h2 {
  margin: 0;
  padding: 0;
}
.news-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.news-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .news-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .news-post {
    padding: 5rem 0;
  }
}
</style>
