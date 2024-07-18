<script lang="ts" setup>
import { reactive, ref } from "vue";
import { Modal, Input, Button, Form, FormItem } from "ant-design-vue";

defineExpose({ show });

interface ISignUpBusiness {
  fullName: String;
  phoneNumber: String;
  email: String;
  nameCompany: String;
  codeTax: String;
}

const formRef = ref();
const showModal = ref(false);
const formSignUpBusiness = reactive<ISignUpBusiness>({
  fullName: "",
  phoneNumber: "",
  email: "",
  nameCompany: "",
  codeTax: "",
});

function show() {
  showModal.value = !showModal.value;
}
function onFinish(data: ISignUpBusiness) {
  showModal.value = !showModal.value;
  console.log("data", data);
  formRef.value.resetFields();
}
</script>

<template>
  <Modal v-model:open="showModal" footer :closable="false" class="modal-signup">
    <div class="modal-header">
      <h2 class="title-modal">Đăng ký tài khoản doanh nghiệp</h2>
      <div class="icon-close" @click="show">
        <svg
          width="10"
          height="10"
          viewBox="0 0 10 10"
          fill="none"
          xmlns="http://www.w3.org/2000/svg"
        >
          <rect
            width="1.1659"
            height="12.8707"
            rx="0.582949"
            transform="matrix(0.701754 0.712419 -0.701754 0.712419 9.18188 0)"
            fill="#EA4025"
          />
          <rect
            width="1.1659"
            height="12.8707"
            rx="0.582949"
            transform="matrix(0.701754 -0.712419 0.701754 0.712419 0 0.830627)"
            fill="#EA4025"
          />
        </svg>
      </div>
    </div>
    <Form
      :model="formSignUpBusiness"
      name="basic"
      autocomplete="off"
      ref="formRef"
      @finish="onFinish"
    >
      <div class="modal-content">
        <p class="modal-content__desc">
          Để được tư vấn và hỗ trợ tạo tài khoản đối tác, vui lòng nhập thông
          tin doanh nghiệp của bạn
        </p>

        <FormItem
          name="fullName"
          :rules="[{ required: true, message: 'Please input your full name!' }]"
        >
          <Input
            placeholder="Họ và tên người liên hệ"
            v-model:value="formSignUpBusiness.fullName"
          />
        </FormItem>

        <FormItem
          name="phoneNumber"
          :rules="[
            { required: true, message: 'Please input your phone number!' },
          ]"
        >
          <Input
            placeholder="Số điện thoại"
            v-model:value="formSignUpBusiness.phoneNumber"
          />
        </FormItem>

        <FormItem
          name="email"
          :rules="[{ required: true, message: 'Please input your email!' }]"
        >
          <Input placeholder="Email" v-model:value="formSignUpBusiness.email" />
        </FormItem>

        <FormItem
          name="nameCompany"
          :rules="[
            { required: true, message: 'Please input your name company!' },
          ]"
        >
          <Input
            placeholder="Tên công ty"
            v-model:value="formSignUpBusiness.nameCompany"
          />
        </FormItem>

        <FormItem
          name="codeTax"
          :rules="[
            { required: true, message: 'Please input your name code Tax!' },
          ]"
        >
          <Input
            type="text"
            placeholder="Mã số thuế"
            v-model:value="formSignUpBusiness.codeTax"
          />
        </FormItem>
      </div>

      <FormItem class="modal-footer">
        <Button class="btn-complete" html-type="submit">Hoàn thành</Button>
      </FormItem>
    </Form>
  </Modal>
</template>

<style lang="scss">
@import "./index.scss";
</style>
