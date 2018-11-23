<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
  </div>
</template>

<script>
export default {
  name: 'Hello',
  props: {
    msg: {
      type: String,
      default: 'Приложение на Vue.js',
    },
  },
};
</script>
