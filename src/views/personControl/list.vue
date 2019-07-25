<template>
  <div>
    <!-- 工具 -->
    <div class="toolBar m-20b">
      <el-input />
      <el-button type="success" class="fr">搜索</el-button>
      <el-button type="success" class="fr" @click="action('add')">新增</el-button>
    </div>
    <!-- 表单 -->
    <el-table :data="tableData" border style="width: 100%">
      <el-table-column fixed prop="date" label="日期" width="150" />
      <el-table-column prop="name" label="姓名" width="120" />
      <el-table-column prop="province" label="省份" width="120" />
      <el-table-column prop="city" label="市区" width="120" />
      <el-table-column prop="address" label="地址" width="300" />
      <el-table-column prop="zip" label="邮编" width="120" />
      <el-table-column fixed="right" label="操作" width="100">
        <template slot-scope="scope">
          <el-button type="text" size="small" @click="action(scope.row)">查看</el-button>
          <el-button type="text" size="small" @click="del(scope.row.id)">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
    <!-- v-if 目的 等待子组件的执行 直到父组件执行完毕  -->
    <el-dialog v-if="dialogVisible" :visible.sync="dialogVisible" title="提示" width="70%">
      <add :item="item" @confirm="confirm" @cancel="cancel"/>
    </el-dialog>
  </div>
</template>

<script>
import add from './components/add.vue'
export default {
  components: {
    add
  },
  data() {
    return {
      dialogVisible: false,
      item: {},
      tableData: [
        {
          date: '2016-05-02',
          name: '王小虎',
          province: '上海',
          city: '普陀区777777',
          address: '上海市普56789弄',
          zip: 44444,
          id: '1'
        },
        {
          date: '2016-05-04',
          name: '李小华',
          province: '上海',
          city: '普陀区00000',
          address: '上海市普陀区金沙江路 12345 弄',
          zip: 33333,
          id: '2'

        },
        {
          date: '2016-05-01',
          name: '张三',
          province: '上海',
          city: '普陀区43434343',
          address: '上海市普陀区金沙江路 1519 弄',
          zip: 22222,
          id: '3'
        },
        {
          date: '2016-05-03',
          name: '王二',
          province: '上海',
          city: '普陀区12345',
          address: '上海区金沙江路 203922 弄',
          zip: 11111,
          id: '4'
        }
      ]
    }
  },
  methods: {
    action(item) {
      // this.item = JSON.parse(JSON.stringify(item))
      this.item = Object.assign({}, item)
      this.dialogVisible = true
    },
    confirm(item) {
      !item.id && this.tableData.unshift(item)
      item.id && this.tableData.forEach(v => {
        v.id === item.id && (v = item)
      })
      this.dialogVisible = false
    },
    cancel() {
      this.dialogVisible = false
    },
    del(id) {
      this.tableData = this.tableData.filter(v => id !== v.id)
    }
  }
}
</script>

<style lang="scss" scoped>
</style>
