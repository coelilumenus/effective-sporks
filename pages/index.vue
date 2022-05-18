<template>
  <div></div>
</template>

<script>
export default {
  name: 'IndexPage',

  created() {
    this.$nuxt.$router.replace({ path: '/quizes'})
  }
}
</script>
