<template>
  <div class="h-full flex gap-x-2">
    <side-bar />

    <div class="container w-full p-4">
      <el-breadcrumb separator-class="el-icon-arrow-right">
        <el-breadcrumb-item v-for="page in $route.matched" :to="{ path: page.path }" :key="page.name">{{ page.meta.name || '-' }}</el-breadcrumb-item>
      </el-breadcrumb>

      <nuxt />
    </div>
  </div>
</template>

<script>
import SideBar from '@/components/SideBar.vue'

export default {
  components: {
    SideBar,
  }
}
</script>
