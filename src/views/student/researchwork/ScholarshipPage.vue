<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>奖助学金</span></div>
      <div class="card-body">
        <el-tabs type="border-card">
          <el-tab-pane label="奖学金申请"><el-button type="primary" size="small" round style="margin-bottom:12px">新增申请</el-button><el-table :data="apps" size="small" stripe><el-table-column prop="name" label="名称" min-width="160"/><el-table-column prop="level" label="级别" width="90"/><el-table-column prop="date" label="日期" width="110"/><el-table-column prop="status" label="状态" width="90"><template #default="{row}"><el-tag :type="row.status==='已通过'?'success':'warning'" size="small" round>{{row.status}}</el-tag></template></el-table-column></el-table></el-tab-pane>
          <el-tab-pane label="个人评优"><el-table :data="awards" size="small" stripe><el-table-column prop="name" label="名称" min-width="160"/><el-table-column prop="level" label="级别" width="90"/><el-table-column prop="date" label="日期" width="110"/></el-table></el-tab-pane>
          <el-tab-pane label="班级评优"><el-table :data="classAwards" size="small" stripe><el-table-column prop="name" label="名称" min-width="160"/><el-table-column prop="className" label="班级" width="150"/><el-table-column prop="date" label="日期" width="110"/></el-table></el-tab-pane>
          <el-tab-pane label="证明打印"><el-table :data="certs" size="small" stripe><el-table-column prop="name" label="名称" min-width="160"/><el-table-column prop="year" label="年度" width="80"/><el-table-column label="操作" width="100"><template #default><el-button type="primary" size="small" round>打印</el-button></template></el-table-column></el-table></el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">import {ref} from 'vue'
const apps=ref([{name:'国家奖学金',level:'国家级',date:'2026-03-01',status:'审核中'},{name:'学业奖学金一等奖',level:'校级',date:'2025-10-15',status:'已通过'}])
const awards=ref([{name:'优秀研究生',level:'校级',date:'2026-04-10'}])
const classAwards=ref([{name:'优秀班集体',className:'2023级计算机硕士班',date:'2026-04-20'}])
const certs=ref([{name:'学业奖学金一等奖',year:'2025'},{name:'国家奖学金',year:'2026'}])
</script>
<style scoped>.page-section{max-width:1000px}</style>
