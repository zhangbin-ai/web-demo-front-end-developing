<template>
  <div class="navbar">
    <!-- <hamburger :is-active="sidebar.opened" class="hamburger-container" @toggleClick="toggleSideBar" /> -->

    <breadcrumb class="breadcrumb-container" />

    <!-- 导航条 -->
    <div class="drawer-bg" />
    <div class="sidebar-container">
      <sidebar />
    </div>

    <div class="right-menu">
      <el-dropdown class="avatar-container" trigger="click">
        <div class="avatar-wrapper">
          <img :src="img_avatar" class="user-avatar" />
          <i class="el-icon-caret-bottom" />
        </div>
        <el-dropdown-menu slot="dropdown" class="user-dropdown">
          <router-link to="/">
            <el-dropdown-item>Home</el-dropdown-item>
          </router-link>
          <a target="_blank" href="https://github.com/PanJiaChen/vue-admin-template/">
            <el-dropdown-item>Github</el-dropdown-item>
          </a>
          <a target="_blank" href="https://panjiachen.github.io/vue-element-admin-site/#/">
            <el-dropdown-item>Docs</el-dropdown-item>
          </a>
          <!-- <el-dropdown-item divided @click.native="logout">
            <span style="display:block;">Log Out</span>
          </el-dropdown-item>-->
        </el-dropdown-menu>
      </el-dropdown>
    </div>
  </div>
</template>

<script>
import { mapGetters } from "vuex";
import Breadcrumb from "@/components/Breadcrumb";
import Sidebar from "@/layout/components/Sidebar/index";
// import { Navbar, Sidebar, AppMain } from './components'

// import Hamburger from '@/components/Hamburger'

export default {
  data() {
    return {
      img_avatar: require("@/assets/logo.jpg"),
    };
  },
  components: {
    Breadcrumb,
    Sidebar,
  },
  computed: {
    sidebar() {
      return this.$store.state.app.sidebar;
    },
    ...mapGetters(["sidebar", "avatar"]),
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch("app/toggleSideBar");
    },
    // async logout() {
    //   // await this.$store.dispatch('user/logout')
    //   console.log("out")
    //   // this.$router.push(`/login?redirect=${this.$route.fullPath}`)
    // }
  },
};
</script>

<style lang="scss" scoped>
// .fixed-header {
//   position: fixed;
//   top: 0;
//   right: 0;
//   z-index: 9;
//   width: calc(100%);
//   transition: width 0.28s;
// }

// .hideSidebar .fixed-header {
//   width: calc(100% - 54px);
// }

// .mobile .fixed-header {
//   width: 100%;
// }
.navbar {
  height: 60px;
  overflow: hidden;
  position: relative;
  background: #fff;
  box-shadow: 0 1px 4px rgba(0, 21, 41, 0.08);
  text-align: center;
  .sidebar-container {
    float: right;
    height: 50px;
  }
  .hamburger-container {
    line-height: 60px;
    height: 100%;
    float: left;
    cursor: pointer;
    transition: background 0.3s;
    -webkit-tap-highlight-color: transparent;

    &:hover {
      background: rgba(0, 0, 0, 0.025);
    }
  }

  .breadcrumb-container {
    float: left;
  }

  .right-menu {
    float: right;
    height: 100%;
    line-height: 50px;

    &:focus {
      outline: none;
    }

    .right-menu-item {
      display: inline-block;
      padding: 0 14px;
      height: 100%;
      font-size: 20px;
      color: #5a5e66;
      vertical-align: text-bottom;

      &.hover-effect {
        cursor: pointer;
        transition: background 0.3s;

        &:hover {
          background: rgba(0, 0, 0, 0.025);
        }
      }
    }

    .avatar-container {
      margin-right: 30px;

      .avatar-wrapper {
        margin-top: 7px;
        position: relative;

        .user-avatar {
          cursor: pointer;
          width: 45px;
          height: 45px;
          border-radius: 10px;
        }

        .el-icon-caret-bottom {
          cursor: pointer;
          position: absolute;
          right: -20px;
          top: 25px;
          font-size: 12px;
        }
      }
    }
  }
}
</style>
