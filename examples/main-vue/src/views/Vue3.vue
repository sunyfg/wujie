<template>
  <!--保活模式，name相同则复用一个子应用实例，改变url无效，必须采用通信的方式告知路由变化 -->
  <WujieVue width="100%" height="100%" name="vue3" :url="vue3Url" :sync="true"></WujieVue>
</template>

<script>
import hostMap from "../hostMap";
import wujieVue from "wujie-vue2";
export default {
  data() {
    return {
      vue3Url: hostMap("//localhost:7300/"),
    };
  },
  mounted() {
    // 告诉子应用要跳转哪个路由
    this.$route.params.path && wujieVue.bus.$emit("vue3-router-change", `/${this.$route.params.path}`);
  },
};
</script>

<style lang="scss" scoped></style>
