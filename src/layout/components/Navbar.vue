<template>
  <div class="navbar">
    <hamburger :is-active="sidebar.opened" @toggleClick="toggleSideBar" />

    <breadcrumb class="breadcrumb-container" />

    <div style="flex: 1 1 0%; min-width: 0;"></div>

    <div class="right-menu flex">
      <div class="right-menu-item">
        <el-dropdown class="avatar-dropdown" trigger="click">
          <div class="avatar-wrapper">
            <img src="@/assets/nezha.jpeg" class="user-avatar">
          </div>
          <el-dropdown-menu slot="dropdown" class="user-menu-wraper">
            <router-link to="/">
              <el-dropdown-item>
                Home
              </el-dropdown-item>
            </router-link>
            <a target="_blank" href="https://github.com/PanJiaChen/vue-admin-template/">
              <el-dropdown-item>Github</el-dropdown-item>
            </a>
            <a target="_blank" href="https://panjiachen.github.io/vue-element-admin-site/#/">
              <el-dropdown-item>Docs</el-dropdown-item>
            </a>
            <el-dropdown-item divided @click.native="logout">
              <span style="display:block;">Log Out</span>
            </el-dropdown-item>
          </el-dropdown-menu>
        </el-dropdown>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'
import Breadcrumb from '@/components/Breadcrumb'
import Hamburger from '@/components/Hamburger'

export default {
  components: {
    Breadcrumb,
    Hamburger
  },
  computed: {
    ...mapGetters([
      'sidebar',
      'avatar'
    ])
  },
  methods: {
    toggleSideBar() {
      this.$store.dispatch('app/toggleSideBar')
    },
    async logout() {
      await this.$store.dispatch('user/logout')
      this.$router.push(`/login?redirect=${this.$route.fullPath}`)
    }
  }
}
</script>

<style lang="scss" scoped>
@import "~@/styles/variables.scss";

.navbar {
  display: flex;
  align-items: center;
  height: 50px;
  padding-left: 8px;
  overflow: hidden;
  position: relative;
  background: #fff;
  box-shadow: 0 1px 4px rgba(0, 21, 41, .08);

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
      padding: 0 8px;
      height: 100%;
      font-size: 18px;
      color: #5a5e66;
      vertical-align: text-bottom;
      display: flex;
      align-items: center;
      justify-content: center;

      &.hover-effect {
        cursor: pointer;
        transition: background .3s;

        &:hover {
          background: rgba(0, 0, 0, .025)
        }
      }
    }

    .avatar-wrapper {
      padding: 6px;
      line-height: 1;
      font-size: 0;
      border-radius: 99px;
      position: relative;

      &:hover {
        background-color: rgba(0, 0, 0, .045);
      }

      .user-avatar {
        cursor: pointer;
        width: 32px;
        height: 32px;
        border-radius: 32px;
      }
    }
  }
}

.user-menu-wraper {
  width: 248px;
}
</style>
