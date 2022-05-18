<template>
  <div class="h-full flex gap-x-2">
    <side-bar />

    <div class="contaner p-4">
      <nuxt />
    </div>
  </div>
</template>

<script>
import SideBar from '@/components/SideBar.vue'

export default {
  components: {
    SideBar,
  },
}
</script>
