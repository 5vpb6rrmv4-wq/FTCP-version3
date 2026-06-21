<template>
  <el-container class="app-root">
    <el-aside :width="sidebarCollapsed ? '64px' : '220px'" class="app-sidebar">
      <SideNav :collapsed="sidebarCollapsed" @toggle="sidebarCollapsed=!sidebarCollapsed" />
    </el-aside>
    <el-container class="main-area">
      <el-header height="auto" class="top-bar">
        <TopNav :role="userRole" @toggle="sidebarCollapsed=!sidebarCollapsed" />
      </el-header>
      <WelcomeBar :role="userRole" />
      <BreadcrumbBar />
      <el-main class="page-content">
        <router-view />
      </el-main>
    </el-container>
  </el-container>
</template>

<script setup lang="ts">
import { ref, computed } from 'vue'
import { useAuthStore } from '@/stores/auth'
import SideNav from './SideNav.vue'
import TopNav from './TopNav.vue'
import WelcomeBar from './WelcomeBar.vue'
import BreadcrumbBar from './BreadcrumbBar.vue'

const auth = useAuthStore()
const sidebarCollapsed = ref(false)
const userRole = computed(() => auth.role)
</script>

<style scoped>
.app-root { height: 100vh; }
.app-sidebar { background: linear-gradient(180deg,#0d2a6b,#153D97 50%,#108B96); transition: width .2s; overflow-x: hidden; flex-shrink: 0; box-shadow: 2px 0 20px rgba(0,0,0,.1); z-index: 10; }
.main-area { flex-direction: column; overflow: hidden; }
.top-bar { padding: 0; background: #fff; border-bottom: 1px solid #e2e8f0; z-index: 5; }
</style>
