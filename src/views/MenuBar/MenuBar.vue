<template>
  <el-col :span="24" class="main">
    <aside class="aside">
      <!--导航菜单-->
      <el-menu
        default-active="1-2"
        class="el-menu-vertical-demo"
        @open="handleopen"
        @close="handleclose"
        @select="handleselect"
        :collapse="isCollapse"
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
    </aside>
  </el-col>
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
.main {
  display: flex;
  position: absolute;
  top: 60px;
  bottom: 0px;
  overflow: hidden;
  aside {
    flex: 0 0 200px;
    width: 200px;
    .el-menu {
      height: 100%;
      text-align: left;
    }
  }
}
</style>
