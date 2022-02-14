<template>
  <div>
    <MyHeader
      background="lightyellow"
      color="green"
      title="TabBar案例"
    ></MyHeader>
    <MyTabBar :arr="tabList"></MyTabBar>
    <!-- ! (父)2 传入数据 -->
  </div>
</template>

<script>
import MyHeader from "./components/MyHeader.vue";
// 目标:完成底部封装
// 1.MyTabBar.vue 组件标签+样式 准备
// 2.字体图标引入
// 3.准备底部数据
// 4.使用MyTabBar组件,传入数据(父->子),循环产生底部导航
// 5.子组件内props自定义检验规则(2-5项)
import MyTabBar from "./components/MyTabBar.vue";
export default {
  data() {
    return {
      tabList: [
        // 底部导航的数据
        {
          iconText: "icon-shangpinliebiao",
          text: "商品列表",
          componentName: "MyGoodsList",
        },
        {
          iconText: "icon-sousuo",
          text: "商品搜索",
          componentName: "MyGoodsSearch",
        },
        {
          iconText: "icon-user",
          text: "我的信息",
          componentName: "MyUserInfo",
        },
      ],
    };
  },
  components: {
    MyHeader,
    MyTabBar,
  },
};
</script>

<style>
</style>