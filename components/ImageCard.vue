<!-- Image card component, inspired by https://github.com/lonewolfonline/vue-photography-portfolio, which
leverages Flickr API for image prop -->
<template>
  <div class="item">
    <a :href="image.url_o">
      <img class="image" :src="image.url_n" :alt="image.title" />
      <div class="body">
        <p v-if="image.title" class="image-title">{{ image.title }}</p>
        <p v-else class="image-title">No Title Found</p>
        <p class="image-owner">By {{ image.ownername }}</p>
        <section class="image-date-view-wrapper">
          <p class="image-date">{{ image.datetaken }}</p>
          <p class="image-views">Views: {{ image.views }}</p>
        </section>
      </div>
    </a>
  </div>
</template>

<script>
export default {
  name: 'ImageCard',
  props: ['image'],
}
</script>

<style lang="scss">
//Styling for image cards. Includes transition on hover to display image data.
.item {
  background-color: #eee;
  display: inline-block;
  margin: 0 0 1em;
  width: 100%;
}
.item a {
  text-decoration: none;
}
.item:hover .body {
  visibility: visible;
  opacity: 1;
}
.image {
  width: 100%;
  height: auto;
  object-fit: cover;
}
.body {
  padding: 0.5rem 1rem 1rem;
  position: relative;
  height: 95px;
  margin: -100px 0 0 0;
  background: rgba(0, 0, 0, 0.5);
  color: white;
  visibility: hidden;
  opacity: 0;
  transition: visibility 0s, opacity 0.5s linear;
}
.image-title {
  font-weight: bold;
  margin: 0;
}
.image-owner {
  margin-top: 0;
  font-size: 0.8rem;
}
.image-title,
.image-owner {
  white-space: nowrap;
  text-overflow: ellipsis;
  overflow: hidden;
}
.image-date-view-wrapper {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.image-date,
.image-views {
  margin-bottom: 0;
  font-size: 0.8rem;
}
</style>
