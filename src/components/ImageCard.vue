<template>
    <li class="image-card">
        <a :href="image.url_l" target="_blank">
            <img class="image-card__image" :src="image.url_n" :alt="image.title">
        </a>
        <div class="image-card__body">
            <p v-if="image.title" class="image-title">{{image.title}}</p>
            <p v-else class="image-title">No Title</p>
            <p class="image-owner">- By {{image.ownername}} <br /></p>
            <p class="image-date">- {{image.datetaken | moment}}</p>
            <p class="image-tags"><span v-for="tag in processedTags" :key="tag">{{tag}}</span></p>
        </div>
    </li>
</template>

<script>
import moment from 'moment';

export default {
  name: 'ImageCard',
  props: ['image'],
  filters: {
    moment(date) {
      return moment(date).format('MMMM Do, YYYY');
    },
  },
  computed: {
    processedTags() {
      const tagsArray = this.image.tags.split(' ');
      // return tagsArray.slice(0, 3).map((n) => `<span>${n}</span>`).join(' ');
      return tagsArray.slice(0, 3);
      // return tagString.join(' ');
    },
  },
};
</script>

<style lang="scss">
.image-card {
  width: calc(33% - 1rem);
  margin: .5rem;
  border-radius: 5px;
  box-shadow: 0 5px 15px rgba(0, 0, 0, .15);
  background: white;
  @media only screen and (max-width: 799px) {
    width: calc(50% - 1rem);
  }
  @media only screen and (max-width: 549px) {
    width: 100%;
    margin: .5rem 0;
  }
}
.image-card__image {
  border-radius: 5px 5px 0 0;
  width: 100%;
  height: 200px;
  object-fit: cover;
}
.image-card__body {
  padding: .5rem 1rem 1rem;
}
.image-title {
  font-weight: bold;
  margin: 0;
  font-size: 1rem;
}
.image-owner {
  margin-top: 0;
  margin-bottom: 2px;
  font-size: .7rem;
}
.image-title,
.image-owner {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
.image-date {
    margin-top: 0;
    font-size: 0.7rem;
}
.image-tags{
    font-size: .7rem;
}
.image-tags span {
    background: #CAC4CE;
    padding:2px;
    margin:0 2px 0 2px;
}
</style>
