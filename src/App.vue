<template>
  <div class="content">
    <img width="100" alt="Vue logo" src="./assets/logo.png">
    <hello />
    <!-- Реализуем табы для отдельного показа компонентов -->
    <ul class="nav nav-tabs justify-content-center mt-4">
      <li
        class="nav-item"
        v-for="(page, index) in pages"
        :key="index"
      >
        <!-- Используем ссылки для изменения отображения табов -->
        <!-- Устанавливаем класс 'active' в зависимости от условия -->
        <a href="#"
          :class="['nav-link', isActivePage(page) ? 'active' : '']"
          @click="setPage(page)">{{ page | capitalize }}</a>
      </li>
    </ul>
    <!-- Выводим в данном месте, активный на данный момент компонент -->
    <component :is="activePage"></component>

  </div>
</template>

<script>
// Подключаем экземпляр Vue.
import Vue from 'vue';
// Подключаем файлы дочерних компонентов.
import Hello from './components/Hello.vue';
import Login from './components/Login.vue';
import Register from './components/Register.vue';
import Stories from './components/Stories.vue';

// Создаем пользовательский фильтр.
Vue.filter('capitalize', value => value.charAt(0)
  .toUpperCase() + value.substr(1));

export default {
  name: 'app',
  // Подключаем дочернии компоненты.
  components: {
    Hello,
    Login,
    Register,
    Stories,
  },
  data() {
    return {
      // Массив для формирования табов на странице.
      pages: [
        'stories',
        'register',
        'login',
      ],
      // Своство содержит название активного компонента.
      activePage: 'stories',
    };
  },
  methods: {
    // Метод по клику мыши добавляет в свойство activePage имя выбранного компонента.
    setPage(newPage) {
      this.activePage = newPage;
    },
    // Метод для подключения css класса .active у ссылок в табах.
    isActivePage(page) {
      return this.activePage === page;
    },
  },
};
</script>

<style>
  .content {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
  }
</style>
