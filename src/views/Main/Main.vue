<template>
  <div class="content-container">
    <el-breadcrumb separator="/" class="breadcrumb-inner">
      <el-breadcrumb-item v-for="item in $route.matched" :key="item.path">
        {{ item.name }}
      </el-breadcrumb-item>
    </el-breadcrumb>
    <transition name="fade" mode="out-in">
      <router-view></router-view>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  }
};
</script>

<style lang="scss" scoped>
.content-container {
  position: absolute;
  top: 60px;
  bottom: 0px;
  left: 200px;
  right: 0px;
  .breadcrumb-inner {
    padding: 10px;
    border-color: rgba(38, 86, 114, 0.2);
    border-bottom-width: 1px;
    border-bottom-style: solid;
    background: rgba(138, 158, 170, 0.2);
  }
}
</style>
