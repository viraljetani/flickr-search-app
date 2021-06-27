<template>
  <div class="about">
    <h1>This is an about page</h1>
  </div>
</template>

<script>
export default {
  name: 'About',
  metaInfo() {
    return {
      title: 'About - Flickr Search App - VueJs, Flickr Api',
      meta: [
        { name: 'description', content: 'About Flickr Search App created using VueJs and Flickr Public photos api.' },

      ],
    };
  },
};
</script>
