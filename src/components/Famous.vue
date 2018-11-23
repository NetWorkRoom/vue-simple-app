<template>
  <div class="card">
    <h5 class="mt-4">Популярные истории <strong>({{famous.length}})</strong></h5>
    <div class="card-body">
      <ul class="list-group">
        <li v-for="(story, index) in famous" :key="index" class="list-group-item">
          {{ story.writer }} сказал "{{ story.plot }}".
          Голосов за историю: {{ story.upvotes }}.
        </li>
      </ul>

    </div>
  </div>
</template>

<script>
// eslint-disable-next-line import/named,import/extensions
import { store } from '../store.js';

export default {
  data() {
    return {
      // даст нам доступ к store.stories
      stories: store.stories,
    };
  },
  computed: {
    famous() {
      return this.stories.filter(item => item.upvotes > 50);
    },
  },
};
</script>

<style scoped>

</style>
