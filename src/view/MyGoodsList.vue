<template>
  <div>
    <!-- c1 父 (父传子) -->
    <MyTable :arr="list">
      <template #header
        ><th>#</th>
        <th>商品名称</th>
        <th>价格</th>
        <th>标签</th>
        <th>操作</th>
      </template>
      <!-- scoped的值:{row:obj} -->
      <!-- <template v-slot:body="scope"> -->
      <template #body="scope">
        <td>{{ scope.row.id }}</td>
        <td>{{ scope.row.goods_name }}</td>
        <td>{{ scope.row.goods_price }}</td>
        <td>{{ scope.row.tags }}</td>
        <td>
          <button class="btn btn-danger btn-sm">删除</button>
        </td>
      </template>
    </MyTable>
  </div>
</template>

<script>
import MyTable from "../components/MyTable.vue";
import axios from "axios";
axios.defaults.baseURL = "https://www.escook.cn";
// 目标:  循环商品列表表格
// 1.封装MyTable.vue 整体表格组件- 一套标签和样式
// 2.axios 请求数据
// 3.传入MyTable 组件里循环tr显示数据
export default {
  data() {
    return {
      list: [],
    };
  },
  components: {
    MyTable,
  },
  created() {
    axios({
      url: "/api/goods",
    }).then((res) => {
      // console.log(res);
      this.list = res.data.data;
    });
  },
};
</script>

<style>
</style>