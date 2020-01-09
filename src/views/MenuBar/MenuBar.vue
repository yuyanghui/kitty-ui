<template>
  <div class="menu-bar-container">
    <!--导航菜单-->
    <el-menu
      default-active="1-2"
      @open="handleopen"
      @close="handleclose"
      @select="handleselect"
      :class="
        $store.state.collapse ? 'menu-bar-collapse-width' : 'menu-bar-width'
      "
      :collapse="$store.state.collapse"
    >
      <el-submenu index="1">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span slot="title">系统管理</span>
        </template>
        <el-menu-item index="1-1" @click="$router.push('user')">
          {{ $t("sys.userMng") }}
        </el-menu-item>
        <el-menu-item index="1-2" @click="$router.push('menu')">
          {{ $t("sys.deptMng") }}
        </el-menu-item>
        <el-menu-item index="1-3" @click="$router.push('menu')">
          {{ $t("sys.roleMng") }}
        </el-menu-item>
        <el-menu-item index="1-4" @click="$router.push('menu')">
          {{ $t("sys.menuMng") }}
        </el-menu-item>
        <el-menu-item index="1-5" @click="$router.push('menu')">
          {{ $t("sys.logMng") }}
        </el-menu-item>
      </el-submenu>
      <el-submenu index="2">
        <template slot="title">
          <i class="el-icon-location"></i>
          <span slot="title">系统监控</span>
        </template>
        <el-menu-item index="2-1" @click="$router.push('user')"
          >服务监控</el-menu-item
        >
        <el-menu-item index="2-2" @click="$router.push('menu')"
          >任务监控</el-menu-item
        >
      </el-submenu>
      <el-menu-item index="3" disabled>
        <i class="el-icon-document"></i>
        <span slot="title">导航三</span>
      </el-menu-item>
      <el-menu-item index="4">
        <i class="el-icon-setting"></i>
        <span slot="title">导航四</span>
      </el-menu-item>
    </el-menu>
  </div>
</template>

<script>
export default {
  data() {
    return {};
  },
  methods: {
    handleopen() {
      console.log("handleopen");
    },
    handleclose() {
      console.log("handleclose");
    },
    handleselect(a, b) {
      console.log("handleselect");
    }
  },
  mounted() {}
};
</script>

<style lang="scss" scoped>
.menu-bar-container {
  .el-menu {
    position: absolute;
    top: 60px;
    bottom: 0px;
    text-align: left;
  }
  .menu-bar-width {
    width: 200px;
  }
  .menu-bar-collapse-width {
    width: 65px;
  }
}
</style>
