<template>
  <div class="card">
    <img :src="resolve_img_url(image)" alt="" />
  </div>
</template>
<script>
  export default {
    name: 'Card',
    props: ['image', 'description'],
    methods: {
      resolve_img_url: function (path) {
        let source = require.context('../../assets/', false, /\.png$|\.jpg$/)
        return source("./"+path)
      }
  }
  }
</script>
<style lang="scss">
  .card {
    width: 100%;
  }
</style>