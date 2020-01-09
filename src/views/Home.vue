<template>
  <el-row class="container">
    <HomeBar />
    <MenuBar />
    <Main />
  </el-row>
</template>

<script>
import mock from "@/mock/index";
import HomeBar from "./HeadBar/HeadBar";
import MenuBar from "./MenuBar/MenuBar";
import Main from "./Main/Main";

export default {
  name: "Home",
  components: {
    HomeBar,
    MenuBar,
    Main
  },
  data() {
    return {};
  },
  methods: {},
  mounted() {}
};
</script>

<style scoped lang="scss">
.container {
  position: absolute;
  top: 0px;
  bottom: 0px;
  left: 0px;
  right: 0px;
  width: 100%;
}
</style>
