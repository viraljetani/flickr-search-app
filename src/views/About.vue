<template>
  <div class="wrapper">
    <h4>About Flickr Search App</h4>
    <p>This app uses Flickr Search API and fetches 15 photos for the given tags.</p>
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

<style lang="scss">
#nav{
  display: flex;
  align-items: center;
  justify-content: center;
  border-bottom: 1px solid #8D86C9;
  background: #9067C6;
}
#nav a{
  padding:0 5px 0 5px;
  color:#fff;
  text-decoration: none;
}
#nav a.router-link-exact-active {
  color: #242038
}
.screen-reader-only {
  height: 1px;
  width: 1px;
  position: absolute;
  left: -100000px;
}
.text-centered {
  text-align: center;
}
.wrapper {
  margin: 0 auto;
  max-width: 800px;
  @media only screen and (max-width: 799px) {
    max-width: 100%;
    margin: 0 1.5rem;
  }
}

</style>
