<template>
  <div class="shoplist-wrapper">
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
/* 容器与背景 */
.shoplist-wrapper {
  min-height: 100vh;
  background-color: #f8fafc; /* 浅灰蓝背景 */
  padding: 60px 20px;
  font-family: -apple-system, system-ui, BlinkMacSystemFont, "Segoe UI", Roboto, sans-serif;
  color: #334155;
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

/* 卡片样式 */
.glass-card {
  background: #ffffff;
  border-radius: 16px;
  padding: 32px;
  margin-bottom: 30px;
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.03);
  border: 1px solid #f1f5f9;
}

h2 {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 20px;
  color: #0f172a;
}

/* 表格样式 */
.table-responsive {
  overflow-x: auto;
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
  border-bottom: 1px solid #f1f5f9;
}

.data-table td {
  padding: 16px;
  font-size: 0.95rem;
  border-bottom: 1px solid #f8fafc;
}

/* 标签与警告框 */
.status-tag {
  font-size: 0.85rem;
  margin-left: 6px;
  font-weight: 500;
}
.danger { color: #ef4444; }
.success { color: #10b981; }

.alert-bar {
  background-color: #fff1f2;
  border-radius: 8px;
  padding: 12px 16px;
  font-size: 0.875rem;
  color: #475569;
  margin-top: 10px;
}

code {
  background: rgba(0, 0, 0, 0.04);
  padding: 2px 6px;
  border-radius: 4px;
  font-family: ui-monospace, monospace;
}

.table-footer {
  margin-top: 15px;
  font-size: 0.8rem;
  color: #94a3b8;
}

/* 政策部分 */
.policy-list {
  padding-left: 20px;
  margin: 15px 0;
}

.policy-list li {
  margin-bottom: 10px;
  font-size: 0.9rem;
}

.agreement-text {
  text-align: center;
  font-size: 0.85rem;
  color: #cbd5e1;
  margin-top: 30px;
}
</style>
