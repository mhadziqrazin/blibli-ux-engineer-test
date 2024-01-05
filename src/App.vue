<script setup lang="ts">
import Card from "./components/Card.vue"
</script>

<template>
  <nav>
    <div class="container">
      <img load="lazy" src="../public/assets/logo.png" class="logo" alt="logo" />
    </div>
  </nav>

  <main>
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
    <section class="items">
      <button>
        aaa
      </button>
      <Card
        v-for="i in 20" :key="i"
        title="NIKE AJ1 Retro High White University Blue Black"
        img= "public/assets/nike.png"
        price=3550000
      />
    </section>
  </main>
  <footer>
    <p class="container">
      Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis sollicitudin mattis nibh ut tincidunt. Pellentesque eget gravida orci, eu rhoncus mauris. Interdum et malesuada fames ac ante ipsum primis in faucibus. Sed eget risus urna. Aenean non lectus risus. Aenean ac sagittis libero, vel volutpat tellus. Mauris sit amet hendrerit velit. Vivamus nec consectetur dolor. Mauris porttitor lacinia velit, sit amet volutpat lacus euismod non. Vivamus laoreet malesuada purus, nec porta elit tincidunt sit amet. Praesent orci quam, laoreet in mi non, venenatis congue dui. Suspendisse non lacus eget massa pretium tincidunt id quis justo. Integer velit tortor, ultricies ac.
    </p>
    <button>
      Collapse all <span>&#8963;</span>
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

.items {
  display: flex;
  padding: 12px 12px;
  gap: 12px;
  overflow-x: hidden;
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
  .three {
    order: 1;
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
</style>
