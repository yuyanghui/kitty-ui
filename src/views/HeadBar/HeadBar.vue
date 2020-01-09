<template>
  <el-col :span="24" class="header">
    <el-col
      :span="5"
      class="logo"
      :class="$store.state.collapse ? 'logo-collapse-width' : 'logo-width'"
    >
      <img :src="this.logo" /> {{ isCollapse ? sysName : sysName }}
    </el-col>
    <el-col :span="1">
      <div class="tools" @click.prevent="collapse">
        <i class="el-icon-menu"></i>
      </div>
      <!-- <i class="fa fa-align-justify"></i> -->
    </el-col>
    <el-col :span="13">
      <div class="hearNavBar">
        <el-menu
          :default-active="activeIndex"
          class="el-menu-demo"
          background-color="#4b5f6e"
          text-color="#fff"
          active-text-color="#ffd04b"
          mode="horizontal"
          @select="handleSelectHearNavBar"
        >
          <el-menu-item index="1">首页</el-menu-item>
          <el-menu-item index="2">消息中心</el-menu-item>
          <el-menu-item index="3">订单管理</el-menu-item>
        </el-menu>
      </div>
    </el-col>
    <el-col :span="6" class="userinfo">
      <span class="el-dropdown-link">
        <ThemePicker></ThemePicker>
      </span>
      <el-dropdown @command="handleCommand">
        <span class="el-dropdown-link lang-inner"
          >中文<i class="el-icon-arrow-down el-icon--right"></i
        ></span>
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item command="zh">中文</el-dropdown-item>
          <el-dropdown-item command="en">English</el-dropdown-item>
        </el-dropdown-menu>
      </el-dropdown>
      <el-dropdown trigger="hover">
        <span class="el-dropdown-link userinfo-inner"
          ><img :src="this.userAvatar" /> {{ username }}</span
        >
        <el-dropdown-menu slot="dropdown">
          <el-dropdown-item>我的消息</el-dropdown-item>
          <el-dropdown-item>设置</el-dropdown-item>
          <el-dropdown-item divided @click.native="logout"
            >退出登录</el-dropdown-item
          >
        </el-dropdown-menu>
      </el-dropdown>
    </el-col>
  </el-col>
</template>

<script>
import ThemePicker from "@/components/ThemePicker";

export default {
  name: "HomeBar",
  components: {
    ThemePicker
  },
  data() {
    return {
      logo: "",
      isCollapse: false,
      username: "Louis",
      userAvatar: "",
      activeIndex: "1",
      sysName: "kitty"
    };
  },
  methods: {
    handleSelectHearNavBar(key, keyPath) {
      console.log(key, keyPath);
    },
    //折叠导航栏
    collapse: function() {
      this.$store.commit("collapse");
    },
    //语言切换
    handleCommand(command) {
      let lang = command === "" ? "zh" : command;
      this.$i18n.locale = lang;
      console.log(this.$i18n.local);
    },
    //退出登录
    logout: function() {
      var _this = this;
      this.$confirm("确认退出吗?", "提示", {
        type: "warning"
      })
        .then(() => {
          sessionStorage.removeItem("user");
          this.$router.push("/login");
        })
        .catch(() => {});
    }
  },
  mounted() {
    this.sysName = "Vue";
    this.logo = require("@/assets/logo.png");
    var user = sessionStorage.getItem("user");
    if (user) {
      this.userName = user;
      this.userAvatar = require("@/assets/user.png");
    }
  }
};
</script>

<style lang="scss" scoped>
.header {
  height: 60px;
  line-height: 60px;
  background: #4b5f6e;
  color: #fff;
  .userinfo {
    text-align: right;
    padding-right: 30px;
    float: right;
    .lang-inner {
      font-size: 15px;
      cursor: pointer;
      color: #fff;
    }
    .userinfo-inner {
      font-size: 20px;
      cursor: pointer;
      padding-left: 15px;
      color: #fff;
      img {
        width: 40px;
        height: 40px;
        border-radius: 10px;
        margin: 10px 0px 10px 10px;
        float: right;
      }
    }
  }
  .logo {
    height: 60px;
    font-size: 22px;
    padding-left: 0px;
    padding-right: 0px;
    border-color: rgba(238, 241, 146, 0.5);
    border-right-width: 1px;
    border-right-style: solid;
    background: #4b5f6e;
    text-align: left;
    img {
      width: 40px;
      height: 40px;
      border-radius: 0px;
      margin: 10px 10px 10px 10px;
      float: left;
    }
    .txt {
      color: #fff;
    }
  }
  .logo-width {
    width: 200px;
  }
  .logo-collapse-width {
    width: 65px;
  }
  .tools {
    padding-left: 10px;
    padding-right: 10px;
    text-align: center;
    width: 40px;
    height: 60px;
    line-height: 60px;
    cursor: pointer;
  }
  .hearNavBar {
    background: #4b5f6e;
    padding: 0px 0px;
    width: 100%;
    height: 60px;
    line-height: 60px;
    font-size: 29px;
    cursor: pointer;
  }
}
</style>
