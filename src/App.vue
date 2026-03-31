<script setup>
import { STYLE_SRC_CONFIG } from './style-src-config.js'

// 提取配置
const { backgroundUrl, avatarUrl, name, signatures, links } = STYLE_SRC_CONFIG
</script>

<template>
  <div class="page-background" :style="{ backgroundImage: `url(${backgroundUrl})` }"></div>

  <div class="shoplist-wrapper">
    <div class="content-container">
      
      <header class="profile-header glass-card">
        <img :src="avatarUrl" class="avatar" alt="avatar" />
        <div class="info">
          <h1>{{ name }}の拼车</h1>
          <div class="signature-box">
            <p v-for="(sig, index) in signatures" :key="index" class="sig-item">{{ sig }}</p>
          </div>
        </div>
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

      <section class="glass-card">
        <h3>📜 须知 & 政策</h3>
        <ul class="policy-list">
          <li><strong>严禁</strong>: 机场 / 车中车 (违者清退不退款)</li>
          <li><strong>退款</strong>: 跳车、个人问题不退；车主/商家问题按余值退</li>
          <li><strong>技术</strong>: 提供 TG 全方位支持</li>
        </ul>
      </section>

      <footer class="links-footer">
        <a v-for="link in links" :key="link.label" :href="link.url" target="_blank" class="link-btn glass-card">
          {{ link.label }}
        </a>
      </footer>
      
      <p class="agreement-text">上车即代表同意上述政策</p>
    </div>
  </div>
</template>

<style scoped>
.page-background {
  position: fixed;
  top: 0; left: 0; width: 100%; height: 100%;
  background-size: cover;
  background-position: center;
  z-index: -1;
  filter: brightness(0.9);
}

.shoplist-wrapper {
  min-height: 100vh;
  padding: 40px 20px;
  font-family: -apple-system, system-ui, sans-serif;
  color: #1e293b;
}

.content-container { max-width: 800px; margin: 0 auto; }

/* 毛玻璃基础卡片 */
.glass-card {
  background: rgba(255, 255, 255, 0.7);
  backdrop-filter: blur(12px);
  -webkit-backdrop-filter: blur(12px);
  border-radius: 16px;
  padding: 24px;
  margin-bottom: 24px;
  border: 1px solid rgba(255, 255, 255, 0.4);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.1);
}

/* 个人信息栏 */
.profile-header {
  display: flex;
  align-items: center;
  gap: 20px;
}
.avatar {
  width: 80px; height: 80px;
  border-radius: 50%;
  border: 3px solid #fff;
  box-shadow: 0 4px 12px rgba(0,0,0,0.1);
}
.profile-header h1 { font-size: 1.5rem; margin: 0 0 8px 0; color: #0f172a; }
.signature-box { font-size: 0.85rem; color: #64748b; line-height: 1.4; }
.sig-item { margin: 2px 0; }

/* 表格样式 */
h2 { font-size: 1.2rem; font-weight: 700; margin-bottom: 16px; }
.table-responsive { overflow-x: auto; }
.data-table { width: 100%; border-collapse: collapse; }
.data-table th { text-align: left; padding: 12px; font-size: 0.75rem; color: #94a3b8; text-transform: uppercase; border-bottom: 1px solid rgba(0,0,0,0.05); }
.data-table td { padding: 12px; font-size: 0.9rem; border-bottom: 1px solid rgba(0,0,0,0.02); }

.status-tag { font-size: 0.8rem; font-weight: 600; margin-left: 4px; }
.danger { color: #ef4444; }
.success { color: #10b981; }

.alert-bar {
  background: rgba(239, 68, 68, 0.1);
  border-left: 4px solid #ef4444;
  padding: 10px 14px;
  font-size: 0.85rem;
  margin-top: 15px;
  border-radius: 4px;
}

.table-footer { font-size: 0.75rem; color: #94a3b8; margin-top: 12px; }

/* 底部按钮 */
.links-footer {
  display: flex;
  flex-wrap: wrap;
  gap: 12px;
  justify-content: center;
  margin-top: 20px;
}
.link-btn {
  padding: 12px 20px;
  margin: 0;
  text-decoration: none;
  color: #1e293b;
  font-size: 0.9rem;
  font-weight: 500;
  transition: transform 0.2s;
}
.link-btn:hover { transform: translateY(-3px); background: rgba(255, 255, 255, 0.9); }

.policy-list { padding-left: 20px; font-size: 0.9rem; line-height: 1.6; }
.agreement-text { text-align: center; font-size: 0.8rem; color: #fff; text-shadow: 0 1px 4px rgba(0,0,0,0.5); margin-top: 40px; opacity: 0.7; }

@media (max-width: 640px) {
  .profile-header {
