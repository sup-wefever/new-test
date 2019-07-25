<template>
  <div>
    <div class="toolBar m-20b">
      <el-input />
      <el-button type="success" class="fr">搜索</el-button>
      <el-button type="success" class="fr" @click="action('add')">新增</el-button>
    </div>
    <el-table :data="tableData" style="width: 100%">
      <el-table-column prop="date" label="日期" width="180"></el-table-column>
      <el-table-column prop="name" label="姓名" width="180"></el-table-column>
      <el-table-column prop="address" label="地址"></el-table-column>
    </el-table>

    <!-- <el-dialog v-if="dialogVisible" :visible.sync="dialogVisible" title="提示" width="70%">
      <add :item="item" @confirm="confirm" @cancel="cancel"/>
    </el-dialog> -->
  </div>
</template>

<script>
export default {
  data() {
    return {
      tableData: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    }
    // methods: {
    //     action(item) {

    //     }
    // },
  }
};
</script>

<style lang="scss" scoped>
</style>