<template>
  <div class="card">
    <div class="title">
      <span class="tag">{{ p.category }}</span>
      <strong>{{ p.node ? p.node : p.cpu }}</strong>
      <span v-if="p.plan" class="plan">Plan {{ p.plan }}</span>
    </div>

    <div class="grid">
      <div><b>流量</b>：{{ p.traffic }}</div>
      <div><b>端口</b>：{{ p.ports }}</div>
      <div><b>带宽</b>：{{ p.bandwidth }}</div>
      <div v-if="p.cycle"><b>周期</b>：{{ p.cycle }} 天</div>
      <div v-if="p.priceCny"><b>价格</b>：¥{{ p.priceCny }}</div>
      <div><b>库存</b>：{{ p.stock }}</div>
      <div><b>付款</b>：{{ p.payMethod }}</div>
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
.title{display:flex;align-items:center;gap:8px;font-size:16px;}
.tag{background:#f3f4f6;color:#374151;border-radius:999px;padding:2px 8px;font-size:12px;}
.plan{color:#6b7280;font-size:12px;}
.grid{display:grid;grid-template-columns:1fr 1fr;gap:6px 10px;font-size:14px;color:#374151;}
.note,.remark{color:#6b7280;font-size:12px;}
.btn{
  margin-top:6px;
  background:#111827;color:#fff;text-align:center;
  padding:8px 10px;border-radius:8px;text-decoration:none;font-size:14px;
}
.btn:hover{background:#0f172a;}
</style>
