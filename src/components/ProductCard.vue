<template>
  <div class="card">
    <div class="title">
      <strong>{{ p.name }}</strong>
    </div>

    <div class="list">
      <div><b>流量(双向)</b>：{{ p.traffic }}</div>
      <div><b>带宽</b>：{{ p.bandwidth }}</div>
      <div v-if="p.priceMonthly"><b>价格(月付)</b>：¥{{ p.priceMonthly }}</div>
      <div><b>端口</b>：{{ p.ports }}</div>
      <div><b>库存</b>：{{ p.stock }}</div>
      <div><b>交付方式</b>：{{ p.delivery }}</div>
    </div>

    <div class="note" v-if="p.note">* {{ p.note }}</div>
    <div class="remark" v-if="p.remark">* {{ p.remark }}</div>

    <a class="btn" :href="p.contact" target="_blank">联系我</a>
  </div>
</template>

<script setup>
defineProps({ p: Object });
</script>

<style scoped>
.card{
  border:1px solid #e5e7eb;
  border-radius:12px;
  padding:16px;
  box-shadow:0 2px 10px rgba(0,0,0,.04);
  background:#fff;
  display:flex;
  flex-direction:column;
  gap:8px;
}
.title{font-size:16px;font-weight:600;}
.list{display:flex;flex-direction:column;gap:6px;font-size:14px;color:#374151;}
.note,.remark{color:#6b7280;font-size:12px;}
.btn{
  margin-top:6px;
  background:#111827;color:#fff;text-align:center;
  padding:8px 10px;border-radius:8px;text-decoration:none;font-size:14px;
}
.btn:hover{background:#0f172a;}
</style>
