<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>个人信息</span></div>
      <div class="card-body">
        <el-tabs type="border-card">
          <el-tab-pane label="基本信息"><el-form :model="form" label-width="100px"><el-row :gutter="20"><el-col :span="12"><el-form-item label="学号"><el-input v-model="form.id" disabled/></el-form-item><el-form-item label="姓名"><el-input v-model="form.name" disabled/></el-form-item><el-form-item label="性别"><el-radio-group v-model="form.gender" disabled><el-radio value="male">男</el-radio></el-radio-group></el-form-item><el-form-item label="出生日期"><el-input v-model="form.birth" disabled/></el-form-item><el-form-item label="民族"><el-input v-model="form.ethnic" disabled/></el-form-item></el-col><el-col :span="12"><el-form-item label="身份证"><el-input v-model="form.idcard" disabled/></el-form-item><el-form-item label="学院"><el-input v-model="form.college" disabled/></el-form-item><el-form-item label="专业"><el-input v-model="form.major" disabled/></el-form-item><el-form-item label="导师"><el-input v-model="form.advisor" disabled/></el-form-item><el-form-item label="入学日期"><el-input v-model="form.enroll" disabled/></el-form-item></el-col></el-row><el-divider/><el-form-item label="手机"><el-input v-model="form.phone"/></el-form-item><el-form-item label="邮箱"><el-input v-model="form.email"/></el-form-item><el-form-item><el-button type="primary" round>保存</el-button></el-form-item></el-form></el-tab-pane>
          <el-tab-pane label="学籍信息"><el-descriptions :column="2" border><el-descriptions-item label="学号">2023301001</el-descriptions-item><el-descriptions-item label="姓名">张三</el-descriptions-item><el-descriptions-item label="培养层次">硕士研究生</el-descriptions-item><el-descriptions-item label="学习形式">全日制</el-descriptions-item><el-descriptions-item label="学制">3年</el-descriptions-item><el-descriptions-item label="学籍状态"><el-tag type="success" round>在籍</el-tag></el-descriptions-item></el-descriptions></el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>
<script setup lang="ts">import {reactive} from 'vue'
const form=reactive({id:'2023301001',name:'张三',gender:'male',birth:'2000-03-15',ethnic:'汉族',idcard:'32010220000315****',college:'计算机学院',major:'计算机科学与技术',advisor:'李教授',enroll:'2023-09-01',phone:'13800138000',email:'zhangsan@cqupt.edu.cn'})
</script>
<style scoped>.page-section{max-width:1000px}</style>
