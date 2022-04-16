<script setup>
import { reactive, ref } from "vue";
import { Plus } from "@element-plus/icons-vue";
import { ArrowDown } from "@element-plus/icons-vue";
import { ElMessageBox } from "element-plus";

const props = defineProps({
  form: Object,
});

//Dialog期望职位
const dialogVisible = ref(false);
const handleClose = (done) => {
  ElMessageBox.confirm("Are you sure to close this dialog?")
    .then(() => {
      done();
    })
    .catch(() => {
      // catch error
    });
};

// Avatar头像
const url = ref("https://jsonplaceholder.typicode.com/posts/");

// Form-Select性别
const sexOptions = [
  {
    value: "男",
    label: "男",
  },
  {
    value: "女",
    label: "女",
  },
];

const onSubmit = () => {
  console.log("submit!");
};

const handleAvatarSuccess = (response, uploadFile) => {
  form.avatar.value = URL.createObjectURL(uploadFile.raw);
};

const beforeAvatarUpload = (rawFile) => {
  if (rawFile.type !== "image/jpeg") {
    ElMessage.error("Avatar picture must be JPG format!");
    return false;
  } else if (rawFile.size / 1024 / 1024 > 2) {
    ElMessage.error("Avatar picture size can not exceed 2MB!");
    return false;
  }
  return true;
};

// 城市
const CITYprops = {
  expandTrigger: "hover",
};
const handleChange = (value) => {
  console.log(value);
};
const cityOptions = [
  {
    value: "guide",
    label: "北京",
    children: [
      {
        value: "disciplines",
        label: "东城区",
      },
      {
        value: "navigation",
        label: "西城区",
      },
    ],
  },
  {
    value: "guide2",
    label: "广东",
    children: [
      {
        value: "disciplines",
        label: "广州",
      },
      {
        value: "navigation",
        label: "深圳",
      },
    ],
  },
];
</script>

<template>
  <div>
    <h3>个人信息</h3>
    <el-form :model="form" label-width="120px" label-position="top">
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="姓名">
            <el-input v-model="form.name" />
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item>
            <el-upload
              class="avatar-uploader"
              :action="url"
              :show-file-list="false"
              :on-success="handleAvatarSuccess"
              :before-upload="beforeAvatarUpload"
            >
              <img v-if="form.avatar" :src="form.avatar" class="avatar" />
              <el-icon v-else class="avatar-uploader-icon"><Plus /></el-icon>
            </el-upload>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="期望职位">
            <el-input v-model="form.job" @click="dialogVisible = true" />
            <el-dialog
              v-model="dialogVisible"
              title="Tips"
              width="30%"
              :before-close="handleClose"
            >
              <span>选择岗位</span>
              <template #footer>
                <span class="dialog-footer">
                  <el-button @click="dialogVisible = false">Cancel</el-button>
                  <el-button type="primary" @click="dialogVisible = false"
                    >Confirm</el-button
                  >
                </span>
              </template>
            </el-dialog>
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="性别">
            <el-select v-model="form.sex" clearable placeholder=" ">
              <el-option
                v-for="item in sexOptions"
                :key="item.value"
                :label="item.label"
                :value="item.value"
              />
            </el-select>
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="参加工作日期">
            <el-date-picker
              v-model="form.workdata"
              type="month"
              placeholder=""
            />
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="生日">
            <el-date-picker
              v-model="form.birthday"
              type="month"
              placeholder=""
            />
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="邮箱">
            <el-input v-model="form.email" />
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="电话">
            <el-input v-model="form.phone" />
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="微信号">
            <el-input v-model="form.wechat" />
          </el-form-item>
        </el-col>
        <el-col :span="12">
          <el-form-item label="期望城市">
            <el-cascader
              v-model="form.city"
              :options="cityOptions"
              :props="CITYprops"
              @change="handleChange"
            />
          </el-form-item>
        </el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="12">
          <el-form-item label="薪资要求">
            <el-input v-model="form.salary" />
          </el-form-item>
        </el-col>
      </el-row>
    </el-form>
  </div>
</template>

<style>
.avatar {
  width: 80px;
  height: 80px;
}
.avatar-uploader .el-upload {
  border: 1px dashed #d9d9d9;
  border-radius: 6px;
  cursor: pointer;
  position: relative;
  overflow: hidden;
  transition: var(--el-transition-duration-fast);
}

.avatar-uploader .el-upload:hover {
  border-color: var(--el-color-primary);
}

.el-icon.avatar-uploader-icon {
  font-size: 28px;
  color: #8c939d;
  width: 80px;
  height: 80px;
  text-align: center;
}

.example-showcase .el-dropdown-link {
  cursor: pointer;
  color: var(--el-color-primary);
  display: flex;
  align-items: center;
}

.dialog-footer button:first-child {
  margin-right: 10px;
}
</style>
