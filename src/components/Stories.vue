<template>
  <div>
    <h5 class="mt-4">Истории</h5>
      <!-- Выводим в виде списка все истории из хранилища данных -->
      <ul class="list-group">
        <li v-for="(story, index) in stories" :key="index" class="list-group-item">
          {{ story.writer }} сказал "{{ story.plot }}"
          Голосов за историю: {{ story.upvotes }}.
        </li>
      </ul>
  </div>
</template>

<script>
/* eslint-disable import/extensions */
// Подключаем общее хранилище данных.
import { store } from '../store.js';

export default {
  name: 'Stories',
  data() {
    return {
      // Получаем доступ к данным в хранилище через объект store.stories
      stories: store.stories,
    };
  },
  created() {
    console.log('истории');
  },

};
</script>
