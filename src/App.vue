<script setup>
import { reactive, ref } from "vue";
import Form from "./components/Form.vue";
import Page from "./components/Page.vue";

const form = reactive({
  name: "",
  avatar:
    "https://fuss10.elemecdn.com/3/63/4e7f3a15429bfda99bce42a18cdd1jpeg.jpeg?imageMogr2/thumbnail/360x360/format/webp/quality/100",
  job: "",
  sex: "",
  workdata: "",
  birthday: "",
  email: "",
  phone: "",
  wechat: "",
  city: "",
  salary: "",
});
</script>

<template>
  <div>
    <el-row :gutter="20">
      <el-col :span="12">
        <Form :form="form" />
      </el-col>
      <el-col :span="12">
        <Page :form="form" />
      </el-col>
    </el-row>
  </div>
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
