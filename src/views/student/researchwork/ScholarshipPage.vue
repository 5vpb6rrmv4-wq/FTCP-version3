<template>
<div class="page-section"><div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>奖助学金</span></div><div class="card-body"><el-tabs type="border-card">
<el-tab-pane label="奖学金申请"><el-button type="primary" size="small" round style="margin-bottom:12px" @click="openAdd">新增申请</el-button>
<el-table :data="apps" size="small" stripe empty-text="暂无申请记录">
<el-table-column prop="name" label="名称" min-width="160"/>
<el-table-column prop="level" label="级别" width="90"/>
<el-table-column prop="date" label="日期" width="110"/>
<el-table-column label="状态" width="90"><template #default="{row}"><el-tag :type="row.status==='已通过'?'success':'warning'" size="small" round>{{row.status}}</el-tag></template></el-table-column>
<el-table-column label="操作" width="180"><template #default="{row}"><el-button text type="primary" size="small" @click="viewDetail(row)">详情</el-button><el-button text type="primary" size="small" @click="viewDetail(row);dlg.mode='edit';dlg.initEdit(row)">编辑</el-button><el-button text type="success" size="small" @click="dlg.row=row;dlg.mode='print';dlg.show=true">打印</el-button></template></el-table-column>
</el-table></el-tab-pane>
<el-tab-pane label="个人评优"><el-table :data="awards" size="small" stripe><el-table-column prop="name" label="名称" min-width="160"/><el-table-column prop="level" label="级别" width="90"/><el-table-column prop="date" label="日期" width="110"/><el-table-column label="操作" width="160"><template #default="{row}"><el-button text type="primary" size="small" @click="viewDetail(row)">详情</el-button><el-button text type="success" size="small" @click="dlg.row=row;dlg.mode='print';dlg.show=true">打印</el-button></template></el-table-column></el-table></el-tab-pane>
<el-tab-pane label="证明打印"><el-table :data="certs" size="small" stripe><el-table-column prop="name" label="名称" min-width="160"/><el-table-column prop="year" label="年度" width="80"/><el-table-column label="操作" width="120"><template #default="{row}"><el-button type="primary" size="small" round @click="dlg.row=row;dlg.mode='print';dlg.show=true;dlg.title='奖学金证明'">打印证明</el-button></template></el-table-column></el-table></el-tab-pane>
</el-tabs>

<!-- Detail/Edit/Print Dialog -->
<el-dialog v-model="dlg.show" :title="dlg.title" width="600px">
  <template v-if="dlg.mode==='view'"><el-descriptions :column="2" border size="small"><el-descriptions-item v-for="f in fields" :key="f.key" :label="f.label"><span>{{dlg.row[f.key]||'-'}}</span></el-descriptions-item></el-descriptions></template>
  <template v-else-if="dlg.mode==='edit'"><el-form :model="dlg.row" label-width="90px"><el-form-item v-for="f in fields" :key="f.key" :label="f.label"><el-input v-model="dlg.row[f.key]"/></el-form-item></el-form></template>
  <template v-else-if="dlg.mode==='print'"><div style="text-align:center"><h3 style="color:#153D97;margin-bottom:16px">{{dlg.title}}</h3><table style="width:100%;border-collapse:collapse;font-size:13px"><tr v-for="f in fields" :key="f.key" style="border-bottom:1px solid #f0f0f0"><td style="padding:8px 12px;font-weight:600;width:100px;background:#f8fafc">{{f.label}}</td><td style="padding:8px 12px">{{dlg.row[f.key]||'-'}}</td></tr></table><p style="margin-top:20px;color:#94a3b8;font-size:11px">打印时间: {{new Date().toLocaleString()}}</p></div></template>
  <template #footer><span v-if="dlg.mode==='view'"><el-button type="warning" @click="dlg.mode='edit'">编辑</el-button><el-button type="success" @click="dlg.mode='print'">打印</el-button><el-button @click="dlg.show=false">关闭</el-button></span><span v-else-if="dlg.mode==='edit'"><el-button @click="dlg.mode='view'">取消</el-button><el-button type="primary" @click="saveEdit">保存</el-button></span><span v-else><el-button type="primary" @click="window.print()">打印</el-button><el-button @click="dlg.mode='view'">返回</el-button></span></template>
</el-dialog>
</div></div></div></template>
<script setup lang="ts">
import { ref, reactive } from 'vue'
const apps=ref([{id:1,name:'国家奖学金',level:'国家级',date:'2026-03-01',status:'审核中',amount:'20000',dept:'教育部'},{id:2,name:'学业奖学金一等奖',level:'校级',date:'2025-10-15',status:'已通过',amount:'8000',dept:'研究生院'}])
const awards=ref([{id:1,name:'优秀研究生',level:'校级',date:'2026-04-10',status:'已通过'}])
const certs=ref([{id:1,name:'学业奖学金一等奖',year:'2025'},{id:2,name:'国家奖学金',year:'2026'}])
const fields=[{key:'name',label:'名称'},{key:'level',label:'级别'},{key:'date',label:'日期'},{key:'status',label:'状态'},{key:'amount',label:'金额(元)'},{key:'dept',label:'主管部门'}]
const dlg=reactive({show:false,title:'详情',mode:'view',row:{} as any})
function viewDetail(row:any){dlg.row={...row};dlg.title='详情';dlg.mode='view';dlg.show=true}
function openAdd(){const r={id:Date.now(),name:'',level:'校级',date:new Date().toISOString().split('T')[0],status:'审核中',amount:'',dept:''};dlg.row=r;dlg.title='新增申请';dlg.mode='edit';dlg.show=true}
function saveEdit(){const idx=apps.value.findIndex(a=>a.id===dlg.row.id);if(idx>=0)apps.value[idx]=dlg.row;else apps.value.unshift(dlg.row);dlg.show=false}
</script>
<style scoped>.page-section{max-width:1000px}</style>
