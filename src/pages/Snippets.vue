<template>
  <Layout>

    <div class="container">
      <div class="snippets-hero">
        <h1 class="snippets-header">
          Recent Snippets
        </h1>
      </div>
    </div>

    <g-link 
      :to="item.node.path"
      v-for="item in $page.posts.edges" 
      :key="item.node.id"
      class="snippets-post">
      <div class="container snippets">
        <h2 class="snippets-title">{{ item.node.title }}</h2>
        <p class="snippets-excerpt">{{ item.node.excerpt }}</p>
      </div>
    </g-link>
      
  </Layout>
</template>

<page-query>
query snippets {
	posts: allSnippetsPost {
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
        title: "Snippets"
      }
    }

}
</script>

<style scoped>
.snippets-hero {
  padding: 8rem 0;
  text-align: left;
}
.snippets-header {
  font-size: 4rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.snippets-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.snippets-post > * {
  transition: transform 0.5s ease;
}
.snippets-post:hover {
  background-color: var(--color-base-1);
}
.snippets-post:hover > * {
  transform: translateX(4rem);
}
.snippets-post h1,
.snippets-post h2 {
  margin: 0;
  padding: 0;
}
.snippets-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.snippets-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .snippets-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .snippets-post {
    padding: 5rem 0;
  }
}
</style>
