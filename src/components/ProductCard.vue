<template>
  <div class="card" :class="{ section: p.type === 'section' }">
    <div class="title">
      <strong>{{ p.name }}</strong>
    </div>

    <div v-if="p.type !== 'section'" class="list">
      <div v-if="p.preVendors"><b>前置可通厂商</b>：{{ p.preVendors }}</div>
      <div v-if="p.cpu"><b>CPU</b>：{{ p.cpu }}</div>
      <div v-if="p.plan"><b>套餐</b>：{{ p.plan }}</div>
      <div><b>流量(双向)</b>：{{ p.traffic }}</div>
      <div><b>带宽</b>：{{ p.bandwidth }}</div>
      <div v-if="p.priceMonthly"><b>价格(月付)</b>：¥{{ p.priceMonthly }}</div>
      <div><b>端口</b>：{{ p.ports }}</div>
      <div><b>库存</b>：{{ p.stock }}</div>
      <div><b>交付方式</b>：{{ p.delivery }}</div>
    </div>

    <div class="note" v-if="p.note">* {{ p.note }}</div>
    <div class="remark" v-if="p.remark">* {{ p.remark }}</div>

    <a v-if="p.type !== 'section'" class="btn" :href="p.contact" target="_blank">联系我</a>
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
  justify-content:center;
  align-items:center;
  min-height:110px;
  font-size:20px;
}
.title{font-size:18px;font-weight:700;}
.list{display:flex;flex-direction:column;gap:8px;font-size:15px;color:#111827;}
.list b{font-weight:700;}
.note,.remark{color:#6b7280;font-size:13px;}
.btn{
  margin-top:8px;
  background:#111827;color:#fff;text-align:center;
  padding:10px 12px;border-radius:10px;text-decoration:none;font-size:15px;font-weight:600;
}
.btn:hover{background:#0f172a;}
</style>
