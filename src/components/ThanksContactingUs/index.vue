<script setup lang="ts">
import { nextTick, onMounted, ref, watch } from "vue";
import { Button, Modal } from "ant-design-vue";
import CardThankYouContacting from "../CardThankYouContacting/index.vue";
import NextIcon from "../../assets/next.svg";
import PrevIcon from "../../assets/prev.svg";
import { onBeforeUnmount } from "vue";

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
  const scrollContainer = document.querySelector(".modal-content__list-card");
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

watch(showModal, (newVal) => {
  nextTick(() => {
    const scrollContainer = document.querySelector(
      ".modal-content__list-card"
    ) as HTMLElement;
    if (newVal) {
      if (scrollContainer) {
        scrollContainer.addEventListener("wheel", handleScroll, {
          passive: true,
        });
      }
    } else {
      if (scrollContainer) {
        scrollContainer.removeEventListener("wheel", handleScroll);
      }
    }
  });
});
</script>

<template>
  <Modal
    v-model:open="showModal"
    footer
    class="modal-thankyou"
    :closable="false"
  >
    <div class="modal-header">
      <h2 class="title-modal">Cảm ơn bạn đã liên hệ với chúng tôi</h2>
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
    <div class="modal-content">
      <div class="modal-content__desc">
        <p class="modal-content__desc__thank">
          Giao Hàng Tiết Kiệm (GHTK) sẽ nhanh chóng liên hệ với bạn. Vui lòng
          kiểm tra hộp thư email để nhận thông tin chi tiết về tài khoản doanh
          nghiệp và các bước tiếp theo.
        </p>
        <p class="modal-content__desc__thank">
          Trong thời gian chờ đợi, bạn có thể tham khảo thêm các thông tin hữu
          ích dưới đây:
        </p>
      </div>
      <div class="modal-content__list">
        <button @click="scrollCards('prev')" class="scroll-button prev-button">
          <PrevIcon />
        </button>
        <div class="modal-content__list-card">
          <CardThankYouContacting
            v-for="card in listCard"
            :key="card.id"
            :card="card"
          />
        </div>
        <button @click="scrollCards('next')" class="scroll-button next-button">
          <NextIcon />
        </button>
      </div>
    </div>
    <div class="modal-footer">
      <Button class="btn-complete" @click="show">OK. Tôi đã hiểu!</Button>
    </div>
  </Modal>
</template>

<style lang="scss">
@import "./index.scss";
</style>
