<template>
    <div>
        <div class="latest-snippets-heading container">
        <span class="label">Latest Snippets</span>
        </div>
        <div class="latest-snippets">
        <div class="container">
            <g-link :to="item.node.path" class="snippets" v-for="item in snippets" :key="item.node.id">
              <h3 class="snippets-title">{{ item.node.title }}</h3>
            </g-link>
        </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        snippets: {
            type: Array,
            required: true
        }
    }
}
</script>

<style scoped>
.latest-snippets-heading {
  margin-top: 6rem;
  margin-bottom: 1rem;
  font-size: 0.6rem;
  font-weight: 400;
  text-transform: uppercase;
}
.latest-snippets {
  max-width: 100%;
  margin: 0 2rem;
  border: 1px solid var(--color-base-1);
}
.latest-snippets > .container {
  display: flex;
  flex-wrap: wrap;
}
.snippets {
  flex: 0 0 100%;
  display: block;
  padding: 2rem;
  transition: background 0.25s ease;
  text-decoration: none;
  border-bottom: 1px solid var(--color-base-1);
}

.snippets:last-of-type {
  border-bottom: 0;
}

.snippets:hover {
  background: var(--color-base-1);
}

.snippets-title {
  font-size: 1rem;
  line-height: 1.35;
}

@media (min-width: 580px) {
  .snippets {
    flex: 0 0 50%;
  }
  .snippets:nth-child(1) {
    border-right: 1px solid var(--color-base-1);
    border-bottom: 1px solid var(--color-base-1);
  }

  .snippets:nth-child(2) {
    border-bottom: 1px solid var(--color-base-1);
  }

  .snippets:nth-child(3) {
    border-right: 1px solid var(--color-base-1);
    border-bottom: 0;
  }
}

@media (min-width: 920px) {
  .snippets {
    flex: 0 0 25%;
  }
  .snippets:nth-child(1) {
    border: 0;
    border-right: 1px solid var(--color-base-1);
  }

  .snippets:nth-child(2) {
    border: 0;
    border-right: 1px solid var(--color-base-1);
  }

  .snippets:nth-child(3) {
    border: 0;
    border-right: 1px solid var(--color-base-1);
  }
  .latest-snippets {
    margin: 0;
    border-left: 0;
    border-right: 0;
    border-top: 1px solid var(--color-base-1);
    border-bottom: 1px solid var(--color-base-1);
  }
}

</style>
