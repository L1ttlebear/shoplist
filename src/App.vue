<script setup>
/**
 * 💡 修改说明：
 * 后续如需调整颜色、间距、模糊度，请直接在 src/style-src-config.js 中修改。
 * 确保该文件导出了包含 colors, glassEffect, layout 等属性的对象。
 */
import { styleConfig } from './style-src-config.js'

// 将配置项解构，方便模板调用
const { colors, glassEffect, layout } = styleConfig
</script>

<template>
  <div class="shoplist-wrapper" :style="{ 
    '--bg-main': colors.background,
    '--card-bg': colors.cardBg,
    '--text-main': colors.textMain,
    '--blur-val': glassEffect.blur,
    '--card-padding': layout.cardPadding,
    '--accent-danger': colors.danger,
    '--accent-success': colors.success
  }">
    <div class="content-container">
      <header class="main-header">
        <h1>NANAの拼车</h1>
      </header>

      <section class="glass-card">
        <h2># 1. 节点交付 (单向流量)</h2>
        <div class="table-responsive">
          <table class="data-table">
            <thead>
              <tr>
                <th>套餐</th>
                <th>流量/带宽</th>
                <th>价格(月)</th>
                <th>价格(季)</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>GOMAMI</strong></td>
                <td>100G / 2Gbps</td>
                <td><strong>30/月</strong> <span class="status-tag danger">(缺6)</span></td>
                <td><strong>75/季</strong> <span class="status-tag danger">(缺6)</span></td>
              </tr>
              <tr>
                <td><strong>SeedNet</strong></td>
                <td>2T / 300Mbps</td>
                <td><strong>30/月</strong> <span class="status-tag danger">(缺5)</span></td>
                <td><strong>75/季</strong> <span class="status-tag danger">(缺5)</span></td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="alert-bar warning">
          ⚠️ SeedNet: 05:00 换IP / 禁直连 / 仅落地
        </div>
      </section>

      <section class="glass-card">
        <h2># 2. IX 线路 (自备落地) 500G 双向</h2>
        <div class="table-responsive">
          <table class="data-table">
            <thead>
              <tr>
                <th>套餐</th>
                <th>方案</th>
                <th>价格</th>
              </tr>
            </thead>
            <tbody>
              <tr>
                <td><strong>套餐 A</strong></td>
                <td>前置G口 + IX + 内网</td>
                <td><strong>70/月</strong> <span class="status-tag success">(长期有位)</span></td>
              </tr>
              <tr>
                <td><strong>套餐 B</strong></td>
                <td>前置G口 + IX</td>
                <td><strong>55/月</strong> <span class="status-tag success">(长期有位)</span></td>
              </tr>
              <tr>
                <td><strong>套餐 C</strong></td>
                <td>IX + 内网</td>
                <td><strong>30/月</strong> <span class="status-tag success">(长期有位)</span></td>
              </tr>
              <tr>
                <td><strong>套餐 D</strong></td>
                <td>仅IX (送阿里200M)</td>
                <td><strong>15/月</strong> <span class="status-tag danger">(余5)</span></td>
              </tr>
            </tbody>
          </table>
        </div>
        <div class="alert-bar warning">
          ⚠️ 落地仅允许协议: <code>SS 2022-blake3</code> / <code>vless+enc</code>
        </div>
        <footer class="table-footer">注：ix通腾讯 华为 阿里 火山 百度等大厂</footer>
      </section>

      <section class="glass-card policy-section">
        <h3>📜 须知 & 政策</h3>
        <ul class="policy-list">
          <li><strong>严禁</strong>: 机场 / 车中车 (违者清退不退款)</li>
          <li><strong>退款</strong>: 跳车、个人问题不退；车主/商家问题按余值退</li>
          <li><strong>技术</strong>: 提供 TG 全方位支持</li>
        </ul>
        <p class="agreement-text">上车即代表同意上述政策</p>
      </section>
    </div>
  </div>
</template>

<style scoped>
/* 使用 var() 引用来自 JS 的变量 */
.shoplist-wrapper {
  min-height: 100vh;
  background-color: var(--bg-main);
  padding: 60px 20px;
  font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: var(--text-main);
  transition: background-color 0.3s ease;
}

.content-container {
  max-width: 900px;
  margin: 0 auto;
}

.main-header {
  text-align: center;
  margin-bottom: 50px;
}

.main-header h1 {
  font-size: 2.2rem;
  font-weight: 800;
  color: #1e293b;
  letter-spacing: -0.025em;
}

/* 卡片样式：实现毛玻璃的核心 */
.glass-card {
  background: var(--card-bg);
  backdrop-filter: blur(var(--blur-val));
  -webkit-backdrop-filter: blur(var(--blur-val));
  border-radius: 16px;
  padding: var(--card-padding);
  margin-bottom: 30px;
  box-shadow: 0 4px 24px rgba(0, 0, 0, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.3);
  transition: transform 0.2s ease;
}

h2 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 20px;
  color: #0f172a;
}

.data-table {
  width: 100%;
  border-collapse: collapse;
  margin-bottom: 20px;
}

.data-table th {
  text-align: left;
  padding: 12px 16px;
  font-size: 0.8rem;
  font-weight: 600;
  color: #94a3b8;
  text-transform: uppercase;
  border-bottom: 1px solid rgba(0, 0, 0, 0.05);
}

.data-table td {
  padding: 16px;
  font-size: 0.95rem;
  border-bottom: 1px solid rgba(0, 0, 0, 0.02);
}

.status-tag {
  font-size: 0.85rem;
  margin-left: 6px;
  font-weight: 600;
}
.danger { color: var(--accent-danger); }
.success { color: var(--accent-success); }

.alert-bar {
  background-color: rgba(0, 0, 0, 0.03);
  border-left: 4px solid var(--accent-danger);
  border-radius: 4px;
  padding: 12px 16px;
  font-size: 0.875rem;
  color: #475569;
  margin-top: 10px;
}

code {
  background: rgba(0, 0, 0, 0.06);
  padding: 2px 6px;
  border-radius: 4px;
  font-family: ui-monospace, monospace;
}

.table-footer {
  margin-top: 15px;
  font-size: 0.8rem;
  color: #94a3b8;
}

.policy-list {
  padding-left: 20px;
  margin: 15px 0;
}

.policy-list li {
  margin-bottom: 12px;
  font-size: 0.9rem;
}

.agreement-text {
  text-align: center;
  font-size: 0.85rem;
  color: #cbd5e1;
  margin-top: 40px;
}

/* 移动端适配优化 */
@media (max-width: 640px) {
  .glass-card { padding: 20px; }
  .main-header h1 { font-size: 1.8rem; }
  .data-table td, .data-table th { padding: 10px 8px; font-size: 0.85rem; }
}
</style>
