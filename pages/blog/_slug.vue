<template>

  <article class="blog">
    <header class="blog__header">
      <h1 class="blog__title">{{ title }}</h1>
	  <p> {{ date }} </p>
    </header>
    <img :src="thumbnail" alt="Image">
    <vue-markdown :source="body"></vue-markdown>
    <h4>{{ author.name }}</h4>
  </article>

</template>


<script>
export default {
  async asyncData({ params }) {
    let post = await import("~/content/blog/posts/" + params.slug + ".json");
    return post;
  },
  data () {
    const authors = require.context('~/content/authors', false, /\.json$/);

    const author = authors.keys().map(key => ({
      ...blog(key),
      _path: `/authors/${key.replace('.json', '').replace('./', '')}`
    }));
  }
};
</script>
