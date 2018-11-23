<template>
  <div>
    <h5 class="mt-4">Истории</h5>
      <ul class="list-group">
        <li v-for="(story, index) in stories" :key="index" class="list-group-item">
          {{ story.writer }} сказал "{{ story.plot }}"
          Голосов за историю: {{ story.upvotes }}.
        </li>
      </ul>
  </div>
</template>

<script>
// eslint-disable-next-line import/named,import/extensions
import { store } from '../store.js';

export default {
  name: 'Stories',
  data() {
    return {
      // даст нам доступ к store.stories
      stories: store.stories,
    };
  },
  created() {
    console.log('истории');
  },

};
</script>

<style scoped>

</style>
