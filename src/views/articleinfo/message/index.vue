<template>
  <div class="app-container">
    <el-row style="margin-top:20px;">
      <el-col :span="24">
        <el-form
          size="mini"
          :inline="true"
        >
          <el-form-item label="文章分类">
            <el-select placeholder="请选择所属专题">
              <el-option
                label="区域一"
                value="shanghai"
              />
            </el-select>
          </el-form-item>
          <el-form-item label="状态">
            <el-select placeholder="请选择状态">
              <el-option
                label="待发布"
                value="0"
              />
              <el-option
                label="已发布"
                value="1"
              />
              <el-option
                label="已撤回"
                value="2"
              />
            </el-select>
          </el-form-item>
          <el-form-item label="发布日期">
            <el-col :span="11">
              <el-form-item prop="">
                <el-date-picker
                  type="date"
                  placeholder="选择日期"
                  style="width: 100%;"
                />
              </el-form-item>
            </el-col>
            <el-col
              class="line"
              :span="1"
            >-</el-col>
            <el-col :span="11">
              <el-form-item prop="">
                <el-date-picker
                  type="date"
                  placeholder="选择日期"
                  style="width: 100%;"
                />
              </el-form-item>
            </el-col>
          </el-form-item>

          <el-form-item label="">
            <el-button
              type="primary"
              icon="el-icon-search"
            >搜索</el-button>
          </el-form-item>
        </el-form>

      </el-col>
    </el-row>
    <el-table
      :data="tableData"
      style="width: 100%"
    >
      <!--<el-table-column
        type="selection"
        width="55"
      />-->
      <el-table-column
        label="标题"
        width="150"
        align="center"
      >
        <template slot-scope="scope">
          <el-popover
            trigger="hover"
            placement="top"
          >
            <p>描述: {{ scope.row.desc }}</p>
            <div
              slot="reference"
              class="name-wrapper"
            >
              <span>{{ scope.row.title }}</span>
            </div>
          </el-popover>

        </template>
      </el-table-column>
      <el-table-column
        label="文章分类"
        width="180"
        align="center"
      >
        <template slot-scope="scope">
          <span>{{ scope.row.articleclass }}</span>
        </template>
      </el-table-column>
      <el-table-column
        label="发布人"
        width="180"
        align="center"
      >
        <template slot-scope="scope">
          <span>{{ scope.row.name }}</span>
        </template>
      </el-table-column>
      <el-table-column
        label="状态"
        width="100"
        align="center"
      >
        <template slot-scope="scope">
          <el-tag :type="scope.row.status | statusFilter">{{ getStatusStr(scope.row.status) }}</el-tag>
        </template>
      </el-table-column>
      <el-table-column
        label="阅读量"
        width="100"
        align="center"
      >
        <template slot-scope="scope">
          <span>{{ scope.row.reading }}</span>
        </template>
      </el-table-column>
      <el-table-column
        label="日期"
        width="180"
        align="center"
      >
        <template slot-scope="scope">
          <i class="el-icon-time" />
          <span style="margin-left: 10px">{{ scope.row.date }}</span>
        </template>
      </el-table-column>

      <!--
           <el-table-column
        label="姓名"
        width="180"
        align="center"
      >
         <template slot-scope="scope">
          <el-popover
            trigger="hover"
            placement="top"
          >
            <p>姓名: {{ scope.row.name }}</p>
            <p>住址: {{ scope.row.address }}</p>
            <div
              slot="reference"
              class="name-wrapper"
            >
              <el-tag size="medium">{{ scope.row.name }}</el-tag>
            </div>
          </el-popover>
        </template>
        </el-table-column>
       -->

      <el-table-column
        label="操作"
        align="left"
      >
        <template slot="header">
          <el-input
            v-model="search"
            size="mini"
            placeholder="输入关键字搜索"
          />
        </template>
        <template slot-scope="scope">
          <el-button
            size="mini"
            icon="el-icon-edit"
            @click="handleEdit(scope.$index, scope.row)"
          />
          <el-button
            size="mini"
            icon="el-icon-delete"
            type="danger"
            @click="handleEdit(scope.$index, scope.row)"
          />
          <el-button
            v-if="scope.row.status==='0'||scope.row.status==='2'"
            size="mini"
            @click="handleEdit(scope.$index, scope.row)"
          >发布</el-button>
          <el-button
            v-if="scope.row.status==='1'"
            size="mini"
            type="warning"
            @click="handleEdit(scope.$index, scope.row)"
          >取消发布</el-button>
          <el-button
            size="mini"
            type="primary"
          >详情</el-button>
        </template>
      </el-table-column>
    </el-table>
  </div>

</template>

<script>
export default {
  filters: {
    statusFilter(status) {
      const statusMap = {
        1: 'success',
        0: 'gray',
        2: 'danger'
      }
      return statusMap[status]
    }
  },
  data() {
    return {
      tableData: [{
        date: '2016-05-02',
        name: '王小虎',
        title: '测试1',
        articleclass: '技术/算法',
        status: '1',
        reading: 0,
        desc: '啊发发是单身撒发'
      }, {
        date: '2016-05-04',
        name: '王小虎',
        title: '测试1',
        articleclass: '技术/算法',
        status: '0',
        reading: 0,
        desc: '啊发发是单身撒发'
      }, {
        date: '2016-05-01',
        name: '王小虎',
        title: '测试1',
        articleclass: '技术/算法',
        status: '1',
        reading: 0,
        desc: '啊发发是单身撒发'
      }, {
        date: '2016-05-03',
        name: '王小虎',
        title: '测试1',
        articleclass: '技术/算法',
        status: '2',
        reading: 0,
        desc: '啊发发是单身撒发'
      }]
    }
  },
  methods: {
    handleEdit(index, row) {
      console.log(index, row)
    },
    getStatusStr(value) {
      let text = ''
      switch (value) {
        case '0':
          text = '待发布'
          break
        case '1':
          text = '已发布'
          break
        case '2':
          text = '已撤回'
          break
        default:
          break
      }
      return text
    }
  }
}
</script>
