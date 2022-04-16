<script>
import App from "./App.vue";
import { defineComponent } from "vue";
import { ElConfigProvider } from "element-plus";
import zhCn from "element-plus/lib/locale/lang/zh-cn";
import dayjs from "dayjs";
import "dayjs/locale/zh-cn";

dayjs.locale("zh-cn"); // 全局使用

// 全局国际化配置，使用zhCn
export default defineComponent({
  components: {
    App,
    ElConfigProvider,
  },
  setup() {
    return {
      locale: zhCn,
    };
  },
});
</script>

<template>
  <el-config-provider :locale="locale">
    <App />
  </el-config-provider>
</template>

<style>
.bg {
  background-color: aqua;
  width: 100%;
}
.title {
  color: green;
}
</style>
