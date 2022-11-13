<template>
  <v-app dark>
    <div class="container">
      <h1 v-if="error.statusCode === 404" class="white--text">
        {{ pageNotFound }}
      </h1>
      <h1 v-else>
        {{ otherError }}
      </h1>
      <NuxtLink to="/" class="white--text">
        ホームへ戻る
      </NuxtLink>
      </div>
  </v-app>
</template>

<style scoped>
.container{
  max-width: 1100px;
}
</style>
<script>
export default {
  name: 'EmptyLayout',
  layout: 'empty',
  props: {
    error: {
      type: Object,
      default: null
    }
  },
  data () {
    return {
      pageNotFound: '404 ページが見つかりません',
      otherError: 'An error occurred'
    }
  },
  head () {
    const title =
      this.error.statusCode === 404 ? this.pageNotFound : this.otherError
    return {
      title
    }
  }
}
</script>

<style scoped>
h1 {
  font-size: 20px;
}
</style>
