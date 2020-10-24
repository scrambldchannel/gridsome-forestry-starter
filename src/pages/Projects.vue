<template>
  <Layout>

    <div class="container">
      <div class="project-hero">
        <h1 class="project-header">
          Recent Articles
        </h1>
      </div>
    </div>

    <g-link 
      :to="item.node.path"
      v-for="item in $page.posts.edges" 
      :key="item.node.id"
      class="project-post"
    >
      <div class="container projects">
        <h2 class="project-title">{{ item.node.title }}</h2>
        <p class="project-excerpt">{{ item.node.excerpt }}</p>
      </div>
    </g-link>
      
  </Layout>
</template>

<page-query>
query projects {
	posts: allProjectPost {
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
        title: "Projects"
      }
    }

}
</script>

<style scoped>
.project-hero {
  padding: 8rem 0;
  text-align: left;
}
.project-header {
  font-size: 4rem;
  font-weight: 700;
  padding: 0;
  margin: 0;
}
.project-post {
  display: block;
  padding: 2rem 0;
  text-decoration: none;
  transition: background 0.5s ease;
}
.project-post > * {
  transition: transform 0.5s ease;
}
.project-post:hover {
  background-color: var(--color-base-1);
}
.project-post:hover > * {
  transform: translateX(4rem);
}
.project-post h1,
.project-post h2 {
  margin: 0;
  padding: 0;
}
.project-title {
  font-size: 2rem;
  color: var(--color-contrast);
}
.project-excerpt {
  color: var(--color-contrast-1);
}

@media (min-width: 560px) {
  .project-post {
    padding: 3rem 0;
  }
}

@media (min-width: 860px) {
  .project-post {
    padding: 5rem 0;
  }
}
</style>
