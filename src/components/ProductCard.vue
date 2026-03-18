<template>
  <div class="card" :class="{ section: p.type === 'section' }">
    <div class="title" :class="{ center: p.type === 'section' }">
      <strong>{{ p.name }}</strong>
    </div>

    <!-- Section cards (A车/B车说明卡) -->
    <div v-if="p.type === 'section'" class="section-center">
      <div class="inner-box" v-if="p.datacenter || p.payCycle || p.discount">
        <div v-if="p.datacenter"><b>数据中心:</b> {{ p.datacenter }}</div>
        <div v-if="p.payCycle"><b>付款周期:</b> {{ p.payCycle }}</div>
        <div v-if="p.discount"><b>优惠:</b> {{ p.discount }}</div>
      </div>

      <div class="inner-box" v-if="p.latency && p.latency.length">
        <div class="latency">
          <div><b>延迟列表:</b></div>
          <div class="latency-list">
            <div v-for="(l, i) in p.latency" :key="i">{{ l }}</div>
          </div>
        </div>
      </div>
    </div>

    <!-- Product cards -->
    <div v-else class="list">
      <div v-if="p.preVendors"><b>前置可通厂商:</b> {{ p.preVendors }}</div>
      <div v-if="p.cpu"><b>CPU:</b> {{ p.cpu }}</div>
      <div v-if="p.plan"><b>套餐:</b> {{ p.plan }}</div>
      <div v-if="p.traffic"><b>流量(双向):</b> {{ p.traffic }}</div>
      <div v-if="p.bandwidth"><b>带宽:</b> {{ p.bandwidth }}</div>
      <div v-if="p.priceMonthly" class="price-box">
        <div class="price-title"><b>价格(月付)</b></div>
        <div class="price-single">{{ p.priceMonthly }} CNY</div>
      </div>

      <div v-if="p.priceQuarter2 || p.priceQuarter4" class="price-box">
        <div class="price-title"><b>价格(季度付款)</b></div>
        <div class="price-grid">
          <div class="price-col">
            <div class="price-label">任意两区域</div>
            <div class="price-value">{{ p.priceQuarter2 }}</div>
          </div>
          <div class="price-col">
            <div class="price-label">四区域全</div>
            <div class="price-value">{{ p.priceQuarter4 }}</div>
          </div>
        </div>
      </div>

      <div v-if="p.ports !== undefined"><b>端口:</b> {{ p.ports }}</div>

      <div v-if="p.stock" class="stock-box">
        <div class="stock-title">
          <span><b>已拼</b></span>
          <span><b>总量</b></span>
          <span><b>剩余车位</b></span>
        </div>
        <div class="stock-grid">
          <span>{{ (p.stock || '').split('/')[0] }}</span>
          <span>{{ (p.stock || '').split('/')[1] }}</span>
          <span class="stock-left">{{ (p.stock || '').split('/')[1] - (p.stock || '').split('/')[0] }}</span>
        </div>
      </div>

      <div v-if="p.delivery"><b>交付方式:</b> {{ p.delivery }}</div>
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
  border:1px solid rgba(255,255,255,.25);
  border-radius:14px;
  padding:20px;
  box-shadow:0 6px 20px rgba(0,0,0,.25);
  background:rgba(0,0,0,.55);
  backdrop-filter: blur(10px);
  -webkit-backdrop-filter: blur(10px);
  color:#fff;
  display:flex;
  flex-direction:column;
  gap:10px;
}
.card.section{
  min-height:190px;
  justify-content:flex-start;
  align-items:stretch;
}
.card.section .title{
  margin-bottom:12px;
  align-self:stretch;
}
.card.section .section-center{
  flex:1;
  justify-content:center;
}
.title{
  font-size:18px;
  font-weight:700;
  text-align:left;
  color:#fff;
}
.title.center{
  text-align:center;
  font-size:22px;
  margin-top:2px;
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
  border:1px solid rgba(255,255,255,.2);
  border-radius:10px;
  padding:10px 12px;
  background:rgba(0,0,0,.45);
  text-align:left;
  line-height:1.6;
  color:#fff;
}
.inner-box b{
  min-width:96px;
  display:inline-block;
}
.latency{margin-top:6px;}
.latency-list{margin-left:12px;}
.list{
  display:flex;
  flex-direction:column;
  gap:6px;
  font-size:14px;
  line-height:1.6;
  color:#fff;
}
.list b{
  font-weight:700;
  min-width:92px;
  display:inline-block;
}
.stock-box{
  margin-top:6px;
  border:1px solid rgba(255,255,255,.2);
  border-radius:10px;
  padding:8px 10px;
  background:rgba(0,0,0,.45);
}
.stock-title{
  display:grid;
  grid-template-columns:repeat(3, 1fr);
  text-align:center;
  font-size:12.5px;
  color:#fff;
  padding-bottom:6px;
  border-bottom:1px solid rgba(255,255,255,.2);
}
.stock-title span{position:relative;}
.stock-title span:not(:last-child)::after{
  content:"";
  position:absolute;
  right:0;
  top:2px;
  bottom:2px;
  width:1px;
  background:rgba(255,255,255,.2);
}
.stock-grid{
  display:grid;
  grid-template-columns:repeat(3, 1fr);
  text-align:center;
  font-weight:700;
  padding-top:6px;
  color:#fff;
}
.stock-grid span:not(:last-child){
  border-right:1px solid rgba(255,255,255,.2);
}
.stock-left{color:#b35220;}
.price-box{
  margin-top:6px;
  border:1px solid rgba(255,255,255,.2);
  border-radius:10px;
  padding:8px 10px;
  background:rgba(0,0,0,.45);
  color:#fff;
}
.price-title{
  text-align:center;
  font-weight:700;
  margin-bottom:6px;
}
.price-grid{
  display:grid;
  grid-template-columns:repeat(2, 1fr);
  text-align:center;
}
.price-col{padding:4px 0;}
.price-col:not(:last-child){
  border-right:1px solid rgba(255,255,255,.2);
}
.price-label{font-size:12.5px;color:#fff;font-weight:700;}
.price-value{font-size:13.5px;font-weight:700;}
.price-single{
  text-align:center;
  font-size:14px;
  font-weight:700;
}
.note,.remark{color:rgba(255,255,255,.8);font-size:12px;}
.btn{
  margin-top:8px;
  background:rgba(0,0,0,.75);
  color:#fff;
  text-align:center;
  padding:10px 12px;
  border-radius:10px;
  text-decoration:none;
  font-size:15px;
  font-weight:600;
  border:1px solid rgba(255,255,255,.2);
}
.btn:hover{background:rgba(0,0,0,.9);}
</style>
