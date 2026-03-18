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

    <div class="rows">
      <div class="row" v-for="(row, i) in aRows" :key="`A-row-${i}`">
        <ProductCard :p="aSection" />
        <ProductCard v-for="(p, j) in row" :key="`A-${i}-${j}`" :p="p" />
      </div>
    </div>

    <div class="divider" />

    <div class="rows">
      <div class="row" v-for="(row, i) in bRows" :key="`B-row-${i}`">
        <ProductCard :p="bSection" />
        <ProductCard v-for="(p, j) in row" :key="`B-${i}-${j}`" :p="p" />
      </div>
    </div>
  </div>
</template>

<script setup>
import { computed } from "vue";
import { sections } from "./data/products";
import ProductCard from "./components/ProductCard.vue";

const aSection = sections.A.find((p) => p.type === "section");
const bSection = sections.B.find((p) => p.type === "section");

const aItems = sections.A.filter((p) => p.type !== "section");
const bItems = sections.B.filter((p) => p.type !== "section");

const chunk = (arr, size) => {
  const res = [];
  for (let i = 0; i < arr.length; i += size) res.push(arr.slice(i, i + size));
  return res;
};

const aRows = computed(() => chunk(aItems, 2));
const bRows = computed(() => chunk(bItems, 2));
</script>

<style scoped>
.page{max-width:1200px;margin:24px auto;padding:0 16px;}
.page h1{ text-align:center; margin-bottom:16px; }
.rows{display:flex;flex-direction:column;gap:18px;}
.row{display:grid;grid-template-columns:repeat(3, minmax(0, 1fr));gap:18px;}
@media (max-width: 980px){
  .row{grid-template-columns:repeat(2, minmax(0, 1fr));}
}
@media (max-width: 640px){
  .row{grid-template-columns:1fr;}
}
.divider{height:1px;background:#e5e7eb;margin:20px 0;}
.extras{margin:10px 0 20px;padding:12px 16px;border:1px dashed #e5e7eb;border-radius:12px;background:#fafafa;}
.extras h2{font-size:16px;margin:0 0 8px;}
.extras ul{margin:0;padding-left:18px;color:#374151;}
</style>
