<template>
  <div class="app-container">
    <el-form>
      <el-form-item label="文章标题">
        <el-input placeholder="请输入文章标题" />
      </el-form-item>
      <el-form-item label="简要描述">
        <el-input type="textarea" />
      </el-form-item>
      <el-form-item label="文章作者">
        <el-input
          disabled=""
          style="width:224px"
        />
      </el-form-item>
      <el-form-item label="专题类型">
        <el-select placeholder="请选择专题类型">
          <el-option value="技术">技术</el-option>
        </el-select>
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
      <el-form-item label="推荐指数">
        <el-rate style="display:inline-block" />
      </el-form-item>
      <el-form-item
        prop=""
        style="margin-bottom: 30px;"
      >
        <Tinymce :height="400" />
      </el-form-item>
      <el-form-item
        label=""
        style="text-align:right"
      >
        <el-button type="primary">保存</el-button>
        <el-button type="plain">取消</el-button>
      </el-form-item>
    </el-form>

  </div>
</template>
<script>
import Tinymce from '@/components/Tinymce'
export default {
  name: 'Textediting',
  components: { Tinymce }
}
</script>
