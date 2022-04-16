<script setup>
import relativeTime from "dayjs/plugin/relativeTime";
import dayjs from "dayjs";
import { Cellphone } from "@element-plus/icons-vue";
import { Message } from "@element-plus/icons-vue";

dayjs.extend(relativeTime);

const props = defineProps({
  form: Object,
});
</script>

<template>
  <div>
    <h2>{{ form.name || "-" }}</h2>
    <el-row :gutter="2">
      <el-col :span="2"
        ><div class="grid-content bg-purple" />
        <p>{{ form.sex }} |</p>
      </el-col>
      <el-col :span="6"
        ><div class="grid-content bg-purple" />
        <p>
          生日：{{
            form.birthday ? dayjs(form.birthday).format("YYYY/MM") : " "
          }}
        </p>
      </el-col>
      <el-col :span="8"
        ><div class="grid-content bg-purple" />
        <p class="box">
          <Cellphone style="width: 1em; height: 1em; margin-right: 8px" />
          <span>{{ form.phone }}</span>
        </p>
      </el-col>
      <el-col :span="8"
        ><div class="grid-content bg-purple" />
        <p class="box">
          <Message style="width: 1em; height: 1em; margin-right: 8px" />
          <span>{{ form.email }}</span>
        </p>
      </el-col>
    </el-row>
    <el-row :gutter="1">
      <el-col :span="6"
        ><div class="grid-content bg-purple" />
        <p>
          {{
            form.workdata
              ? dayjs(form.workdata).to(dayjs(Date.now()), true)
              : "无"
          }}工作经验 |
        </p>
      </el-col>
      <el-col :span="8"
        ><div class="grid-content bg-purple" />
        <p>求职意向：{{ form.job }} |</p>
      </el-col>
      <el-col :span="8"
        ><div class="grid-content bg-purple" />
        <p>期望薪资：{{ form.salary }}</p>
      </el-col>
    </el-row>
  </div>
  <div>
    <h3>个人优势</h3>
    <el-row>
      <el-col :span="24"
        ><div class="grid-content bg-purple" />
        <p>
          1.
          7年产品经验，5年教育行业经验，擅长在线教育、低代码工具、创作社区等业务
        </p></el-col
      >
    </el-row>
    <el-row>
      <el-col :span="24"
        ><div class="grid-content bg-purple" />
        <p>
          2. 擅长团队管理，担当过多个产品的Owner，负责过产品的全生命周期管理
        </p></el-col
      >
    </el-row>
    <el-row>
      <el-col :span="24"
        ><div class="grid-content bg-purple" />
        <p>
          3.
          有技术背景，业余时间曾独立开发过两款工具小软件(Swift)，对新技术充满热情
        </p></el-col
      >
    </el-row>
  </div>
  <div>
    <h3>工作经历</h3>
    <el-row :gutter="20">
      <el-col :span="16"
        ><div class="grid-content bg-purple" />
        <div>
          <div>无</div>
        </div>
      </el-col>
      <el-col :span="8"><div class="grid-content bg-purple" /></el-col>
    </el-row>
  </div>
</template>

<style>
.box {
  display: flex;
  align-items: center;
}
</style>
