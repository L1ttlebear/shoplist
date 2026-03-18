<template>
  <div class="page">
    <h1>NANAの拼车</h1>

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
          <img class="avatar" :src="avatarUrl" alt="NANA" />
          <div class="profile-text">
            <div class="name">NANA</div>
            <div class="signature"><span class="typing">{{ typedText }}</span><span class="cursor">|</span></div>
          </div>
        </div>

        <a class="side-btn" href="https://www.nodeseek.com/space/41701#/general" target="_blank">nodeseek - 主页</a>
        <a class="side-btn" href="https://www.nodeseek.com/notification#/message?mode=talk&to=41701" target="_blank">nodeseek - PM</a>
        <a class="side-btn" href="https://t.me/MesNANA_bot" target="_blank">Telegram - Bot</a>
      </aside>

      <aside class="rightbox">
        <div class="extra-card">
          <div class="extra-title">公告</div>
          <ul>
            <li>这里填写内容（可改）</li>
            <li>支持放文字/活动/联系方式</li>
          </ul>
        </div>
      </aside>
    </div>
  </div>
</template>

<script setup>
import { computed, ref, onMounted, onBeforeUnmount } from "vue";
import { sections } from "./data/products";
import ProductCard from "./components/ProductCard.vue";

const avatarUrl = "https://example.com/avatar.jpg"; // 头像远程链接（内容在此修改）

const signatures = [
  "快来拼车吧,少年~",
  "怎样才算好呢?好难抉择呀!",
  "人没有梦想,和咸鱼有什么区别!!"
];

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
.page{max-width:1500px;margin:24px auto;padding:0 16px;}
.page h1{ text-align:center; margin-bottom:16px; }

.layout{display:grid;grid-template-columns:minmax(760px, 1fr) 260px 260px;gap:24px;align-items:start;}
@media (max-width: 1400px){
  .layout{grid-template-columns:1fr 260px;}
  .rightbox{grid-column:2;grid-row:2;}
}
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
.extras{margin:10px 0 20px;padding:12px 16px;border:1px dashed #e5e7eb;border-radius:12px;background:#fafafa;}
.extras h2{font-size:16px;margin:0 0 8px;}
.extras ul{margin:0;padding-left:18px;color:#374151;}

.sidebar{display:flex;flex-direction:column;gap:12px;position:sticky;top:12px;}
.rightbox{position:sticky;top:12px;}
.profile-card{
  border:1px solid #e5e7eb;
  border-radius:12px;
  padding:14px;
  background:#fff;
  display:flex;
  gap:12px;
  align-items:center;
}
.avatar{width:64px;height:64px;border-radius:12px;object-fit:cover;}
.profile-text .name{font-size:18px;font-weight:700;margin-bottom:6px;}
.signature{font-weight:700;font-size:14px;color:#111827;min-height:22px;}
.cursor{margin-left:2px;animation:blink 1s infinite;}

.side-btn{
  border:1px solid #e5e7eb;
  border-radius:12px;
  padding:10px 12px;
  text-align:center;
  background:#fff;
  color:#111827;
  text-decoration:none;
  font-weight:600;
}
.side-btn:hover{background:#f9fafb;}

.extra-card{
  border:1px solid #e5e7eb;
  border-radius:12px;
  padding:14px;
  background:#fff;
}
.extra-title{font-size:16px;font-weight:700;margin-bottom:8px;text-align:center;}
.extra-card ul{margin:0;padding-left:18px;color:#374151;}

@keyframes blink{0%,49%{opacity:1;}50%,100%{opacity:0;}}
</style>
