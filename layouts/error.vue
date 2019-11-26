<template>
  <div class="container">
    <h1 v-if="error.statusCode === 404">404</h1>
    <h1 v-else>Что то не так</h1>
    <nuxt-link to="/" class="button--green">Вернуться</nuxt-link>
  </div>
</template>
<script>
export default {
  props: {
    error: {
      type: Object,
      required: true
    }
  }
}
</script>
