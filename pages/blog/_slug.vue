<template>
  <article>
    <h1>{{ title }}</h1>
    <img :src="thumbnail" alt="Image">
    <div v-md.breaks.xhtmlOut.linkify.html>{{ body }}</div>
  </article>
</template>

<script>
export default {
  async asyncData({ params }) {
    // const postPromise = process.BROWSER_BUILD
    //   ? import('~/content/blog/posts/' + params.slug + '.json')
    //   : Promise.resolve(
    //       require('~/content/blog/posts/' + params.slug + '.json')
    //     );

    let post = await import('~/content/blog/posts/' + params.slug + '.json');
    return post;
  }
};
</script>
