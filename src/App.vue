<template>
  <div class="page">
    <h1>套餐列表</h1>
    <div class="cards">
      <ProductCard v-for="(p, i) in products" :key="i" :p="p" />
    </div>
  </div>
</template>

<script setup>
import { products } from "./data/products";
import ProductCard from "./components/ProductCard.vue";
</script>

<style scoped>
.page{max-width:1100px;margin:24px auto;padding:0 16px;}
.cards{display:grid;grid-template-columns:repeat(auto-fit,minmax(260px,1fr));gap:16px;}
</style>
