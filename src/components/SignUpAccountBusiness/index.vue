<script lang="ts" setup>
import { Button, Form, FormItem, Input, Modal } from "ant-design-vue";
import { reactive, ref } from "vue";
import { CloseIcon } from "../../assets";

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
    <div class="t-flex t-justify-between t-items-center t-p-4 line-border-b">
      <h2 class="t-text-lg t-font-medium t-leading-6 t-text-black t-m-0">
        Cảm ơn bạn đã liên hệ với chúng tôi
      </h2>

      <div
        class="t-flex t-items-center t-rounded-full t-justify-center t-w-[22px] t-h-[22px] t-bg-inactive t-cursor-pointer"
        @click="show"
      >
        <CloseIcon />
      </div>
    </div>

    <Form
      :model="formSignUpBusiness"
      name="basic"
      autocomplete="off"
      ref="formRef"
      @finish="onFinish"
    >
      <div class="modal-content t-p-4">
        <p class="t-m-0 t-text-base t-leading-6 t-mb-6">
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

      <FormItem class="t-p-4 t-flex t-justify-end t-mb-0">
        <Button
          class="t-bg-ghtk t-text-white t-h-10 t-rounded t-text-base t-font-medium t-leading-6 t-px-3 t-py-2"
          html-type="submit"
          >Hoàn thành</Button
        >
      </FormItem>
    </Form>
  </Modal>
</template>

<style lang="scss" src="./styles.scss"></style>
