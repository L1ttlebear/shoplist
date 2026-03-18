<template>
  <div class="page">
    <h1>NANAの拼车</h1>

    <div class="extras">
      <h2>可选项目</h2>
      <ul>
        <li>ix深港杜甫</li>
        <li>Akari亚太内网</li>
      </ul>
    </div>

    <div class="cards">
      <ProductCard v-for="(p, i) in sections.A" :key="`A-${i}`" :p="p" />
    </div>

    <div class="divider" />

    <div class="cards">
      <ProductCard v-for="(p, i) in sections.B" :key="`B-${i}`" :p="p" />
    </div>
  </div>
</template>

<script setup>
import { sections } from "./data/products";
import ProductCard from "./components/ProductCard.vue";
</script>

<style scoped>
.page{max-width:1200px;margin:24px auto;padding:0 16px;}
.page h1{ text-align:center; margin-bottom:16px; }
.cards{display:grid;grid-template-columns:repeat(3, minmax(0, 1fr));gap:18px;}
@media (max-width: 980px){
  .cards{grid-template-columns:repeat(2, minmax(0, 1fr));}
}
@media (max-width: 640px){
  .cards{grid-template-columns:1fr;}
}
.divider{height:1px;background:#e5e7eb;margin:20px 0;}
.extras{margin:10px 0 20px;padding:12px 16px;border:1px dashed #e5e7eb;border-radius:12px;background:#fafafa;}
.extras h2{font-size:16px;margin:0 0 8px;}
.extras ul{margin:0;padding-left:18px;color:#374151;}
</style>
