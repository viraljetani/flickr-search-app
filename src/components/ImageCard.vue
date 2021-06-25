<template>
    <div>
        <li>
            <img :src="image.url_m" :alt="image.title">
            <div>
                <p v-if="image.title">{{image.title}}</p>
                <p>By {{image.ownername}}</p>
                <p>{{image.datetaken}}</p>
                <p>Views: {{image.views}}</p>
            </div>
        </li>
    </div>
</template>

<script>
export default {
  name: 'ImageCard',
  props: ['image'],
};
</script>
