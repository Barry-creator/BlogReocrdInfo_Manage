<template>
  <div class="dashboard-container">
    <div class="dashboard-div">
      <el-row>
        <el-col :span="3">
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
    <div class="num_desc_box">
      <div class="mouth_count_box">
        <div>
          <label>
            <span>4</span>
            <span>月</span>
          </label>
          <div>
            <span class="diff_act">30</span><span>篇</span>
          </div>
        </div>
        <div style="border:0" />
      </div>
      <div class="list_article">
        <el-divider content-position="left">最近发布</el-divider>
        <el-table
          :data="tableData"
          style="width: 100%"
          :show-header="false"
        >
          <el-table-column
            prop="date"
            label="日期"
            width="180"
          >
            <template slot-scope="scope">
              <i class="el-icon-time" />
              <span style="margin-left: 10px">{{ scope.row.date }}</span>
            </template>
          </el-table-column>
          <el-table-column
            prop="name"
            label="姓名"
            width="180"
          />
          <el-table-column
            prop="address"
            label="地址"
          />
        </el-table>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters } from 'vuex'

export default {
  name: 'Dashboard',
  data() {
    return {
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1518 弄'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1517 弄'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1519 弄'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        address: '上海市普陀区金沙江路 1516 弄'
      }]
    }
  },
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
    width: 100px;
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
    padding: 20px 0;
  }
}
.num_desc_box {
  width: 100%;
  height: 400px;
  border: 1px solid #ccc;
  .mouth_count_box {
    width: 30%;
    height: 100%;
    border-right: 1px solid #ccc;
    float: left;
    > div {
      margin: 0 20px;
      border-bottom: 1px solid #ccc;
      height: 48%;
      label {
        display: block;
        padding: 10px 0;
        color: #ccc;
      }
      .diff_act {
        color: yellowgreen;
        font-size: 18px;
      }
      .diff_act + span {
        font-size: 13px;
      }
    }
  }
  .list_article {
    width: 65%;
    height: 400px;
    float: left;
    padding-left: 20px;
    tr {
      height: 30px;
    }
  }
}
</style>
