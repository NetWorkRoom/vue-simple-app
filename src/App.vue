<template>
  <div id="app">

    <img width="100" alt="Vue logo" src="./assets/logo.png">

    <hello />

    <ul class="nav nav-tabs justify-content-center mt-4">
      <!-- установка класса 'active' в зависимости от условия -->
      <li
        class="nav-item"
        v-for="(page, index) in pages"
        :key="index"
      >
        <!-- используем ссылки для изменения табов -->
        <a href="#"
          :class="['nav-link', isActivePage(page) ? 'active' : '']"
          @click="setPage(page)">{{ page | capitalize }}</a>
      </li>
    </ul>
    <component :is="activePage"></component>
  </div>
</template>

<script>
import Vue from 'vue';

import Hello from './components/Hello.vue';
import Login from './components/Login.vue';
import Register from './components/Register.vue';
import Stories from './components/Stories.vue';

Vue.filter('capitalize', value => value.charAt(0)
  .toUpperCase() + value.substr(1));

export default {
  name: 'app',
  components: {
    Hello,
    Login,
    Register,
    Stories,
  },
  data() {
    return {
      pages: [
        'stories',
        'register',
        'login',
      ],
      activePage: 'stories',
    };
  },
  methods: {
    setPage(newPage) {
      this.activePage = newPage;
    },
    isActivePage(page) {
      return this.activePage === page;
    },
  },
};
</script>

<style>
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
