<script setup lang="ts">
import { toRefs } from "vue";

const props = defineProps(["card"]);
const { card } = toRefs(props);
</script>

<template>
  <div class="card-thankyou">
    <div class="card-thankyou__image">
      <img :src="card.url" :alt="card.url" />
    </div>
    <div class="card-thankyou__content">
      <h2 class="card-thankyou__content-title">{{ card.title }}</h2>
      <p class="card-thankyou__content-desc">
        {{ card.desc }}
      </p>
    </div>
  </div>
</template>

<style lang="scss">
@import "./index.scss";
</style>
