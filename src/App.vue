<template>
  <div class="page">
    <h1>套餐列表</h1>
    <div class="cards">
      <ProductCard v-for="(p, i) in products" :key="i" :p="p" />
    </div>

    <div class="extras">
      <h2>可选项目</h2>
      <ul>
        <li>IX</li>
        <li>线路优化</li>
      </ul>
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
.extras{margin-top:20px;padding:12px 16px;border:1px dashed #e5e7eb;border-radius:12px;background:#fafafa;}
.extras h2{font-size:16px;margin:0 0 8px;}
.extras ul{margin:0;padding-left:18px;color:#374151;}
</style>
