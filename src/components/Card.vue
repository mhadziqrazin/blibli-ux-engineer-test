<script setup lang="ts">
defineProps<{
  title: string
  price: number
  img: string
}>()
</script>

<template>
  <div class="card">
    <img load="lazy" :src="img" />
    <div class="info">
      <h1 class="title">
        {{ title }}
      </h1>
      <div class="price-container">
        <p class="price">
          {{ Intl.NumberFormat('id-ID', { style: 'currency', currency: 'IDR' }).format(price) }}
        </p>
        <div class="discount-container">
          <p class="discount-price">
            Rp1.000.000
          </p>
          <div class="discount-percent-container">
            <p class="discount-percent">
            99%
            </p>
          </div>
        </div>
      </div>
      <button>
        Add to bag
      </button>
    </div>
  </div>
</template>

<style scoped>
.card {
  width: 182px;
  border-radius: 20px;
  overflow: hidden;
  box-shadow: 0 0 8px 0.5px rgb(0 0 0 / 0.2);
  display: grid;
  grid-template-rows: 1fr 1fr;
}

@media (max-width: 640px) {
  .card {
    width: 132px;
  }
}

img {
  max-width: 100%;
  min-height: 100%;
  object-fit: cover;
}

h1, p {
  margin: 0;
}

.title {
  font-size: 12px;
  font-weight: 500;
  overflow: hidden;
  display: -webkit-box;
  -webkit-box-orient: vertical;
  -webkit-line-clamp: 2;
}

.info {
  padding: 8px;
  display: flex;
  flex-direction: column;
  gap: 4px;
}

.price-container {
  display: flex;
  flex-direction: column;
}

.price {
  font-size: 12px;
  font-weight: 600;
  color: #f3792e;
}

.discount-container {
  display: flex;
  gap: 8px;
  align-items: center;
}

.discount-price {
  font-size: 11px;
  color: rgb(0 0 0 / 0.5);
  font-weight: 500;
  text-decoration-line: line-through;
}

.discount-percent-container {
  background: #f9b9bc;
  border-radius: 999px;
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 0 6px;
}

.discount-percent {
  color: #f04147;
  font-weight: 700;
  font-size: 11px;
}

button {
  background: #0095da;
  border: 0;
  border-radius: 12px;
  padding: 10px 4px;
  font-size: 12px;
  color: #fff;
  font-weight: 600;
  margin-top: 6px;
  cursor: pointer;
}

button:hover {
  background: #0086c4;
  transition-property: background-color;
  transition-duration: 200ms;
}
</style>
