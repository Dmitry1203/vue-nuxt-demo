<template>
  <div class="container">
    <div>
      <logo />
      <h1 class="title">
        Каталог
      </h1>
      <h2 class="subtitle">
        {{ test }}
      </h2>
      <button @click="getTest">ПОЛУЧИТЬ ДАННЫЕ</button>
      <hr>
      {{ $store.state.test }}

      <div class="links">
        <nuxt-link to="/" class="button--green">Главная</nuxt-link>
        <nuxt-link to="/about" class="button--green">О компании</nuxt-link>
      </div>
    </div>
  </div>
</template>

<script>
  import Logo from '~/components/Logo.vue'
  export default {
    data(){
      return {
        test: "",
      }
    },
    methods: {
      async getTest(){
        this.test = await this.$store.dispatch("GET_TEST");
      },
    },

    // хук жизн цикла в nuxt
    async asyncData({ store }){
      await store.dispatch("LOAD_TEST");
    },

  }
</script>

<style>
  .container {
    margin: 0 auto;
    min-height: 100vh;
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }

  .title {
    font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
    display: block;
    font-weight: 300;
    font-size: 100px;
    color: #35495e;
    letter-spacing: 1px;
  }

  .subtitle {
    font-weight: 300;
    font-size: 42px;
    color: #526488;
    word-spacing: 5px;
    padding-bottom: 15px;
  }

  .links {
    padding-top: 15px;
  }
</style>
