<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>助学贷款</span></div>
      <div class="card-body"><el-button type="primary" size="small" round style="margin-bottom:12px">贷款申请</el-button><el-table :data="loans" size="small" stripe><el-table-column prop="type" label="类型" width="140"/><el-table-column prop="amount" label="金额(元)" width="110"/><el-table-column prop="bank" label="银行" width="150"/><el-table-column prop="date" label="日期" width="110"/><el-table-column prop="status" label="状态" width="90"><template #default><el-tag type="success" size="small" round>已通过</el-tag></template></el-table-column></el-table></div>
    </div>
  </div>
</template>
<script setup lang="ts">import {ref} from 'vue';const loans=ref([{type:'国家助学贷款',amount:12000,bank:'中国银行',date:'2025-09-10',status:'已通过'}])</script>
<style scoped>.page-section{max-width:800px}</style>
