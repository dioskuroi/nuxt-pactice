<template>
  <el-container class="layout-default">
    <el-header height="auto">
      <my-header />
    </el-header>
    <el-main>
      <nuxt />
    </el-main>
    <el-footer>Footer</el-footer>
  </el-container>
</template>

<script>
import MyHeader from '@/components/public/header'
export default {
  components: {
    MyHeader
  }
}
</script>

<style lang="scss">
@import '@/assets/css/public/layout.scss';

</style>
