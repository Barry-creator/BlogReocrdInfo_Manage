<template>
  <div class="app-container">
    <div style="width:100%">
      <el-input
        v-model="filterText"
        placeholder="请输入关键字进行检索"
        style="margin-bottom:20px;width:300px"
      />
    </div>
    <div class="tree_box">
      <el-tree
        ref="tree2"
        :data="data2"
        :props="defaultProps"
        :filter-node-method="filterNode"
        class="filter-tree"
        default-expand-all
        highlight-current
        @node-click="showform"
      />
    </div>
    <transition name="el-fade-in-linear">
      <div
        v-show="isShow"
        class="tree_form"
      >
        <el-form
          ref="treeForm"
          :model="treeForm"
        >
          <el-form-item
            label="类别名称"
            label-width="100px"
            required
            hide-required-asterisk="true"
          >
            <el-input
              v-model="treeForm.dicMean"
              placeholder="请输入类别名称"
            />
          </el-form-item>
          <el-form-item
            label="启用"
            label-width="100px"
          >
            <el-switch v-model="treeForm.isenable" />
          </el-form-item>
          <el-form-item
            label=""
            style="text-align:center;"
          >
            <el-button
              type="primary"
              @click.native.prevent="append(onval)"
            >保存</el-button>
          </el-form-item>
        </el-form>
      </div>
    </transition>

  </div>
</template>

<script>
export default {

  data() {
    return {
      filterText: '',
      onval: null,
      isShow: false,
      data2: [{
        id: 1,
        label: 'Level one 1',
        children: [{
          id: 4,
          label: 'Level two 1-1',
          children: [{
            id: 9,
            label: 'Level three 1-1-1'
          }, {
            id: 10,
            label: 'Level three 1-1-2'
          }]
        }]
      }, {
        id: 2,
        label: 'Level one 2',
        children: [{
          id: 5,
          label: 'Level two 2-1'
        }, {
          id: 6,
          label: 'Level two 2-2'
        }]
      }, {
        id: 3,
        label: 'Level one 3',
        children: [{
          id: 7,
          label: 'Level two 3-1'
        }, {
          id: 8,
          label: 'Level two 3-2'
        }]
      }],
      defaultProps: {
        children: 'children',
        label: 'label'
      },
      treeForm: {
        dicMean: '',
        dicCode: 0,
        isenable: true
      }
    }
  },
  watch: {
    filterText(val) {
      this.$refs.tree2.filter(val)
    }
  },

  methods: {
    filterNode(value, data) {
      if (!value) return true
      return data.label.indexOf(value) !== -1
    },
    showform(data, node, dom) {
      // debugger
      if (!node.childNodes || node.childNodes.length === 0) {
        // debugger
        this.onval = data
        this.treeForm.dicCode = data.id
        this.isShow = true
      }
    },
    append(data) {
      // debugger
      this.treeForm.dicCode = data.dicCode++
      const newChild = { id: this.treeForm.dicCode, label: this.treeForm.dicMean, children: [] }
      if (!data.children) {
        this.$set(data, 'children', [])
      }
      data.children.push(newChild)
    }
  }
}
</script>
<style lang="scss" scoped>
.tree_box,
.tree_form {
  width: 300px;
  height: auto;
  float: left;
}
</style>
