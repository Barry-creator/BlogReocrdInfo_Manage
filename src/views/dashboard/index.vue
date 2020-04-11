<template>
  <div class="dashboard-container">
    <div class="dashboard-div">
      <el-row>
        <el-col :span="4">
          <div class="person-header-div">
            <span class="svg-container">
              <svg-icon
                icon-class="head-portrait"
                class="person-header"
              />
            </span>

          </div>
        </el-col>
        <el-col :span="20">
          <h3>{{ name }}</h3>
          <el-row class="count-info">
            <el-col :span="4">
              <span>
                5
              </span>
              <span class="small-size">
                文章
              </span>
              <span class="svg-container">
                <svg-icon icon-class="charts" />
              </span>
            </el-col>
            <el-col :span="4">
              <span>
                5
              </span>
              <span class="small-size">
                浏览量
              </span>
              <span class="svg-container">
                <svg-icon icon-class="charts" />
              </span>
            </el-col>
            <el-col :span="4">
              <span>
                5
              </span>
              <span class="small-size">
                评论
              </span>
              <span class="svg-container">
                <svg-icon icon-class="charts" />
              </span>
            </el-col>
          </el-row>
        </el-col>
      </el-row>
      <el-row>
        <el-col
          :span="24"
          class="btn-box"
        >
          <el-button type="primary">发布文章</el-button>
          <el-button type="primary">发布资讯</el-button>
          <el-button type="primary">评论管理</el-button>
          <el-button type="primary">文章列表</el-button>
          <el-button type="primary">日志管理</el-button>
          <el-button type="primary">实时列表</el-button>
        </el-col>
      </el-row>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  computed: {
    ...mapGetters([
      'name'
    ])
  }
}
</script>

<style lang="scss" scoped>
.dashboard {
  &-container {
    margin: 30px;
  }
  &-text {
    font-size: 30px;
    line-height: 46px;
  }
}
.dashboard-div {
  .el-button + .el-button {
    margin-left: 20px;
  }
  h3 {
    font-size: 30px;
    margin: 0;
    padding: 0;
    font-weight: 500;
    padding: 10px 0;
  }
  .small-size {
    font-size: 12px;
    color: #808080;
  }
  .person-header-div {
    text-align: center;
    .person-header {
      width: 100px;
      height: 100px;
      border-radius: 100%;
    }
  }
  .count-info {
    height: 48px;
    line-height: 47px;
    padding-top: 10px;
  }
  .btn-box {
    padding: 20px 56px 0;
  }
}
</style>
