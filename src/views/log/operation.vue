<template>
  <div class="app-container">
    <el-row style="margin-top:20px;">
      <el-col :span="24">
        <el-form
          size="mini"
          :inline="true"
        >
          <el-form-item label="状态">
            <el-select placeholder="请选择状态">
              <el-option
                label="成功"
                value="0"
              />
              <el-option
                label="失败"
                value="1"
              />
            </el-select>
          </el-form-item>
          <el-form-item label="操作日期">
            <el-col>
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
        label="操作类型"
        width="150"
        align="center"
      >
        <template slot-scope="scope">
          <span>{{ scope.row.type }}</span>
        </template>
      </el-table-column>
      <el-table-column
        label="数据库"
        width="150"
        align="center"
      >
        <template slot-scope="scope">
          <span>{{ scope.row.databasetype }}</span>
        </template>
      </el-table-column>
      <el-table-column
        label="操作内容"
        width="500"
        align="center"
      >
        <template slot-scope="scope">
          <span>{{ scope.row.content }}</span>
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
        label="日期"
        width="180"
        align="center"
      >
        <template slot-scope="scope">
          <i class="el-icon-time" />
          <span style="margin-left: 10px">{{ scope.row.date }}</span>
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
        0: 'danger'
      }
      return statusMap[status]
    }
  },
  data() {
    return {
      tableData: [{
        date: '2016-05-02',
        type: 'insert',
        content: '啊发发是单身撒发',
        status: '1',
        databasetype: 'mysql'
      }, {
        date: '2016-05-02',
        type: 'insert',
        content: '啊发发是单身撒发',
        status: '1',
        databasetype: 'mysql'
      }, {
        date: '2016-05-02',
        type: 'insert',
        content: '啊发发是单身撒发',
        status: '1',
        databasetype: 'mysql'
      }, {
        date: '2016-05-02',
        type: 'insert',
        content: '啊发发是单身撒发',
        status: '1',
        databasetype: 'mysql'
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
          text = '失败'
          break
        case '1':
          text = '成功'
          break
        default:
          break
      }
      return text
    }
  }
}
</script>
