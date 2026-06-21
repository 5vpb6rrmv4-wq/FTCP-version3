<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>三助一辅</span></div>
      <div class="card-body">
        <el-tabs type="border-card">
          <el-tab-pane label="岗位申请"><el-button type="primary" size="small" round style="margin-bottom:12px">申请岗位</el-button><el-table :data="apps" size="small" stripe><el-table-column prop="post" label="岗位" min-width="160"/><el-table-column prop="dept" label="部门" width="130"/><el-table-column prop="type" label="类别" width="80"><template #default><el-tag size="small" round>助教</el-tag></template></el-table-column><el-table-column prop="date" label="日期" width="110"/><el-table-column prop="status" label="状态" width="90"><template #default><el-tag type="success" size="small" round>已通过</el-tag></template></el-table-column></el-table></el-tab-pane>
          <el-tab-pane label="退岗申请"><el-table :data="resigns" size="small" stripe><el-table-column prop="post" label="岗位" min-width="160"/><el-table-column prop="reason" label="原因" min-width="160"/><el-table-column prop="date" label="日期" width="110"/><el-table-column prop="status" label="状态" width="90"><template #default><el-tag type="success" size="small" round>已批准</el-tag></template></el-table-column></el-table></el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">import {ref} from 'vue'
const apps=ref([{post:'研究生助教',dept:'计算机学院',date:'2026-02-20',status:'已通过'}])
const resigns=ref([{post:'图书馆管理员助理',reason:'学业繁忙',date:'2025-12-15',status:'已批准'}])
</script>
<style scoped>.page-section{max-width:1000px}</style>
