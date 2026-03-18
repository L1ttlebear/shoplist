<template>
  <div class="card" :class="{ section: p.type === 'section' }">
    <div class="title" :class="{ center: p.type === 'section' }">
      <strong>{{ p.name }}</strong>
    </div>

    <!-- Section cards (A车/B车说明卡) -->
    <div v-if="p.type === 'section'" class="section-center">
      <div class="inner-box" v-if="p.datacenter || p.payCycle || p.discount">
        <div v-if="p.datacenter"><b>数据中心</b>：{{ p.datacenter }}</div>
        <div v-if="p.payCycle"><b>付款周期</b>：{{ p.payCycle }}</div>
        <div v-if="p.discount"><b>优惠</b>：{{ p.discount }}</div>
      </div>

      <div class="inner-box" v-if="p.latency && p.latency.length">
        <div class="latency">
          <div><b>延迟列表</b>：</div>
          <div class="latency-list">
            <div v-for="(l, i) in p.latency" :key="i">{{ l }}</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Product cards -->
    <div v-else class="list">
      <div v-if="p.preVendors"><b>前置可通厂商</b>：{{ p.preVendors }}</div>
      <div v-if="p.cpu"><b>CPU</b>：{{ p.cpu }}</div>
      <div v-if="p.plan"><b>套餐</b>：{{ p.plan }}</div>
      <div v-if="p.traffic"><b>流量(双向)</b>：{{ p.traffic }}</div>
      <div v-if="p.bandwidth"><b>带宽</b>：{{ p.bandwidth }}</div>
      <div v-if="p.priceMonthly"><b>价格(月付)</b>：{{ p.priceMonthly }} CNY</div>
      <div v-if="p.priceQuarter2"><b>价格(季付)</b>：{{ p.priceQuarter2 }}</div>
      <div v-if="p.priceQuarter4"><b>价格(季付)</b>：{{ p.priceQuarter4 }}</div>
      <div v-if="p.ports !== undefined"><b>端口</b>：{{ p.ports }}</div>
      <div v-if="p.stock"><b>库存</b>：{{ p.stock }}</div>
      <div v-if="p.delivery"><b>交付方式</b>：{{ p.delivery }}</div>
    </div>

    <div class="note" v-if="p.note">* {{ p.note }}</div>
    <div class="remark" v-if="p.remark">* {{ p.remark }}</div>

    <a v-if="p.contact" class="btn" :href="p.contact" target="_blank">联系我</a>
  </div>
</template>

<script setup>
defineProps({ p: Object });
</script>

<style scoped>
.card{
  border:1px solid #e5e7eb;
  border-radius:14px;
  padding:20px;
  box-shadow:0 4px 16px rgba(0,0,0,.06);
  background:#fff;
  display:flex;
  flex-direction:column;
  gap:10px;
}
.card.section{
  min-height:190px;
  justify-content:center;
  align-items:center;
}
.card.section .title{
  margin-bottom:10px;
}
.title{
  font-size:18px;
  font-weight:700;
  text-align:left;
}
.title.center{
  text-align:center;
}
.section-center{
  width:100%;
  display:flex;
  flex-direction:column;
  align-items:center;
  gap:10px;
}
.inner-box{
  width:90%;
  border:1px solid #e5e7eb;
  border-radius:10px;
  padding:10px 12px;
  background:#fafafa;
  text-align:left;
  line-height:1.6;
}
.inner-box b{
  min-width:96px;
  display:inline-block;
}
.latency{
  margin-top:6px;
}
.latency-list{
  margin-left:12px;
}
.list{
  display:flex;
  flex-direction:column;
  gap:6px;
  font-size:14px;
  line-height:1.6;
  color:#111827;
}
.list b{
  font-weight:700;
  min-width:92px;
  display:inline-block;
}
.note,.remark{color:#6b7280;font-size:12px;}
.btn{
  margin-top:8px;
  background:#111827;color:#fff;text-align:center;
  padding:10px 12px;border-radius:10px;text-decoration:none;font-size:15px;font-weight:600;
}
.btn:hover{background:#0f172a;}
</style>
