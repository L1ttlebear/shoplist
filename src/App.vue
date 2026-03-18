<template>
  <div class="page">
    <div class="title-card">
      <h1>NANAの拼车</h1>
    </div>

    <div class="layout">
      <main class="main">
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
      </main>

      <aside class="sidebar">
        <div class="profile-card">
          <img class="avatar" :src="avatarUrl" :alt="name" />
          <div class="profile-text">
            <div class="name">{{ name }}</div>
            <div class="signature"><span class="typing">{{ typedText }}</span><span class="cursor">|</span></div>
          </div>
        </div>

        <a v-for="(l, i) in links" :key="i" class="side-btn" :href="l.url" target="_blank">{{ l.label }}</a>
      </aside>

    </div>
  </div>
</template>

<script setup>
import { computed, ref, onMounted, onBeforeUnmount } from "vue";
import { sections } from "./data/products";
import ProductCard from "./components/ProductCard.vue";
import { STYLE_SRC_CONFIG } from "./style-src-config";

const { avatarUrl, name, signatures, links } = STYLE_SRC_CONFIG;

const typedText = ref("");
let sigIndex = 0;
let charIndex = 0;
let deleting = false;
let timer = null;

const loopType = () => {
  const current = signatures[sigIndex];
  let delay = 80;

  if (!deleting) {
    charIndex += 1;
    typedText.value = current.slice(0, charIndex);
    if (charIndex >= current.length) {
      deleting = true;
      delay = 1200;
    }
  } else {
    charIndex -= 1;
    typedText.value = current.slice(0, charIndex);
    delay = 50;
    if (charIndex <= 0) {
      deleting = false;
      sigIndex = (sigIndex + 1) % signatures.length;
      delay = 300;
    }
  }

  timer = setTimeout(loopType, delay);
};

onMounted(() => loopType());
onBeforeUnmount(() => timer && clearTimeout(timer));

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
:global(body){
  background:url('https://img.ezov.de/uploads/2026/03/sItZmWb3CAfe.webp') center/cover fixed no-repeat;
}
.page{max-width:1500px;margin:24px auto;padding:0 16px;}
.page h1{ text-align:center; margin:0; }
.title-card{
  margin:0 auto 18px;
  max-width:520px;
  padding:10px 16px;
  text-align:center;
  border-radius:14px;
  background:rgba(0,0,0,.55);
  border:1px solid rgba(255,255,255,.25);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  box-shadow:0 6px 20px rgba(0,0,0,.25);
}
.title-card h1{
  font-size:28px;
  font-weight:900;
  color:#fff;
  letter-spacing:2px;
  text-shadow:0 2px 10px rgba(0,0,0,.5);
}

.layout{display:grid;grid-template-columns:minmax(760px, 1fr) 260px;gap:24px;align-items:start;}
@media (max-width: 980px){
  .layout{grid-template-columns:1fr;}
}

.main{}

.rows{display:flex;flex-direction:column;gap:18px;}
.row{display:grid;grid-template-columns:repeat(3, minmax(0, 1fr));gap:18px;}
@media (max-width: 980px){
  .row{grid-template-columns:repeat(2, minmax(0, 1fr));}
}
@media (max-width: 640px){
  .row{grid-template-columns:1fr;}
}

.divider{height:1px;background:#e5e7eb;margin:20px 0;}
.extras{
  margin:10px 0 20px;
  padding:12px 16px;
  border-radius:12px;
  background:rgba(0,0,0,.55);
  color:#fff;
  border:1px solid rgba(255,255,255,.25);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  box-shadow:0 6px 20px rgba(0,0,0,.25);
}
.extras h2{font-size:16px;margin:0 0 8px;color:#fff;}
.extras ul{margin:0;padding-left:18px;color:#fff;}

.sidebar{display:flex;flex-direction:column;gap:12px;position:sticky;top:12px;}
.profile-card{
  border:1px solid #111827;
  border-radius:12px;
  padding:14px;
  background:#111827;
  color:#fff;
  display:flex;
  gap:12px;
  align-items:center;
}
.avatar{width:64px;height:64px;border-radius:12px;object-fit:cover;}
.profile-text .name{font-size:18px;font-weight:700;margin-bottom:6px;color:#fff;}
.signature{font-weight:700;font-size:14px;color:#fff;min-height:22px;}
.cursor{margin-left:2px;animation:blink 1s infinite;}

.side-btn{
  border:1px solid #111827;
  border-radius:12px;
  padding:10px 12px;
  text-align:center;
  background:#111827;
  color:#fff;
  text-decoration:none;
  font-weight:600;
}
.side-btn:hover{background:#0b1220;}

@keyframes blink{0%,49%{opacity:1;}50%,100%{opacity:0;}}
</style>
