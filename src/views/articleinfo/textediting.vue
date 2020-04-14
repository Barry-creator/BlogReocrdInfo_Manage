<template>
  <div class="app-container">
    <el-form>
      <el-form-item label="文章标题">
        <el-input placeholder="请输入文章标题" />
      </el-form-item>
      <el-form-item label="简要描述">
        <textarea />
        </el-form-item>
      <el-form-item label="作者">
        <el-input disabled="" />
      </el-form-item>
      <el-form-item label="定时发布">
        <el-switch />
      </el-form-item>
      <el-form-item label="发布时间">
        <el-date-picker
          type="datetime"
          placeholder="选择日期时间"
        />
      </el-form-item>
    </el-form>
  </div>
</template>
