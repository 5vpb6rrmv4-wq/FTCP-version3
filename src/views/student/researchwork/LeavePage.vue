<template>
<div class="page-section"><div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>日常管理</span><el-button type="primary" size="small" round @click="openAdd">请假申请</el-button></div><div class="card-body">
<el-table :data="leaves" size="small" stripe empty-text="暂无记录">
<el-table-column prop="type" label="类型" width="80"/><el-table-column prop="reason" label="事由" min-width="180"/><el-table-column prop="start" label="开始" width="110"/><el-table-column prop="end" label="结束" width="110"/><el-table-column prop="days" label="天数" width="60"/>
<el-table-column label="状态" width="90"><template #default="{row}"><el-tag :type="row.status==='已批准'?'success':row.status==='审核中'?'warning':'info'" size="small" round>{{row.status}}</el-tag></template></el-table-column>
<el-table-column label="操作" width="180"><template #default="{row}"><el-button text type="primary" size="small" @click="viewDetail(row)">详情</el-button><el-button v-if="row.status==='审核中'" text type="warning" size="small" @click="row.status='已撤销';$message.success('已撤销')">撤销</el-button><el-button v-if="row.status==='已批准'" text type="success" size="small" @click="row.status='已销假';$message.success('销假成功')">销假</el-button><el-button text type="success" size="small" @click="dlg.row=row;dlg.mode='print';dlg.show=true">打印</el-button></template></el-table-column>
</el-table>

<el-dialog v-model="dlg.show" :title="dlg.title" width="550px">
  <template v-if="dlg.mode==='view'"><el-descriptions :column="2" border size="small"><el-descriptions-item v-for="f in leaveFields" :key="f.key" :label="f.label"><span>{{dlg.row[f.key]||'-'}}</span></el-descriptions-item></el-descriptions></template>
  <template v-else-if="dlg.mode==='edit'"><el-form :model="dlg.row" label-width="90px"><el-form-item label="请假类型"><el-select v-model="dlg.row.type" style="width:100%"><el-option label="事假" value="事假"/><el-option label="病假" value="病假"/><el-option label="公假" value="公假"/></el-select></el-form-item><el-form-item label="开始日期"><el-date-picker v-model="dlg.row.start" type="date" style="width:100%"/></el-form-item><el-form-item label="结束日期"><el-date-picker v-model="dlg.row.end" type="date" style="width:100%"/></el-form-item><el-form-item label="请假事由"><el-input v-model="dlg.row.reason" type="textarea" :rows="3"/></el-form-item></el-form></template>
  <template v-else><div style="text-align:center"><h3 style="color:#153D97;margin-bottom:16px">请假单</h3><table style="width:100%;border-collapse:collapse;font-size:13px"><tr v-for="f in leaveFields" :key="f.key" style="border-bottom:1px solid #f0f0f0"><td style="padding:8px 12px;font-weight:600;width:100px;background:#f8fafc">{{f.label}}</td><td style="padding:8px 12px">{{dlg.row[f.key]||'-'}}</td></tr></table><p style="margin-top:20px;color:#94a3b8;font-size:11px">{{new Date().toLocaleString()}}</p></div></template>
  <template #footer><span v-if="dlg.mode==='view'"><el-button type="warning" @click="dlg.mode='edit'">编辑</el-button><el-button type="success" @click="dlg.mode='print'">打印</el-button><el-button @click="dlg.show=false">关闭</el-button></span><span v-else-if="dlg.mode==='edit'"><el-button @click="dlg.mode='view'">取消</el-button><el-button type="primary" @click="saveEdit">提交</el-button></span><span v-else><el-button type="primary" @click="window.print()">打印</el-button><el-button @click="dlg.mode='view'">返回</el-button></span></template>
</el-dialog>
</div></div></div></template>
<script setup lang="ts">
import {ref,reactive} from 'vue';import {ElMessage as $m} from 'element-plus';
const leaves=ref([{id:1,type:'事假',reason:'回家探亲',start:'2026-05-01',end:'2026-05-05',days:5,status:'已批准',approver:'李教授'},{id:2,type:'病假',reason:'感冒发烧',start:'2026-06-10',end:'2026-06-11',days:2,status:'审核中',approver:'待审批'}])
const leaveFields=[{key:'type',label:'类型'},{key:'reason',label:'事由'},{key:'start',label:'开始日期'},{key:'end',label:'结束日期'},{key:'days',label:'天数'},{key:'status',label:'状态'},{key:'approver',label:'审批人'}]
const dlg=reactive({show:false,title:'详情',mode:'view',row:{} as any})
function viewDetail(row:any){dlg.row={...row};dlg.title='详情';dlg.mode='view';dlg.show=true}
function openAdd(){const r={id:Date.now(),type:'事假',reason:'',start:'',end:'',days:0,status:'审核中',approver:'待审批'};dlg.row=r;dlg.title='请假申请';dlg.mode='edit';dlg.show=true}
function saveEdit(){const idx=leaves.value.findIndex(l=>l.id===dlg.row.id);if(idx>=0)leaves.value[idx]=dlg.row;else leaves.value.unshift(dlg.row);dlg.show=false;$m.success('已提交')}
</script>
<style scoped>.page-section{max-width:1000px}</style>
