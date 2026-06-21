<template>
<div class="page-section"><div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>招生管理</span></div><div class="card-body"><el-tabs type="border-card">
<el-tab-pane label="招生目录"><el-table :data="catalog" size="small" stripe><el-table-column prop="name" label="专业名称" min-width="160"/><el-table-column prop="dir" label="研究方向" min-width="160"/><el-table-column prop="advisor" label="导师" width="100"/><el-table-column prop="quota" label="拟招人数" width="80"/><el-table-column label="操作" width="80"><template #default><el-button text type="primary" size="small">编辑</el-button></template></el-table-column></el-table></el-tab-pane>
<el-tab-pane label="报名管理"><el-table :data="regs" size="small" stripe><el-table-column prop="id" label="考生编号" width="130"/><el-table-column prop="name" label="姓名" width="80"/><el-table-column prop="type" label="类别" width="80"/><el-table-column prop="status" label="状态" width="90"><template #default><el-tag type="success" size="small" round>已确认</el-tag></template></el-table-column><el-table-column label="操作" width="120"><template #default><el-button text type="primary" size="small">查看</el-button><el-button text type="primary" size="small">审核</el-button></template></el-table-column></el-table></el-tab-pane>
<el-tab-pane label="成绩管理"><el-table :data="scores" size="small" stripe><el-table-column prop="id" label="考生编号" width="130"/><el-table-column prop="name" label="姓名" width="80"/><el-table-column prop="first" label="初试" width="70"/><el-table-column prop="second" label="复试" width="70"/><el-table-column prop="total" label="综合" width="70"/><el-table-column prop="status" label="状态" width="90"><template #default><el-tag type="warning" size="small" round>待录取</el-tag></template></el-table-column></el-table></el-tab-pane>
</el-tabs></div></div></div></template>
<script setup lang="ts">
import {ref} from "vue"
const catalog=ref([{name:"计算机科学与技术",dir:"人工智能",advisor:"李教授",quota:5},{name:"计算机科学与技术",dir:"数据科学",advisor:"王教授",quota:3}])
const regs=ref([{id:"20261001001",name:"考生A",type:"统考",status:"已确认"},{id:"20261001002",name:"考生B",type:"推免",status:"已确认"}])
const scores=ref([{id:"20261001001",name:"考生A",first:385,second:88,total:473,status:"待录取"},{id:"20261001002",name:"考生B",first:402,second:92,total:494,status:"待录取"}])
</script>
<style scoped>.page-section{max-width:1200px}</style>