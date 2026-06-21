<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>培养管理</span></div>
      <div class="card-body">
        <el-tabs type="border-card">
          <el-tab-pane label="学期注册"><el-table :data="registers" size="small" stripe><el-table-column prop="semester" label="学期" min-width="200"/><el-table-column label="状态" width="120"><template #default="{row}"><el-tag :type="row.status==='已注册'?'success':'warning'" size="small" round>{{row.status}}</el-tag></template></el-table-column><el-table-column prop="date" label="注册时间" width="140"/><el-table-column label="操作" width="120"><template #default="{row}"><el-button v-if="row.status==='待注册'" type="primary" size="small" round>注册</el-button><el-button v-else text type="primary" size="small">详情</el-button></template></el-table-column></el-table></el-tab-pane>
          <el-tab-pane label="培养计划"><el-button type="primary" size="small" round style="margin-bottom:12px">编辑计划</el-button><el-table :data="planItems" size="small" stripe><el-table-column prop="course" label="课程" min-width="180"/><el-table-column prop="credits" label="学分" width="60"/><el-table-column prop="type" label="类别" width="100"><template #default="{row}"><el-tag size="small" round>{{row.type}}</el-tag></template></el-table-column><el-table-column prop="status" label="状态" width="90"><template #default="{row}"><el-tag :type="row.status==='已完成'?'success':'info'" size="small" round>{{row.status}}</el-tag></template></el-table-column></el-table><div style="margin-top:12px;text-align:right;font-weight:600">已修: 24 / 要求: 32</div></el-tab-pane>
          <el-tab-pane label="变更导师"><el-button type="primary" size="small" round style="margin-bottom:12px">发起申请</el-button><el-table :data="advisorChanges" size="small" stripe><el-table-column prop="applyDate" label="申请日期" width="120"/><el-table-column prop="old" label="原导师" width="100"/><el-table-column prop="new" label="新导师" width="100"/><el-table-column prop="reason" label="原因" min-width="180"/><el-table-column prop="status" label="状态" width="100"><template #default="{row}"><el-tag :type="row.status==='已通过'?'success':'warning'" size="small" round>{{row.status}}</el-tag></template></el-table-column></el-table></el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">
import { ref } from 'vue'
const registers=ref([{semester:'2025-2026学年第二学期',status:'已注册',date:'2026-02-20'},{semester:'2025-2026学年第一学期',status:'已注册',date:'2025-09-05'}])
const planItems=ref([{course:'高级算法设计与分析',credits:3,type:'学位课',status:'已完成'},{course:'机器学习理论',credits:2,type:'学位课',status:'已完成'},{course:'学术英语写作',credits:2,type:'公共课',status:'已完成'},{course:'自然语言处理',credits:2,type:'选修课',status:'进行中'}])
const advisorChanges=ref([{applyDate:'2025-11-10',old:'张教授',new:'李教授',reason:'研究方向调整',status:'已通过'}])
</script>
<style scoped>.page-section{max-width:1000px}</style>
