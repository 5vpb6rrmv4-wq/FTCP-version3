<template>
  <div class="page-section">
    <div class="home-card"><div class="card-header"><span class="card-title"><span class="title-dot"></span>学位论文</span></div>
      <div class="card-body">
        <el-tabs type="border-card" tab-position="left">
          <el-tab-pane label="开题报告"><el-descriptions :column="2" border><el-descriptions-item label="论文题目">基于深度学习的图像识别算法研究与优化</el-descriptions-item><el-descriptions-item label="开题日期">2025-03-20</el-descriptions-item><el-descriptions-item label="开题结果"><el-tag type="success" round>通过</el-tag></el-descriptions-item><el-descriptions-item label="评审专家">王教授、赵教授、周教授</el-descriptions-item></el-descriptions><el-button type="primary" round style="margin-top:12px">查看开题报告</el-button></el-tab-pane>
          <el-tab-pane label="中期报告"><el-descriptions :column="2" border><el-descriptions-item label="论文题目">基于深度学习的图像识别算法研究与优化</el-descriptions-item><el-descriptions-item label="检查日期">2026-01-15</el-descriptions-item><el-descriptions-item label="检查结果"><el-tag type="success" round>通过</el-tag></el-descriptions-item><el-descriptions-item label="完成度">60%</el-descriptions-item></el-descriptions><el-button type="primary" round style="margin-top:12px">上传中期报告</el-button></el-tab-pane>
          <el-tab-pane label="评审报名"><el-alert title="报名开放: 2026年9月1日-15日" type="info" :closable="false"/><el-empty description="报名尚未开放" :image-size="60"/></el-tab-pane>
          <el-tab-pane label="评审管理"><el-empty description="暂无评审记录" :image-size="60"/></el-tab-pane>
          <el-tab-pane label="预答辩"><el-empty description="待安排" :image-size="60"/></el-tab-pane>
          <el-tab-pane label="答辩管理"><el-empty description="待安排" :image-size="60"/></el-tab-pane>
          <el-tab-pane label="优秀论文申请"><el-button type="primary" size="small" round>申请优秀论文</el-button><el-empty description="暂无申请记录" :image-size="40" style="margin-top:12px"/></el-tab-pane>
          <el-tab-pane label="论文存档"><el-alert title="请答辩通过后上传最终版" type="warning" :closable="false"/><el-empty description="暂无存档记录" :image-size="60"/></el-tab-pane>
        </el-tabs>
      </div>
    </div>
  </div>
</template>
<style scoped>.page-section{max-width:1100px}</style>
