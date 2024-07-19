<script setup lang="ts">
import { Button, Modal } from "ant-design-vue";
import { ref } from "vue";
import { CloseIcon, NextIcon, PrevIcon } from "../../assets";
import CardThankYouContacting from "../CardThankYouContacting/index.vue";

defineExpose({ show });

const showModal = ref(false);

const listCard = [
  {
    id: 1,
    url: "https://s3-alpha-sig.figma.com/img/d82c/8d39/622de0951fabc7c325262107e7a192ac?Expires=1722211200&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=ZgXxrXEgJP67M~RwRNpVEiyNrXJxHNULZE8O3rozq26N0qwg6UAPJpbrngefQtemPpC8j99xXbIpCTZ1dS7DPiBsTmMN9wJXge1Q4NKOOCUFkW9qTZ0JdJno5ReeQ0Zyv3gn6A60nihMStQyHGxvZKcksELTyffeE~-sqSdY6GnuT1kxGAsGpLOBDuPHcXmvDnY8qOr319jn2B3TVRTtJmTJMy3X~jyu4ZJhwWiT5sUui5W6vWlPR6pxNJ~WX1dZKIVsNwycMvgPY888sme8SH4MOGLy55nJu8miWtQ9iKNNzlScWhSG4Mt7OOwj2pi0Bf9U9iGKFAGwQTAj1eDP2g__",
    title: "May đo giải pháp",
    desc: "Thiết lập mô hình theo doanh nghiệp",
  },
  {
    id: 2,
    url: "https://s3-alpha-sig.figma.com/img/f869/ebac/29728ea499673907c741ca03381d1d52?Expires=1722211200&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=LjyR-MKm~TyWnEIeBj92qAesf74pgeiPH-orCXb0ddFz9rTAKoR1jQhKqoXpYix-zqCB-rQ2N1TmA7hGKprFSQhDIDZ8NeDbo7r7AXVgP43rvkUBBOLimbCF9rIqvZfp3o~EXmKYUv5DkyyDJIyit9l~r-PAG4giK~T6VKnA-3-fb9CUAxPJHJUzPOJgJptmFzWEN~~Y4lCT2qNcbqhm0CvkE2muabJQvpmD8EZOPxhu-IAqBqoezLh2ALBVBRP4VSwf4J7J74mbfdbE9Pa25JXh2AFKTHt5sgiifZnoerT0~PGwftDvF4iG8OzXjoZjZSjDtzrTxNQVg~762Ovhlw__",
    title: "Giao hàng EXPRESS",
    desc: "Giao hàng tận nơi 63 tỉnh thành",
  },
  {
    id: 3,
    url: "https://s3-alpha-sig.figma.com/img/bd5c/e1be/3c0fff2c24160af9afd87872d658db27?Expires=1722211200&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=JA7CO2ZKNPI2yt6gRYotf~avTl~BPgKivA3jTBsIwYQKbs64iVgJd908tCi07zIAsJbh3~6oR8NwAxUOQue~xdnH814a96G6uizLoefIQEhDNPJmN4FdjEu25qRubpsGRL5Or2rUXYNDrgIud4eSfEuRdUPYNY54sZfmEau5P8CtdsZBLzJGGRfrOqEKrI8~wUqmPALzYlzYF2hTD664JCMV25CpmdEdSa-EDej5fv2JNnx3UE-yzItdDpV7ffxlgwgxGbYoG7ZVku1Swbfxtx4v~nUZyqdbnD2g7JnItBZWvcGORN2Y2xGbqj9eVjQojKLJWzq1f-sXXWSujcGQMg__",
    title: "Giao hàng BBS",
    desc: "Giao hàng lên tới 500kg",
  },
  {
    id: 4,
    url: "https://s3-alpha-sig.figma.com/img/d82c/8d39/622de0951fabc7c325262107e7a192ac?Expires=1722211200&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=ZgXxrXEgJP67M~RwRNpVEiyNrXJxHNULZE8O3rozq26N0qwg6UAPJpbrngefQtemPpC8j99xXbIpCTZ1dS7DPiBsTmMN9wJXge1Q4NKOOCUFkW9qTZ0JdJno5ReeQ0Zyv3gn6A60nihMStQyHGxvZKcksELTyffeE~-sqSdY6GnuT1kxGAsGpLOBDuPHcXmvDnY8qOr319jn2B3TVRTtJmTJMy3X~jyu4ZJhwWiT5sUui5W6vWlPR6pxNJ~WX1dZKIVsNwycMvgPY888sme8SH4MOGLy55nJu8miWtQ9iKNNzlScWhSG4Mt7OOwj2pi0Bf9U9iGKFAGwQTAj1eDP2g__",
    title: "May đo giải pháp",
    desc: "Thiết lập mô hình theo doanh nghiệp",
  },
  {
    id: 5,
    url: "https://s3-alpha-sig.figma.com/img/f869/ebac/29728ea499673907c741ca03381d1d52?Expires=1722211200&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=LjyR-MKm~TyWnEIeBj92qAesf74pgeiPH-orCXb0ddFz9rTAKoR1jQhKqoXpYix-zqCB-rQ2N1TmA7hGKprFSQhDIDZ8NeDbo7r7AXVgP43rvkUBBOLimbCF9rIqvZfp3o~EXmKYUv5DkyyDJIyit9l~r-PAG4giK~T6VKnA-3-fb9CUAxPJHJUzPOJgJptmFzWEN~~Y4lCT2qNcbqhm0CvkE2muabJQvpmD8EZOPxhu-IAqBqoezLh2ALBVBRP4VSwf4J7J74mbfdbE9Pa25JXh2AFKTHt5sgiifZnoerT0~PGwftDvF4iG8OzXjoZjZSjDtzrTxNQVg~762Ovhlw__",
    title: "Giao hàng EXPRESS",
    desc: "Giao hàng tận nơi 63 tỉnh thành",
  },
  {
    id: 6,
    url: "https://s3-alpha-sig.figma.com/img/bd5c/e1be/3c0fff2c24160af9afd87872d658db27?Expires=1722211200&Key-Pair-Id=APKAQ4GOSFWCVNEHN3O4&Signature=JA7CO2ZKNPI2yt6gRYotf~avTl~BPgKivA3jTBsIwYQKbs64iVgJd908tCi07zIAsJbh3~6oR8NwAxUOQue~xdnH814a96G6uizLoefIQEhDNPJmN4FdjEu25qRubpsGRL5Or2rUXYNDrgIud4eSfEuRdUPYNY54sZfmEau5P8CtdsZBLzJGGRfrOqEKrI8~wUqmPALzYlzYF2hTD664JCMV25CpmdEdSa-EDej5fv2JNnx3UE-yzItdDpV7ffxlgwgxGbYoG7ZVku1Swbfxtx4v~nUZyqdbnD2g7JnItBZWvcGORN2Y2xGbqj9eVjQojKLJWzq1f-sXXWSujcGQMg__",
    title: "Giao hàng BBS",
    desc: "Giao hàng lên tới 500kg",
  },
];

function show() {
  showModal.value = !showModal.value;
}

function scrollCards(direction: string) {
  const scrollContainer = document.querySelector(".card-list");
  const cardWidth = 320;
  const gap = 16;

  if (scrollContainer) {
    const scrollAmount = cardWidth + gap;
    if (direction === "next") {
      return scrollContainer.scrollBy({
        left: scrollAmount,
        behavior: "smooth",
      });
    }
    return scrollContainer.scrollBy({
      left: -scrollAmount,
      behavior: "smooth",
    });
  }
}

function handleScroll(event: WheelEvent) {
  if (event.deltaY > 0) {
    scrollCards("next");
  } else {
    scrollCards("prev");
  }
}
</script>

<template>
  <Modal
    v-model:open="showModal"
    footer
    class="modal-thankyou"
    :closable="false"
  >
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

    <div class="modal-content t-p-4 t-pr-0">
      <div class="t-mb-6">
        <p class="t-text-base t-font-normal t-leading-6 t-m-0 t-mb-3">
          Giao Hàng Tiết Kiệm (GHTK) sẽ nhanh chóng liên hệ với bạn. Vui lòng
          kiểm tra hộp thư email để nhận thông tin chi tiết về tài khoản doanh
          nghiệp và các bước tiếp theo.
        </p>

        <p class="t-text-base t-font-normal t-leading-6 t-m-0">
          Trong thời gian chờ đợi, bạn có thể tham khảo thêm các thông tin hữu
          ích dưới đây:
        </p>
      </div>

      <div class="t-flex t-items-center t-pl-4 modal-content__list">
        <button
          @click="scrollCards('prev')"
          class="scroll-button t-absolute t-bg-white t-w-10 t-h-10 t-rounded-full t-border-0 t-cursor-pointer t-p-0 t-hidden t-top-1/2 t-left-3 t-translate-y-1/2 t-z-10"
        >
          <PrevIcon />
        </button>

        <div
          class="card-list t-relative t-flex t-gap-4 t-overflow-hidden t-snap-x t-snap-mandatory t-scroll-smooth"
          @mousewheel.passive="handleScroll"
        >
          <CardThankYouContacting
            v-for="card in listCard"
            :key="card.id"
            :card="card"
          />
        </div>

        <button
          @click="scrollCards('next')"
          class="scroll-button t-absolute t-bg-white t-w-10 t-h-10 t-rounded-full t-border-0 t-cursor-pointer t-p-0 t-hidden t-top-1/2 t-right-3 t-translate-y-1/2 t-z-10 t-mt-1.5-"
        >
          <NextIcon />
        </button>
      </div>
    </div>

    <div class="t-p-4 t-flex t-justify-end t-mb-0">
      <Button
        class="t-bg-ghtk t-text-white t-h-10 t-rounded t-text-base t-font-medium t-leading-6 t-px-3 t-py-2"
        @click="show"
        >OK. Tôi đã hiểu!</Button
      >
    </div>
  </Modal>
</template>

<style lang="scss">
@import "./index.scss";
</style>
