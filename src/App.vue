<template>
  <el-table :data="tableData" style="width: 100%">
    <el-table-column prop="date" label="日期" width="180"> </el-table-column>
    <el-table-column prop="name" label="姓名" width="180"> </el-table-column>
    <el-table-column prop="address" label="地址"> </el-table-column>
    <el-table-column label="按钮">
      <template #default="{ row }">
        <el-button v-show="row.isShow"> 按钮 </el-button>
      </template>
    </el-table-column>
  </el-table>
</template>

<script>
import axios from "axios";
import { onMounted, ref } from "vue";
export default {
  setup() {
    const tableData = ref([]);
    onMounted(() => {
      axios.get("https://assets.winerlu.com/temp/data.json").then((res) => {
        tableData.value = res.data;
      });
    });
    return {
      tableData
    };
  },
};
</script>
