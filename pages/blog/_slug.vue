<template>

  <article class="blog">
    <header class="blog__header">
      <h1 class="blog__title">{{ post.title }}</h1>
	  <p> {{ post.date }} </p>
    </header>
    <img :src="post.thumbnail" alt="Image">
    <vue-markdown :source="post.body"></vue-markdown>
    <h4>{{ author.name }}</h4>
  </article>

</template>


<script>
export default {
  async asyncData({ params }) {
    let post = await import("~/content/blog/posts/" + params.slug + ".json");
    let author = await import("~/content/authors/" + params.slug + ".json");
    return post, author;
  },
  
};
</script>
