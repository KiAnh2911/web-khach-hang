<script setup lang="ts">
import { toRefs } from "vue";
import { ICard } from "../ThanksContactingUs/index.vue";

interface Props {
  card: ICard;
}

const props = defineProps<Props>();
const { card } = toRefs(props);
</script>

<template>
  <div
    class="t-relative t-flex-[0_0_20rem] t-h-[414px] t-shadow-lg last:t-mr-4"
  >
    <div class="t-w-full t-h-full t-overflow-hidden t-rounded-lg">
      <img
        :src="card.url"
        :alt="card.url"
        class="t-object-cover t-w-full t-h-full"
      />
    </div>
    <div
      class="t-absolute t-inset-0 t-p-5 t-bg-gradient-to-t t-from-[rgba(0,0,0,0.4)] t-to-[rgba(0,0,0,0)] t-rounded-lg"
    >
      <h2 class="t-text-[28px] t-font-semibold t-leading-9 t-text-white t-m-0">
        {{ card.title }}
      </h2>
      <p class="t-text-base t-font-medium t-leading-6 t-text-white t-m-0">
        {{ card.desc }}
      </p>
    </div>
  </div>
</template>
