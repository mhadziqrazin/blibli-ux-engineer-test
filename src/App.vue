<script setup lang="ts">
import Card from "./components/Card.vue"
import { onMounted, onUpdated, ref } from "vue"

const items = ref<HTMLElement | null>(null);
const leftVis = ref(false);
const rightVis = ref(false);
const showFooter = ref(false);
const topVis = ref(false);
const main = ref<HTMLElement | null>(null);

function scrollRight() {
  const items = document.querySelector(".items");
  if (!!items) items.scrollLeft += 30;
  updateButtonVis();
}

function scrollLeft() {
  const items = document.querySelector(".items");
  if (!!items) items.scrollLeft -= 30;
  updateButtonVis();
}

function scrollTop() {
  window.scrollTo({
    top: 0,
    behavior: "smooth"
  });
}

function updateTopVis() {
  const tres = 20;
  topVis.value = window.scrollY > tres;
}

function updateButtonVis() {
  if (items.value) {
    leftVis.value = items.value.scrollLeft > 0;
    rightVis.value = items.value.scrollLeft < items.value.scrollWidth - items.value.clientWidth;
  }
}

function handleScroll() {
  updateButtonVis();
}

function handleScrollTop() {
  updateTopVis();
}

onMounted(() => {
  updateButtonVis();
  updateTopVis();
  window.addEventListener('scroll', handleScrollTop, { passive: true });
  window.addEventListener('touchmove', handleScrollTop, { passive: true });
  items.value?.addEventListener('scroll', handleScroll, { passive: true });
  items.value?.addEventListener('touchmove', handleScroll, { passive: true });
});

onUpdated(() => {
  updateButtonVis();
  updateTopVis();
});
</script>

<template>
  <nav>
    <div class="container">
      <img load="lazy" src="/assets/logo.png" class="logo" alt="logo" />
    </div>
  </nav>

  <main ref="main">
    <section class="one-n-two">
      <div class="one box">
        1
      </div>
      <div class="two box">
        2
      </div>
    </section>
    <section class="three box">
      3
    </section>
    <section class="four box">
      4
    </section>
    <section class="container-items">
      <div class="items" ref="items">
        <button v-show="leftVis" @click="scrollLeft" class="left scroll-btn util-btn">
          &lsaquo;
        </button>
        <button v-show="rightVis" @click="scrollRight" class="right scroll-btn util-btn">
          &rsaquo;
        </button>
        <Card
          v-for="i in 10" :key="i"
          title="NIKE AJ1 Retro High White University Blue Black"
          img= "/assets/nike.png"
          :price=3550000
        />
      </div>
    </section>
  </main>
  <button @click="scrollTop" v-show="topVis" class="scroll-top-btn util-btn">
    &uarr;
  </button>
  <footer>
    <p v-if="showFooter" class="container footer">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis sollicitudin mattis nibh ut tincidunt. Pellentesque eget gravida orci, eu rhoncus mauris. Interdum et malesuada fames ac ante ipsum primis in faucibus. Sed eget risus urna. Aenean non lectus risus. Aenean ac sagittis libero, vel volutpat tellus. Mauris sit amet hendrerit velit. Vivamus nec consectetur dolor. Mauris porttitor lacinia velit, sit amet volutpat lacus euismod non. Vivamus laoreet malesuada purus, nec porta elit tincidunt sit amet. Praesent orci quam, laoreet in mi non, venenatis congue dui. Suspendisse non lacus eget massa pretium tincidunt id quis justo. Integer velit tortor, ultricies ac.
    </p>
    <button @click="showFooter = !showFooter" v-if="showFooter" class="collapse">
      Collapse all <span>&#8963;</span>
    </button>
    <button @click="showFooter = !showFooter" v-else class="collapse">
      Show all <span>&or;</span>
    </button>
    <p class="copyright">
      c 2022 PT Global Digital Niaga
    </p>
  </footer>
</template>

<style scoped>
nav {
  padding: 8px 16px;
  background: #0095da;
}

main {
  display: flex;
  flex-direction: column;
  gap: 16px;
  padding: 16px;
}

.logo {
  max-width: 75px;
}

.one-n-two {
  display: flex;
  gap: 10px;
}

.container-items {
  position: relative;
}

.items {
  display: flex;
  padding: 12px 12px;
  gap: 12px;
  overflow-x: scroll;
  -ms-overflow-style: none;
  scrollbar-width: none;
}

.items::-webkit-scrollbar {
  display: none;
}

.box {
  width: 100%;
  height: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  font-size: 52px;
  font-weight: 700;
}

.one {
  flex: 1 1 0;
  background: #dbfb15;
}

.two {
  flex: 1 1 0;
  background: #2af3fe;
}

.three {
  background: #f474ff;
}

.four {
  background: #ff8a8a;
}

@media (max-width: 640px) {
  .four {
    order: -1;
  }
  .three {
    order: 0;
  }

  .items {
    order: 2;
  }

  .one-n-two {
    order: 3;
  }

  .box {
    height: 250px;
  }
}

button {
  cursor: pointer;
}

.util-btn {
  width: 40px;
  height: 40px;
  border: 0;
  border-radius: 999px;
  color: #0095da;
  background: #fff;
  font-size: 20px;
  font-weight: 700;
  padding: 8px;
  box-shadow: 1px 1px 5px 2px rgb(0 0 0 / 0.2);
}

.scroll-btn {
  position: absolute;
  top: 50%;
}

.left {
  left: 20px;
}

.right {
  right: 20px;
}

.scroll-top-btn {
  position: fixed;
  right: 50px;
  bottom: 50px;
}

footer {
  padding: 40px 16px;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  text-align: justify;
  background: #d9d9d9;
}

.copyright {
  margin-top: 80px;
}

.collapse {
  background: transparent;
  border: 0;
  color: #0095da;
  font-weight: 600;
}
</style>
