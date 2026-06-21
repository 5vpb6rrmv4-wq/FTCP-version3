<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>困难申请</span></div>
      <div class="card-body"><el-button type="primary" size="small" round style="margin-bottom:12px">新增申请</el-button><el-table :data="apps" size="small" stripe><el-table-column prop="type" label="类型" width="130"/><el-table-column prop="reason" label="原因" min-width="200"/><el-table-column prop="date" label="日期" width="110"/><el-table-column prop="status" label="状态" width="90"><template #default><el-tag type="success" size="small" round>已通过</el-tag></template></el-table-column></el-table></div>
    </div>
  </div>
</template>
<script setup lang="ts">import {ref} from 'vue';const apps=ref([{type:'家庭经济困难',reason:'家庭收入较低，难以承担学费',date:'2025-09-15',status:'已通过'}])</script>
<style scoped>.page-section{max-width:800px}</style>
