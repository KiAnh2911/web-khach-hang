<script setup lang="ts">
import { ref } from "vue";
import { Button } from "ant-design-vue";
import SignUpAccountBusiness from "./components/SignUpAccountBusiness/index.vue";
import ThanksContactingUs from "./components/ThanksContactingUs/index.vue";

const modalSignUpAccountRef = ref();
const modalThankYouRef = ref();

function handleModalSignUpAccount() {
  modalSignUpAccountRef.value.show();
}
function handleModalThankYou() {
  modalThankYouRef.value.show();
}
</script>

<template>
  <Button @click="handleModalSignUpAccount">Sign Up</Button>
  <Button @click="handleModalThankYou">Thanks you contacting us</Button>

  <SignUpAccountBusiness ref="modalSignUpAccountRef" />
  <ThanksContactingUs ref="modalThankYouRef" />
</template>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
