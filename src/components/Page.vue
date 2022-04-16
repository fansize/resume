<script setup>
import { reactive, ref } from "vue";
import Preview from "./Preview.vue";
import { Upload } from "@element-plus/icons-vue";
const props = defineProps({
  form: Object,
});
</script>

<template>
  <div>
    <el-button type="primary">
      导出PDF<el-icon class="el-icon--right"><Upload /></el-icon>
    </el-button>
    <Preview :form="form" />
  </div>
</template>
