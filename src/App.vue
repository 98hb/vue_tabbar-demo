<template>
  <div>
    <MyHeader
      background="lightyellow"
      color="green"
      title="TabBar案例"
    ></MyHeader>
    <div class="main">
      <component :is="comName"> </component>
    </div>
    <MyTabBar :arr="tabList" @changeCom="changeComFn"></MyTabBar>
    <!-- ! (父)a2 传入数据 -->
  </div>
</template>

<script>
// 目标:切换组件显示
// 1.创建组件 - 编写内容
// 2.引入App.vue显示
// 3.挂载点设置is
// 4.切换comName的值
// 5.底部导航点击 - MyTabBar.vue里
// 子 -> 父 技术 (传要切换的组件名出来)
import MyHeader from "./components/MyHeader.vue";
import MyGoodsList from "./view/MyGoodsList.vue";
import MyGoodsSearch from "./view/MyGoodsSearch.vue";
import MyUserInfo from "./view/MyUserInfo.vue";
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
      comName: "MyGoodsList", //默认显示的组件
    };
  },
  components: {
    MyHeader,
    MyTabBar,
    MyGoodsList,
    MyGoodsSearch,
    MyUserInfo,
  },
  methods: {
    changeComFn(cName) {
      this.comName = cName;
      // MyTabBar里选出来的组件名赋予给
      // is属性的comName
      // b2父 (子传父)导致组件的切换
    },
  },
};
</script>

<style scoped>
.main {
  padding-top: 45px;
  padding-bottom: 51px;
}
</style>