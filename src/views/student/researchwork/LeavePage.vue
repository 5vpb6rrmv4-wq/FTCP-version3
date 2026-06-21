<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>日常管理</span><el-button type="primary" size="small" round>请假申请</el-button></div>
      <div class="card-body"><el-table :data="leaves" size="small" stripe><el-table-column prop="type" label="类型" width="80"/><el-table-column prop="reason" label="事由" min-width="180"/><el-table-column prop="start" label="开始" width="110"/><el-table-column prop="end" label="结束" width="110"/><el-table-column prop="days" label="天" width="50"/><el-table-column prop="status" label="状态" width="90"><template #default="{row}"><el-tag :type="row.status==='已批准'?'success':'warning'" size="small" round>{{row.status}}</el-tag></template></el-table-column><el-table-column label="操作" width="100"><template #default><el-button text type="primary" size="small">销假</el-button></template></el-table-column></el-table></div>
    </div>
  </div>
</template>
<script setup lang="ts">import {ref} from 'vue';const leaves=ref([{type:'事假',reason:'回家探亲',start:'2026-05-01',end:'2026-05-05',days:5,status:'已批准'},{type:'病假',reason:'感冒发烧',start:'2026-06-10',end:'2026-06-11',days:2,status:'审核中'}])</script>
<style scoped>.page-section{max-width:1000px}</style>
