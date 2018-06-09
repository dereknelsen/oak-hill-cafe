<template>
  <section class="container">
    <h2>Blog</h2>
    <ul>
      <li v-for="post in posts" :key="post.date">
        <nuxt-link :to="post._path">
          {{ post.title }}
        </nuxt-link>
      </li>
    </ul>
    <h2>Gallery</h2>
      <ul>
        <li v-for="thumbnail in thumbnails" :key="thumbnail.date">
          <h4>{{ thumbnail.title }}</h4>
          <img :src="thumbnail.image" alt="">
        </li>
      </ul>
  </section>
</template>

<script>
import AppLogo from '~/components/AppLogo.vue';

export default {
  components: {
    AppLogo
  },
  data() {

    // Using webpacks context to gather all files from a folder
    const blog = require.context('~/content/blog/posts/', false, /\.json$/);
    const gallery = require.context('~/content/gallery/thumbnails/', false, /\.json$/);

    const posts = blog.keys().map(key => ({
      ...blog(key),
      _path: `/blog/${key.replace('.json', '').replace('./', '')}`
    }));

    const thumbnails = gallery.keys().map(key => ({
      ...gallery(key),
      _path: `/gallery/${key.replace('.json', '').replace('./', '')}`
    }));

    return { 
      posts, 
      thumbnails 
    };
  }
};
</script>

<style>

</style>
