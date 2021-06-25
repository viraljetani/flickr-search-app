<template>
  <div class="home">
    <form>
      <label>Search: <input v-model="tag" type="text">
      </label>
      <button type="submit" class="search-btn" @click.prevent="search">Search</button>
    </form>
    <p v-if="loading">Loading...</p>
    <ul v-else>
      <li v-for="image in images" :key="image.id">
        <img :src="image.url_m" :alt="image.title">
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
import config from '../../config';

export default {
  name: 'Home',
  components: {
  },
  data() {
    return {
      tag: '',
      loading: false,
      images: [],
    };
  },
  methods: {
    search() {
      this.loading = true;
      // this.console.log('Searching for: ', this.tag);

      this.getImages()
        .then((res) => {
          this.images = res.data.photos.photo;
          this.loading = false;
        })
        .catch((err) => {
          this.console.log(err);
        });
    },
    getImages() {
      return axios({
        method: 'get',
        url: 'https://api.flickr.com/services/rest',
        params: {
          method: 'flickr.photos.search',
          api_key: config.api_key,
          tags: this.tag,
          page: 1,
          per_page: 15,
          format: 'json',
          nojsoncallback: 1,
          extras: 'date_upload, owner_name, tags,url_l, url_sq, url_t, url_s, url_q, url_m, url_n, url_z, url_c, url_l, url_o',
        },
      });
    },
  },
};
</script>
