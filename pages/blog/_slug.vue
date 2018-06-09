<template>

  <article class="blog">
    <header class="blog__header">
      <h1 class="blog__title">{{ title }}</h1>
	  <p> {{ date }} </p>
    </header>
    <img :src="thumbnail" alt="Image">
    <section class="blog__rich-text" v-md>{{ body }}</section>
  </article>

</template>


<script>
export default {
  async asyncData({ params }) {
    let post = await import("~/content/blog/posts/" + params.slug + ".json");
    return post;
  }
};
</script>
